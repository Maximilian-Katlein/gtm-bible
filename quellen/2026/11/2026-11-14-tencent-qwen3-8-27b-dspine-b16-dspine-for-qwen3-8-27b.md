# DSpine für Qwen3.8-27B: Draft-Modell für spekulatives Decoding (tencent/Qwen3.8-27B-DSpine-b16)

> **Quelle:** [tencent/Qwen3.8-27B-DSpine-b16 (DSpine for Qwen3.8-27B)](https://huggingface.co/tencent/Qwen3.8-27B-DSpine-b16) · Tencent (Autoren laut Zitat: Zhang Haohui, Chen Keyu, Sun Haocheng, Gu Weibo, Qiao Ruizhi, Sun Xing, Jiang Bo) · Model Card · 2026-11-14
> **Sprecher verkauft:** Kostenloses Open-Weight Draft-Modell (Apache 2.0), das die Inferenz von Qwen3.8-27B beschleunigt; Tencent positioniert damit das eigene Verfahren DSpine gegenüber DFlash2 · **Zielmarkt der Aussagen:** Teams, die Qwen3.8-27B selbst mit SGLang hosten, vor allem für agentische Workloads (Code, Web, Office, Tool-Calling) · **Beweislage:** ausschließlich Herstellermessungen ohne Hardwareangabe, bei nur einer Lastgröße (Concurrency 8) und mit ungleichen Blockgrößen im Vergleich.

## Worum es geht
Die Karte beantwortet eine Frage: Wie viel schneller liefert ein selbst gehostetes Qwen3.8-27B Tokens aus, wenn man ein kleines Draft-Modell mit dem Verfahren DSpine davorschaltet? Sie richtet sich an Betreiber eigener Inferenz, die Durchsatz pro GPU steigern wollen, ohne das Zielmodell zu wechseln. Für souveräne oder On-Premise-Setups ist das relevant, weil die Beschleunigung vollständig lokal läuft.

## Was man anwenden kann
1. **Draft-Modell nur als Ergänzung einplanen.** Der Checkpoint ist kein eigenständiges Sprachmodell. Er schlägt Tokens vor, die Qwen3.8-27B prüft. Er hat rund 2,03 Mrd. Parameter in BF16, nach eigener Rechnung etwa 4,05 GB Gewichte zusätzlich zum 27-Mrd.-Zielmodell. Ohne das Zielmodell ist er nutzlos, ein gehostetes Inference-Widget gibt es nicht.

2. **Installation in zwei Schritten.** Zuerst das Repository github.com/Tencent/DSpine klonen und mit `pip install -e .` installieren. Danach SGLang mit `--speculative-algorithm DSPINE` starten und Zielmodell (`--model-path Qwen/Qwen3.8-27B`) sowie Draft-Pfad (`--speculative-draft-model-path`) getrennt angeben. `--speculative-num-draft-tokens 16` entspricht der Blockgröße b16 im Modellnamen.

3. **Die dokumentierte Konfiguration als Startpunkt übernehmen.** BF16, FlashAttention 3 für Ziel- und Draft-Modell (`fa3`), `flashinfer` als Sampling-Backend, `--mem-fraction-static 0.80`, `--context-length 131072`, `--max-running-requests 8`. Getestet ist nur SGLang 0.5.22. Für vLLM, llama.cpp, Ollama oder Quantisierungen wie FP8 und GGUF gibt es keine Angaben.

4. **Die Mamba/SSM-Flags nicht weglassen.** Der Befehl setzt `--enable-linear-replayssm-spec`, `--mamba-ssm-dtype float32`, `--mamba-radix-cache-strategy extra_buffer` und `--max-mamba-cache-size 64`. Das legt nahe, dass Qwen3.8-27B lineare Attention oder SSM-Schichten enthält und ReplaySSM den Zustand zurücksetzt, wenn Draft-Tokens verworfen werden. Diese Deutung ist ein Schluss aus den Flags, die Karte beschreibt die Zielarchitektur nicht.

5. **`--trust-remote-code` bewusst entscheiden.** Der Startbefehl führt Code aus dem Repository aus. In Umgebungen mit Sicherheits- oder Souveränitätsanforderungen den Code vor dem Einsatz prüfen und eine feste Version pinnen.

6. **Für Agenten-Workloads die Parser mitsetzen.** `--reasoning-parser qwen3` und `--tool-call-parser qwen3_coder` sind auf Reasoning-Ausgaben und Tool-Calls ausgelegt. Die größten Speedups misst Tencent bei Office-Aufgaben (bis 3,84x gegenüber autoregressivem Decoding), die kleinsten Vorsprünge gegenüber DFlash2 bei SWE-bench Pro und τ²-bench.

7. **Kapazität am Durchsatz planen, nicht an der Acceptance Length.** Bei Office (Reasoning low) steigt die Acceptance Length gegenüber DFlash2 um 33 Prozent, der Durchsatz nur um 21 Prozent (eigene Rechnung). Realistisch sind laut Herstellerwerten +8 bis +21 Prozent Durchsatz gegenüber DFlash2 und 2,71x bis 3,84x gegenüber Decoding ohne Spekulation, jeweils bei Concurrency 8.

8. **Mit eigener Last nachmessen.** Alle Zahlen gelten für 8 parallele Requests auf unbekannter GPU. Wer mehr Parallelität fährt, sollte selbst messen: Spekulatives Decoding bringt bei hoher Batchgröße typischerweise weniger, die Karte liefert dazu keine Kurve.

9. **Lizenz zweistufig prüfen.** Das Draft-Modell steht unter Apache 2.0 ohne zusätzliche Einschränkungen. Für den Produktivbetrieb zählt aber auch die Lizenz von Qwen3.8-27B, die nicht in dieser Karte steht.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 2.025.912.064 Parameter (BF16) | Größe des Draft-Modells | Herstellerangabe |
| ca. 4,05 GB | Gewichte des Drafts, 2 Byte pro Parameter | eigene Rechnung |
| 5 Schichten, Blockgröße 16, Sliding Window 8.192 | Konfiguration des Checkpoints | Herstellerangabe |
| 4.332 Downloads | Stand der Metadaten nach Veröffentlichung am 2026-11-07 | Herstellerangabe |
| 7,20 gegen 5,69 | Acceptance Length GSM8K, DSpine gegen DFlash2, T=0 | Herstellerangabe |
| +9,0 bis +26,5 % | Vorsprung Acceptance Length bei T=0 (MT-Bench bis GSM8K) | eigene Rechnung aus Herstellerwerten |
| +3,6 bis +15,8 % | Vorsprung Acceptance Length bei T=1 | eigene Rechnung aus Herstellerwerten |
| 5,63 gegen 4,24 | Acceptance Length WorkBuddy Office, Reasoning low | Herstellerangabe |
| 805,53 Tokens/s (3,84x) | Durchsatz WorkBuddy Office low, DSpine gegen AR 210,03 | Herstellerangabe |
| 978,39 Tokens/s (2,87x) | Durchsatz τ²-bench xhigh, höchster Absolutwert | Herstellerangabe |
| 686,23 gegen 590,27 Tokens/s | Durchsatz WorkBuddy Code low, DSpine gegen DFlash2 | Herstellerangabe |
| +8 bis +21 % | Durchsatzvorsprung DSpine gegen DFlash2 über alle Agent-Benchmarks | eigene Rechnung aus Herstellerwerten |
| 2,71x bis 3,84x | Speedup DSpine gegen AR (DFlash2: 2,33x bis 3,17x) | Herstellerangabe |
| 193,00 bis 340,39 Tokens/s | Spannweite der AR-Baseline bei Agent-Benchmarks | Herstellerangabe |
| 20 Konversationen | Stichprobe pro WorkBuddy-Teilmenge | Herstellerangabe |
| T=1,0, top_p=0,95, top_k=20 | Sampling-Parameter der Temperature-Läufe | Herstellerangabe |

## Wortlaute
- „This checkpoint is a five-layer draft model for Qwen3.8-27B, with block size 16 and an 8,192-token sliding window.“ Kernbeschreibung, was der Checkpoint ist und was nicht.
- „Each layer passes predicted predecessor features to adjacent positions, carrying causal dependencies through network depth.“ Die Architekturidee: Tokens parallel entwerfen, Abhängigkeiten über die Tiefe statt über Zeitschritte führen (Adjacent Causal Injection).
- „--speculative-algorithm DSPINE --speculative-draft-model-path /path/to/Qwen3.8-27B-DSpine-b16 --speculative-num-draft-tokens 16“ Die drei Flags, die DSpine in SGLang aktivieren.
- „Throughput is total output tokens divided by end-to-end concurrent replay wall time (tokens/s).“ Die Definition, an der man eigene Messungen ausrichten kann.
- „Draft blocks: DSpine 16; official DFlash2 8.“ Der Satz, der die Vergleichbarkeit der Baseline einschränkt.

## Grenzen und Widerspruch
- **Hardware fehlt.** Absolute Durchsätze in Tokens/s ohne GPU-Typ, Anzahl und VRAM lassen sich nicht auf die eigene Infrastruktur übertragen. Der Gesamtspeicherbedarf von Ziel- plus Draft-Modell ist nicht beziffert.
- **Vergleich nicht sauber getrennt.** DSpine läuft mit Blockgröße 16, DFlash2 mit 8. Eine Ablation, die den Effekt der Blockgröße von dem der Architektur trennt, fehlt. Ob DFlash2 ebenfalls mit Dynamic Verification und ReplaySSM lief, bleibt offen. Andere Spekulationsverfahren werden nicht verglichen.
- **Nur eine Lastgröße.** Gemessen wurde ausschließlich bei Concurrency 8. Für Produktionsbetrieb mit vielen parallelen Nutzern fehlt jede Aussage.
- **Kleine, nachgespielte Stichprobe.** WorkBuddy Bench umfasst 20 Konversationen pro Teilmenge und spielt aufgezeichnete Trajektorien ab, statt Agenten live laufen zu lassen. Zum Aufbau von SWE-bench Pro und τ²-bench gibt es keine Beschreibung.
- **Qualität nicht belegt.** Die Karte definiert Acceptance Length nicht, sagt nicht ausdrücklich, dass die Ausgabe identisch zum Zielmodell bleibt, und enthält keine Qualitätsbenchmarks.
- **Unerklärte Schwankungen.** Die AR-Baseline reicht von 193,00 bis 340,39 Tokens/s und sinkt bei Code von low auf xhigh. Bei τ²-bench fällt die Acceptance Length von DSpine von 5,53 auf 4,95, wenn das Reasoning auf xhigh steigt. Die Karte erklärt beides nicht.
- **Lange Kontexte ungetestet.** Das Sliding Window des Drafts beträgt 8.192 Tokens, der Server läuft mit 131.072 Tokens Kontext. Wie gut der Draft bei sehr langen Eingaben trifft, ist nicht gemessen.
- **Sprache und Training.** Keine Angaben zu Trainingsdaten, Trainingsmethode und Sprachen. Ob der Speedup bei deutschsprachigen Inhalten ähnlich ausfällt, ist offen.
- **Gebunden an ein Zielmodell und eine Laufzeit.** Der Draft hilft nur bei Qwen3.8-27B und ist nur für SGLang 0.5.22 dokumentiert.
