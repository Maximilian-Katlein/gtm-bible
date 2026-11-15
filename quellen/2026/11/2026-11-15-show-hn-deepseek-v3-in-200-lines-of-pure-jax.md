# DeepSeek V3 in rund 200 Zeilen reinem JAX

> **Quelle:** [Show HN: DeepSeek V3 in ~200 lines of pure Jax](https://github.com/Vaibhaav-Tiwari/deepseek-v3-jax) · Vaibhaav Tiwari, Privatperson · Diskussion (Show HN mit GitHub-Repo, [HN-Thread](https://news.ycombinator.com/item?id=50497589)) · 2026-11-15
> **Sprecher verkauft:** nichts, MIT-lizenziertes Lernprojekt mit freiem Code und Checkpoint · **Zielmarkt der Aussagen:** ML-Praktiker und Lernende, die die DeepSeek-V3-Architektur nachbauen wollen · **Beweislage:** eigene Einzelläufe auf einem Laptop, eine Ablation, kaum fachliche Gegenprüfung im Thread

## Worum es geht
Wie sehen die Kernideen von DeepSeek V3 aus, wenn man sie ohne Framework auf ein Modell mit 36,2M Parametern verkleinert und auf einem MacBook trainiert? Das Repo richtet sich an Entwickler, die MLA, DeepSeekMoE, Auxiliary-loss-free Balancing und Multi-Token Prediction im Code nachvollziehen wollen. Es ist ausdrücklich eine Architektur-Demo, kein brauchbares Sprachmodell.

## Was man anwenden kann
1. **MLA als Cache-Sparer verstehen.** Multi-head Latent Attention speichert pro Token einen kleinen Latent statt voller Keys und Values. In der Demo sinkt der Cache von 480 auf 144 Zahlen pro Token und Layer, also um 70 Prozent. Ein einzelner Rotary-Key (Decoupled RoPE) wird von allen Heads geteilt und liegt außerhalb des Latents. Eine gemessene Speicher- oder Geschwindigkeitsersparnis gibt es nicht.
2. **MoE-Aufbau nachbauen.** Ein geteilter Experte läuft immer, dazu kommen 16 geroutete Experten, von denen pro Token die Top 4 gewählt werden. Die Funktionen route und moe in deepseek_v3.py zeigen das Routing. Achtung: Die Demo rechnet dicht, jeder Experte läuft auf jedem Token und nicht gewählte Ausgaben werden genullt. Der Rechenvorteil von MoE ist hier nicht realisiert.
3. **Experten per Bias ausbalancieren statt per Loss.** Ein Bias pro Experte schiebt das Routing zu wenig genutzten Experten. Er ändert nur die Auswahl, nicht die Gewichtung der Ausgaben. Ergänzt wird er durch einen kleinen Balance-Loss auf Sequenzebene mit α = 1e-4. Mit dem Flag --no-bias in train.py lässt sich der Effekt selbst prüfen.
4. **Ablation in zwei Läufen reproduzieren.** train.py --steps 2000 einmal mit, einmal mit --no-bias, Ausgabe in runs/bias_on und runs/bias_off. Jeder Lauf schreibt metrics.jsonl mit Loss, Validierungs-Loss, Last pro Experte, Biases und Tokens pro Sekunde. Mit Bias lag die Last pro Experte bei 5,7 bis 6,9 Prozent, ohne Bias bei 0,09 bis 18,6 Prozent.
5. **Multi-Token Prediction einbauen.** Ein Zusatzmodul sagt auch das übernächste Token voraus und geht mit Gewicht λ = 0,3 in den Loss ein. Die Tests prüfen die MTP-Targets gesondert.
6. **Ohne Framework schreiben, um zu lernen.** Kein Flax, kein Equinox, kein PyTorch. Parameter sind einfache Dicts aus Arrays, jeder Modellteil ist eine Funktion, lesbar von oben nach unten. Training mit bf16-Compute auf f32-Master-Weights, AdamW mit Warmup und Cosine Decay.
7. **Testen vor dem Trainieren.** 39 Tests laufen auf der CPU mit JAX_PLATFORMS=cpu. Sie decken Causal Masking, Cache gegen Full Forward, Routing, Balancing, MTP-Targets, NaN-Handling und bf16-Master-Weights ab. Der Vergleich Cache gegen Full Forward ist ein übertragbares Prüfmuster für jede eigene Decode-Implementierung.
8. **Apple-GPU-Pfad mit festen Versionen.** Voraussetzung laut README: Apple-Silicon-Mac, Python 3.12, uv. jax-metal 0.1.1 läuft nur mit jax==0.4.34, JAX darf nicht aktualisiert werden. smoke_metal.py zeigt, welche Operationen auf Metal laufen; der Test „grad through 2-axis contraction“ scheitert erwartungsgemäß, das Modell umgeht diese Operation.
9. **AMD-GPU über ROCm-Container.** Ein Kommentator ließ das Projekt auf einer RX 7600 XT (16 GB) unter Fedora mit dem AMD-Image rocm/jax laufen, ohne ROCm auf dem Host. Nötig waren HSA_OVERRIDE_GFX_VERSION=11.0.0, weil das JAX-Plugin gfx1102 ablehnt, und XLA_FLAGS=--xla_gpu_enable_triton_gemm=false gegen einen GPU-Hang. Das Container-Setup liegt in PR #1. Einzelbericht, Versionen nicht geprüft.
10. **CPU-Fallback für kleine Macs.** JAX_PLATFORMS=cpu train.py --config small nutzt 4 Layer, 8 Experten, Top 2 und 128 Token Kontext, gedacht auch für Macs mit 8 bis 16 GB. Diese Konfiguration wurde nur wenige Schritte geprüft, Ergebnisqualität ist unbekannt.
11. **Exakt gleiche Daten verwenden.** prepare_data.py lädt 207 Bücher (ca. 120 MB, ca. 7 Minuten) und trainiert einen BPE-Tokenizer mit 8192 Token. Weil Project Gutenberg 28 der 203 Bücher leicht geändert neu ausgegeben hat, weichen Hashes eigener Builds ab. Wer identische Bytes will, lädt train.bin, val.bin und tokenizer.json aus Release v1.0 und prüft mit shasum -a 256 gegen die im README genannten Hashes.
12. **Pickle-Checkpoints nur aus vertrauenswürdiger Quelle laden.** Der Checkpoint (138 MB) ist ein Python-Pickle und kann beim Laden Code ausführen. Das gilt für jeden geteilten Checkpoint aus Forks oder Releases. Sampling danach mit sample.py, Standard: Temperatur 0,8, Top-k 50, 300 neue Tokens.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 36,2M Parameter, 13,6M aktiv pro Token | Standardkonfiguration; „aktiv“ ist nominal, da dicht gerechnet | eigene Daten |
| 6 Layer, 256 Token Kontext, 8192 Token Vokabular | Demo, gegenüber 61 Layern und 128K Kontext im Original mit 671B Parametern | eigene Daten |
| 480 auf 144 Zahlen pro Token und Layer (70 Prozent weniger) | MLA-Cache in der Demo, rechnerisch, nicht gemessen | eigene Daten, Prozent eigene Rechnung |
| 21,7M Trainingstokens, 207 Bücher | Hammett-Texte 3× wiederholt, Validierung auf zurückgehaltener Kriminalliteratur | eigene Daten |
| 12000 Schritte, ca. 98M Tokens, ca. 2,6 h | ein Lauf auf MacBook Air M5 mit 24 GB, jax-metal | eigene Daten |
| ca. 10,7k Tokens pro Sekunde | Median desselben Laufs | eigene Daten |
| Validierungs-Loss 5,02 auf 3,51 | Schritt 250 bis Laufende | eigene Daten |
| 3,921 gegen 3,923 | Validierungs-Loss bei Schritt 2000 mit und ohne Bias, je ein Lauf | eigene Daten |
| 5,7 bis 6,9 Prozent gegen 0,09 bis 18,6 Prozent | Last pro Experte mit und ohne Bias, gleichmäßig wären 6,25 Prozent | eigene Daten |
| α = 1e-4, λ = 0,3 | Gewicht Balance-Loss, Gewicht MTP-Loss | eigene Daten, aus dem Paper übernommen |
| 190 Zeilen | nur nichtleere Zeilen ohne Kommentare nach dem Docstring; der Titel rundet auf ca. 200 | eigene Daten |

## Wortlaute
- „Caches one small latent per token instead of full keys and values“ steht für den Kern von MLA in einem Satz.
- „it changes which experts are picked, not their weights“ beschreibt präzise, was der Balancing-Bias tut und was nicht.
- „This is an architecture demo, not a strong language model.“ ist die Einordnung des Autors selbst.
- „The checkpoint is a Python pickle, which can run code when loaded.“ ist die Sicherheitswarnung im README.
- `tail -n +5 deepseek_v3.py | grep -cvE '^\s*(#|$)'` prüft die Zeilenzählung nach.

## Grenzen und Widerspruch
- **Kein Effizienzbeleg.** Dichtes MoE, keine Weight Absorption in MLA, keine Messung von Inferenzgeschwindigkeit oder realem Speicher. Durchsatzaussagen lassen sich nicht auf echte DeepSeek-Implementierungen übertragen.
- **Ablation dünn.** Je ein Lauf pro Variante, 2000 Schritte, Differenz 0,002, keine Seed-Streuung. Belegt ist nur, dass Balancing in diesem Maßstab nicht schadet, kein Qualitätsgewinn. MLA und MTP werden nicht gegen Standard-Attention oder ein dichtes Basismodell verglichen.
- **Fehlende Teile.** Kein FP8-Training, kein DualPipe, kein node-limited Routing, kein YaRN, kein Post-Training. Ergebnis ist ein kleines Basismodell.
- **Nicht vergleichbar.** Ein Kommentator bemängelt die eigene Datenwahl statt eines bekannten Datensatzes. Der Loss von 3,51 lässt sich mit keinem Benchmark anderer Kleinmodelle vergleichen.
- **Plattform-Widerspruch.** Das README verlangt einen Mac und pinnt JAX 0.4.34. Der ROCm-Bericht mit JAX 0.11.1 zeigt, dass beides nur für den jax-metal-Pfad gilt. Er ist aber ein Einzelbericht.
- **Nicht bitgenau reproduzierbar.** Seeds sind fixiert, Metal rechnet aber nicht deterministisch. Eigene Läufe landen nahe an, nicht exakt auf den Zahlen.
- **Datenrecht.** Die Trainingstexte sind in den USA gemeinfrei. Außerhalb der USA kann der Status abweichen; für Nachtrainings in der EU ist das ungeprüft.
- **Lücken im Material.** Batchgröße, Lernrate, Hidden-Dimension und Head-Zahl stehen nur im Code. Das Write-up mit „what worked, what didn't“ lag nicht vor. Kleine README-Inkonsistenzen: 207 Bücher gegen 211 plus 4 Dokumente, Flag --num gegen --n.
- **Junges Projekt, kleine Diskussion.** 4 Commits, 9 Kommentare, keine fachliche Code-Prüfung. Die Frage nach einem Lernpfad für Entwickler mit Java- und Python-Hintergrund blieb unbeantwortet.
- **Kein GTM-Bezug.** Das Projekt sagt nichts über Lizenzen der DeepSeek-Gewichte, Betrieb oder Kosten im Unternehmen.
