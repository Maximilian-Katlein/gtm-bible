# Unsloth-Quantisierungen von Qwen3.8-27B: Update auf Dynamic v3.1

> **Quelle:** [Unsloth Qwen3.8-27B Quantizations - Dynamic v3.1 Update](https://unsloth.ai/docs/models/qwen3.8) · Unsloth (Dokumentationsseite), Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50491980) mit Unsloth-Teammitglied danielhanchen · Dokumentation mit Diskussion · 2026-11-14
> **Sprecher verkauft:** Quantisierungen (GGUF, NVFP4) von Qwen3.8, die Open-Source-App Unsloth Desktop, Fine-tuning · **Zielmarkt der Aussagen:** Entwickler und Teams, die offene Modelle lokal oder selbst gehostet betreiben, auch auf schwacher Hardware · **Beweislage:** fast ausschließlich Herstellerangaben und eigene Messungen von Unsloth, keine unabhängige Reproduktion.

## Worum es geht
Die Seite beantwortet, welche Quantisierung von Qwen3.8-27B auf welcher Hardware läuft und mit welchen Einstellungen man sie betreibt. Sie richtet sich an Entwickler, die ein dichtes 27B-Modell mit Vision, Reasoning und 256K Kontext selbst betreiben wollen, vom Mac mit 24 GB bis zum Blackwell-Server. Nebenbei trägt Unsloth einen Benchmark-Streit mit dem Wettbewerber ISTA (GSQ-RCO) aus, der methodisch lehrreich ist, aber nur eine Seite zeigt.

## Was man anwenden kann
1. **Quantisierungsstufe nach Gesamtspeicher wählen.** Unsloth nennt den Bedarf als Summe aus RAM und VRAM oder Unified Memory: 1 Bit 7 bis 8 GB, 2 Bit 9 bis 11 GB, 3 Bit 12 bis 14 GB, 4 Bit 16 bis 19 GB, 6 Bit 23 bis 26 GB, 8 Bit 31 GB, BF16 56 GB. Der KV-Cache für lange Kontexte kommt dazu. Wer Multi-Token Prediction (MTP) nutzt, plant 1 bis 2 GB zusätzlich ein.

2. **4 Bit als Standard für 16 bis 24 GB.** Die 4-Bit-Quants laufen laut Unsloth auf RTX 5080, RTX 4090 oder einem Mac mit 24 GB RAM. Eine Tokengeschwindigkeit nennt die Seite dafür nicht. Ein Kommentator meldet, dass er mit 12 GB VRAM und 16 GB RAM unter Windows eine einseitige HTML-Seite bauen ließ; das entspricht nach Tabelle etwa 3 Bit mit Auslagerung in den RAM.

3. **Sampling-Parameter je Modus getrennt setzen.** Thinking: temperature 1.0, top_p 0.95, top_k 20, min_p 0.0, presence_penalty 0.0, repetition_penalty 1.0. Instruct (Non-Thinking): temperature 0.7, top_p 0.80, top_k 20, min_p 0.0, presence_penalty 1.5, repetition_penalty 1.0. Der wichtigste Unterschied ist die presence_penalty von 1.5 im Instruct-Modus.

4. **Reasoning-Aufwand bewusst herunterregeln.** Standard ist xhigh, also die längste Denkspur. Für Alltagsaufgaben stellt man per `--chat-template-kwargs` in `unsloth run` oder `llama-server` auf medium (Ausgleich) oder low (Kosten sparen) um, none schaltet ab. Unter Windows PowerShell müssen die Anführungszeichen maskiert werden.

5. **Preserve Thinking nur dort, wo es sich lohnt.** Die Funktion hält die Denkspur der vorigen Runde im Kontext. Das kostet Tokens und kann laut Unsloth in fortgesetzten Gesprächen die Genauigkeit steigern, beziffert wird der Gewinn nicht. Sinnvoll eher für mehrstufige Agenten-Schleifen als für Einzelanfragen.

6. **Auf NVIDIA Blackwell NVFP4 statt BF16 betreiben.** Die NVFP4-Quants laufen laut Unsloth-Messung unter vLLM 1,41 bis 1,49 mal so schnell wie BF16, über Batchgrößen von 1 bis 64. Voraussetzung sind Blackwell-GPUs (RTX 50, DGX Spark, B200, B300); für ältere Karten empfiehlt Unsloth GGUF. FP8-KV-Cache-Kalibrierung soll doppelt so lange Kontexte erlauben. Für SGLang ist Version v0.5.19 Pflicht, weil Unsloth den lm_head auf FP8 quantisiert.

7. **MTP für Latenz einsetzen, nicht für Durchsatz.** Speculative Decoding per MTP beschleunigt das Decoding einzelner Anfragen, senkt aber laut Seite den Gesamtdurchsatz etwas. Bei vielen parallelen Nutzern ist das abzuwägen.

8. **Eigene Benchmarks mehrfach laufen lassen.** Unsloth fuhr AIME25 mit 14 Durchläufen und kam auf 93 bis 96 Prozent durchschnittliche Recovery, während ISTA nach Unsloths Schätzung aus einem Lauf 100 Prozent meldete. Greedy Decoding mit Temperatur 0 behebt das nicht, weil GPUs nicht deterministisch rechnen, und bildet reale Nutzung schlecht ab. Antworten zusätzlich mit einem zweiten Grader prüfen (Unsloth nutzte Math Verify und LightEval).

9. **Kontextbudget im Vergleich gleich halten.** Bei LiveCodeBench kippt das Ergebnis je nach Budget: Bei 96K liegt GSQ-RCO laut Unsloth leicht vorn, bei 128K liegt UD3 deutlich vorn. Wer Quants vergleicht, dokumentiert Kontextbudget, Sampling und Anzahl der Läufe.

10. **Bei Größenvergleichen die Embedding-Schicht mitzählen.** Exllama-v3 hält die Token-Embeddings in BF16. Unsloth rechnet sie in den Hauptplots heraus, zeigt aber, dass sich die Kurven verschieben, wenn man Download-Größe und RAM vollständig zählt. Für die eigene Hardwareplanung zählt der vollständige Wert.

11. **Unsloth-Quants für agentische Tools prüfen.** Laut Unsloth enthalten die Quants Developer-Role-Support für Tools wie Codex, MTP und ein verbessertes Parsing verschachtelter Objekte beim Tool-Calling. Ob Tool-Aufrufe dadurch messbar häufiger gelingen, belegt die Seite nicht mit Zahlen.

12. **Mit llama.cpp richtig bauen.** Aktuelle Version holen, mit `-DGGML_CUDA=ON` für NVIDIA bauen, `OFF` ohne GPU oder bei reiner CPU-Inferenz; auf Apple ist Metal standardmäßig aktiv. Modell per huggingface_hub laden, Start mit llama-cli. Die konkreten Befehle fehlen im Auszug.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 5 bis 10 % höhere Genauigkeit | Dynamic V3.1 gegenüber eigenen V3.0-Quants bei gleicher Größe, u. a. Terminal Bench, DeepSWE | eigene Daten Unsloth, Einzelwerte im Auszug nicht sichtbar |
| 262.144 Token, per YaRN bis 1M | Kontextfenster Qwen3.8-27B | Herstellerangabe |
| 7 bis 8 GB bis 56 GB | Gesamtspeicher von 1 Bit bis BF16, ohne KV-Cache | Herstellerangabe |
| 1 bis 2 GB | Zusatzspeicher für MTP | Herstellerangabe |
| 89,8 gegen 133,7 tok/s (1,49x) | BF16 gegen NVFP4, Batch 1, vLLM | eigene Daten, Messhardware nicht genannt |
| 3048,5 gegen 4407,2 tok/s (1,45x) | BF16 gegen NVFP4, Batch 64 | eigene Daten |
| 92 bis 97 % | NVFP4 „Accuracy Recovery“, tatsächlich Top-1-Übereinstimmung mit BF16 je Korpus | eigene Daten |
| KLD 0,026 / 0,058 | NVFP4 Code (beste) gegen Chat (schlechteste Domäne) | eigene Daten |
| 93 bis 96 % | AIME25-Recovery, Mittel aus 14 Läufen | eigene Daten |
| 100 % | AIME25-Recovery laut ISTA, nach Unsloths Schätzung aus 1 Lauf | Angabe der Gegenseite, nur über Unsloth überliefert |
| 96K gegen 128K | Kontextbudget GSQ-RCO (geschätzt) gegen Unsloth bei LiveCodeBench | Schätzung von Unsloth |
| 73,0 gegen 63,4 | Terminal Bench 2.1: Qwen3.8-27B gegen Qwen3.6-27B (Opus4.6 Max: 78,2) | Herstellerangabe Qwen |
| 42,2 gegen 13,3 | DeepSWE 1.1: Qwen3.8-27B gegen Qwen3.6-27B | Herstellerangabe Qwen |
| 79,5 gegen 62,5 | IFBench: Qwen3.8-27B gegen Opus4.6 Max | Herstellerangabe Qwen |
| 2x schneller, 70 % weniger VRAM | Fine-tuning mit Unsloth | Herstellerangabe ohne Beleg im Material |
| 397 GB, 91 % kleiner | dynamische 1-Bit-Version von Qwen3.8-2.4T-A95B | Herstellerangabe, keine Genauigkeitsdaten |
| ca. 45 tok/s | „Qwen 3.8 Splash“ mit Thinking auf M4 Mac mini 48 GB, LM Studio | Anekdote, Variante unklar |

## Wortlaute
Textquelle, daher ohne Zeitstempel.

- `--chat-template-kwargs '{"reasoning_effort":"medium"}'` steht für die Umstellung des Reasoning-Aufwands in `unsloth run` oder `llama-server`.
- `--chat-template-kwargs "{\"reasoning_effort\":\"medium\"}"` ist die maskierte Variante für Windows PowerShell.
- „GPUs themselves are non deterministic. That is why you benchmarks should be run multiple times.“ fasst Unsloths Argument gegen Einzelläufe zusammen.

## Grenzen und Widerspruch
- **Eine Seite spricht.** Alle Aussagen zu Dynamic V3.1 und zum Streit mit ISTA kommen von Unsloth, das die Quants selbst anbietet. ISTA kommt nicht zu Wort, die Zahl der ISTA-Läufe und das 96K-Budget sind Unsloths Schätzungen.
- **Nur gegen sich selbst verbessert.** Die 5 bis 10 Prozent beziehen sich auf Unsloths eigene V3.0-Quants. Die Einzelwerte je Quant und die Dateigrößen stehen hinter einem Aufklappbereich und fehlen im Auszug. Die 3-Bit-Quants wurden nicht aktualisiert, weil der Gewinn laut Unsloth zu klein war.
- **Top-1 ist keine Aufgabengenauigkeit.** Die „92 bis 97 Prozent Accuracy Recovery“ von NVFP4 sind Übereinstimmungen der wahrscheinlichsten Token mit BF16. Die Seite setzt das gleich.
- **Widerspruch zu SGLang.** Die Seite sagt erst, NVFP4 laufe nur in vLLM, liefert dann SGLang-Anleitungen ab v0.5.19.
- **Modell-Benchmarks vom Modellanbieter.** Die Vergleichstabelle mit Qwen3.7-Plus, Muse Glimmer-30B und Opus4.6 Max stammt von Qwen. Ob alle Spalten gleich getestet wurden, ist nicht belegt. Opus4.6 Max liegt bei Terminal Bench 2.1 und NL2Repo vorn. Die Tabelle bricht vor GPQA, MMLU-Pro, LiveCodeBench und AIME25 ab.
- **Es fehlt, was für den Einsatz in Firmen zählt:** Lizenz und kommerzielle Nutzung, unterstützte Sprachen, Architekturdetails. Für Sovereign-AI-Entscheidungen reicht die Seite daher nicht.
- **Unbeantwortete Fragen der Diskussion:** Wie schneiden die Quants bei Q5 und höher gegen v3.0 ab? Wie stehen die kleinsten Quants gegen Bonsai 2, gegen die TensorFold-Versionen und gegen die KT/KS-Quants von ik_llama? Ein Kommentator verweist zudem auf ByteShape als weiteren Anbieter. Ein anderer fragt, woher man weiß, welche Parameter wichtig sind; die Seite erklärt den Dynamic-Algorithmus nicht.
- **Praxisberichte sind dünn.** Die 45 tok/s auf dem M4 Mac mini betreffen ein Modell namens „Qwen 3.8 Splash“, das auf der Seite nicht vorkommt. Der 12-GB-Bericht nennt weder Quantisierung noch Tempo. Ein Kommentator wünscht sich ausdrücklich, dass 27B-Modelle mit vernünftigem KV-Cache auf schwachen GPUs auch langsam laufen; ob das gelingt, bleibt offen.
