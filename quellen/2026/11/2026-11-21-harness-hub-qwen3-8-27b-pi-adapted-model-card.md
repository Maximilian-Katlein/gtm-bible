# Qwen3.8-27B für den pi Coding Agent: LoRA-Adapter per Reinforcement Learning (Model Card)

> **Quelle:** [harness-hub/Qwen3.8-27B-pi-adapted (Model Card)](https://huggingface.co/harness-hub/Qwen3.8-27B-pi-adapted) · harness-hub · Model Card · 2026-11-21
> **Sprecher verkauft:** kostenlosen Open-Weight LoRA-Adapter (Apache 2.0) für Qwen/Qwen3.8-27B, trainiert für den pi Coding Agent · **Zielmarkt der Aussagen:** Entwickler und Teams, die Coding Agents lokal oder selbst gehostet betreiben · **Beweislage:** ausschließlich Herstellerangaben, aber mit Konfidenzintervallen, Vorzeichentests, Korrekturhistorie und veröffentlichten Trajektorien

## Worum es geht
Die Karte beantwortet eine Frage: Kann ein kleiner RL-trainierter Adapter ein 27B-Modell im Agent-Betrieb ohne Thinking fast so gut machen wie dasselbe Modell mit maximalem Thinking, bei einem Bruchteil der Tokens? Relevant ist das für Teams, die Coding Agents selbst hosten und Rechenkosten pro Aufgabe senken wollen. Für Marketing oder Vertrieb gibt es keine direkten Belege. Die Bedeutung liegt bei AI Building und Selbsthosting.

## Was man anwenden kann
1. **Adapter nur auf dem richtigen Basismodell.** Es handelt sich um einen LoRA-Adapter (PEFT, r = 32) auf Qwen/Qwen3.8-27B und nicht um ein eigenständiges Modell. Auf anderen Basismodellen funktioniert er nicht. Die Ergebnisse gelten nur für den pi Harness, mit Thinking aus und reinem Textbetrieb.

2. **Serving mit vLLM wie in der Evaluierung.** Die Evaluierung lief mit `vllm serve Qwen/Qwen3.8-27B --enable-lora --max-lora-rank 32 --lora-modules qwen3.8-pi=...`. Dazu kamen `--language-model-only`, `--enable-auto-tool-choice`, `--tool-call-parser qwen3_xml`, `--reasoning-parser qwen3`, `enable_thinking: false` und `--max-model-len 131072`. Wer die Zahlen reproduzieren will, übernimmt diese Flags unverändert.

3. **Prefix Caching nur mit Zusatzflag.** Bei diesem Hybridmodell greift Prefix Caching nur mit `--enable-prefix-caching --mamba-cache-mode align`. Ohne das Flag liest jeder Agent-Turn die ganze bisherige History neu ein. Bei langen Agent-Sessions steigen dadurch Latenz und Rechenlast deutlich.

4. **pi korrekt anbinden.** pi setzt Node.js 22.19 oder neuer voraus. Installiert wird es mit `npm install -g --ignore-scripts @earendil-works/pi-coding-agent`. In `~/.pi/agent/models.json` trägt man einen Provider `local` ein, mit baseUrl `http://localhost:8000/v1`, Modell-ID `qwen3.8-pi` und zwingend `api: openai-completions`. Fehlt diese Zeile, nutzt pi die Responses API. Mit ihr wurde der Adapter weder trainiert noch evaluiert.

5. **Merge für Engines ohne LoRA-Unterstützung.** Mit PEFT lädt man das Basismodell in bfloat16 auf der CPU, dann folgen `PeftModel.from_pretrained(...).merge_and_unload()` und `save_pretrained`. Den Tokenizer aus dem Adapter-Repo speichert man mit ab. Das Ergebnis ist ein normaler Checkpoint von etwa 54 GB in BF16. Er läuft mit vLLM ohne LoRA-Flags oder mit `transformers serve ... --reasoning off`. Der CPU-Merge hält die GPU für das Serving frei.

6. **Lokal mit llama.cpp oder Llama.app.** Man kombiniert eine Basis-GGUF (empfohlen Q8_0) mit der F16-LoRA-GGUF aus `harness-hub/Qwen3.8-27B-pi-adapted-GGUF`. Gestartet wird mit `enable_thinking: false`, die Anbindung an pi läuft über die Erweiterung `huggingface/pi-llama`. Achtung: Die Beispielkonfigurationen weichen von der Evaluierung ab, etwa beim Kontext (65.536 bzw. 32.768 statt 131.072). Das Llama.app-Snippet nutzt außerdem Temperatur 0.7 statt 0.8 und setzt Thinking nicht aus.

7. **Agent-Evals gegen Infrastrukturfehler absichern.** Die Karte hat zwei eigene Fehler korrigiert. Ein ausgefallener Tunnel zwischen Sandboxes und Modellserver ließ neun Basis-Rollouts scheitern und blähte den Gewinn auf (vorher 29,4 % → 62,7 %, korrigiert 39,2 % → 64,7 %). Ein Output-Cap von 16k Tokens pro Aufruf kürzte lange Thinking-Ketten ab. Mit 32k kommen beide Modelle auf 74,5 %. Daraus folgt: Jeden Rollout auf Infrastrukturausfälle prüfen und das Output-Limit bei Thinking-Modellen ausdrücklich festlegen.

8. **Test-Manipulation strukturell ausschließen.** Agenten ändern manchmal Testdateien. Der SWE-bench-Pro-Grader setzt deshalb alle Testdateien zurück, bei Terminal-Bench werden die Tests erst zur Bewertung hineinkopiert. Für eigene Agent-Benchmarks ist das ein übertragbares Muster.

9. **Reward mit Effizienzanteil.** Trainiert wurde mit AsyncGRPO aus TRL (experimentell). Der Reward besteht aus der Korrektheit laut Task-Verifier plus einem Tool-Effizienz-Bonus mit Gewicht 0,1. Pro Aufgabe gab es 8 Rollouts, Thinking aus, bis zu 50 Agent-Schritte. Gerechnet wurde auf 2× NVIDIA B200 pro Harness, eine für vLLM und eine für den Trainer. Welchen Anteil der Bonus am Ergebnis hat, ist nicht isoliert.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 39,2 % → 64,7 % (+25,5 ± 14,2, p = 0,0023) | SWE-bench Pro, 51 schwerste Aufgaben, Basis gegen Adapter, Thinking aus | Herstellerangabe |
| 39,5 % → 55,8 % (+16,3 ± 9,1, p = 0,0013) | Terminal-Bench 2.1, 86 gepaarte Aufgaben | Herstellerangabe |
| 39,7 % → 55,9 % (+16,2 ± 10,6, p = 0,0074) | Terminal-Bench 2.1, 68 Aufgaben ohne Rolle bei der Checkpoint-Wahl | Herstellerangabe |
| 74,5 % / 64,7 % | SWE-bench Pro: Basis mit xhigh Thinking gegen Adapter ohne Thinking | Herstellerangabe |
| 54,2 % / 56,6 % | Terminal-Bench 2.1 (83 Aufgaben): Basis mit Thinking gegen Adapter ohne | Herstellerangabe |
| 48,8k gegen 9,4k / 16,5k gegen 3,7k | Median generierte Tokens pro Task, Basis mit Thinking gegen Adapter (etwa 5,2× bzw. 4,5× weniger) | Herstellerangabe, SWE-Wert teils aus Trajektorien rekonstruiert |
| 61 gegen 21 / 19 gegen 9 | Median Modellaufrufe pro Task, gleiche Gegenüberstellung | Herstellerangabe |
| etwa 160 gegen 10 Tokens | sichtbarer Text pro Turn, Adapter gegen Basis | Herstellerangabe |
| 20 von 31 | gescheiterte Basis-Versuche auf SWE-bench Pro, die am 100-Schritte-Limit endeten (Adapter: 0) | Herstellerangabe |
| Step 160 von 1.000 geplanten | veröffentlichter Checkpoint, Lauf bei Step 191 gestoppt, 750 scale800- plus 300 TermGrade-Aufgaben | Herstellerangabe |
| etwa 54 GB | gemergter Checkpoint in BF16 | Herstellerangabe |

## Wortlaute
- „Most of the gain of maximum-effort thinking, at a quarter of the tokens.“ Das ist die Kernbotschaft der Karte. „Viertel“ ist gerundet, gemessen sind 4,5× bis 5,2× weniger Tokens.
- „nearly all the difference is reasoning: the adapter reaches the same answers without it.“ Die These: Der Mehraufwand des Thinking-Modus besteht fast vollständig aus versteckten Reasoning-Tokens.
- „pi then capped each model call at 16k output tokens, which cut long reasoning short.“ Die Karte dokumentiert damit selbst einen Evaluierungsfehler.
- „The files carry canary strings: keep them out of training data.“ Ein Hinweis zum Umgang mit den veröffentlichten Trajektorien.

## Grenzen und Widerspruch
- **Gleichstand mit Thinking ist nicht gesichert.** Im direkten Vergleich zählt die Karte nur Aufgaben, die genau eines der beiden Modelle löst: SWE-bench Pro 6 zu 11 (p = 0,33), Terminal-Bench 12 zu 10. Sowohl „auf Augenhöhe“ als auch „10 Punkte dahinter“ sind bei diesen Stichproben statistisch nicht unterscheidbar.
- **Breite Intervalle.** Die untere Grenze des Gewinns liegt bei etwa +11 (SWE-bench Pro) bzw. +7 Punkten (Terminal-Bench). Es gab nur einen Versuch pro Task bei Temperatur 0,8, keine weiteren Seeds und kein pass@k.
- **Kein unabhängiger Holdout für SWE-bench Pro.** Der Checkpoint wurde auch anhand dieses Benchmarks ausgewählt.
- **Uneinheitliche Zahlenbasis.** Terminal-Bench 2.1 hat 89 Aufgaben. Bewertet wurden 86 bzw. 83, ohne Begründung. Wer zitiert, muss die Basis nennen (56,6 % gegen 55,8 %).
- **Ein Teil des Gewinns sind Limits.** Das Basismodell scheitert oft, weil es das Budget aufbraucht. Der Adapter wird innerhalb der Limits fertig. Bei großzügigeren Budgets könnte der Abstand kleiner sein.
- **Nur pi, nur Text, nur BF16.** Andere Harnesses, Vision und quantisierte GGUFs wurden nicht evaluiert. Die Aussage, niedrigere Quants würden stärker driften, ist nicht gemessen. Die Zahlen sind ausdrücklich nicht mit der Karte des Basismodells vergleichbar.
- **Keine Ablation.** Weder der Beitrag des Effizienz-Bonus noch die Wahl von Step 160 sind isoliert.
- **Lizenz unvollständig.** Der Adapter steht unter Apache 2.0. Die Lizenz des Basismodells nennt die Karte nicht, sie muss separat geprüft werden.
- **Fehlende Betriebsangaben.** VRAM, Durchsatz, Latenz, unterstützte Sprachen und die Architekturdetails fehlen. Deutschsprachige Leistung ist nicht belegt.
- **Selbstprüfung.** Die Kontrollen auf Internet-Nachschlagen von Lösungen und auf Test-Manipulation stammen von den Autoren. Die Rohdaten im Bucket `harness-hub/harness-adapters-trajectories` erlauben eine Gegenprüfung.
