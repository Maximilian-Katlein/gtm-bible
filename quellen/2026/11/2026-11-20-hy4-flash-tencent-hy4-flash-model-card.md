# Hy4 flash (tencent/Hy4-flash): Modellkarte

> **Quelle:** [Hy4 flash (tencent/Hy4-flash) Model Card](https://huggingface.co/tencent/Hy4-flash) · Tencent Hy Team, Tencent · Model Card · 2026-11-20
> **Sprecher verkauft:** Open-Weight-Sprachmodell mit Bildeingabe (Instruct, FP8, Base) unter der Tencent Hy License · **Zielmarkt der Aussagen:** Entwickler und Unternehmen, die günstige Modelle für Alltags-Produktivität und Agenten selbst betreiben wollen · **Beweislage:** ausschließlich Herstellerangaben, Leistung und Kosten vor allem auf internen Benchmarks und mit internen Nutzern gemessen

## Worum es geht
Die Karte beantwortet eine Frage: Wie viel Agenten- und Büroleistung bekommt man mit einem Modell, das nur 12B aktive Parameter pro Token rechnet, aber 220B Parameter im Speicher hält? Sie richtet sich an Teams, die ein günstiges Modell für Folien, Dokumente, Deep Search und Computer Use selbst hosten wollen und dafür einen 8-GPU-Server haben.

## Was man anwenden kann

1. **Variante nach Zweck wählen.** Es gibt drei Gewichte: Hy4 flash (Instruct), Hy4 flash-FP8 und Hy4 flash-base. Die Base-Variante ist ausdrücklich kein Chat-Modell. Alle Chat-, Reasoning- und Deployment-Beispiele gelten nur für Instruct und FP8. Wer ein Produkt baut, startet mit FP8, wer selbst nachtrainieren will, mit Base.

2. **Einsatzgrenze ernst nehmen.** Tencent empfiehlt Flash für Deep Search, Dokumentverarbeitung, Folienerstellung, einfache Frontend-Demos und Computer Use. Für langfristiges Software Engineering verweist der Hersteller selbst auf das größere Hy4. Das deckt sich mit den Zahlen: Auf dem Code-Benchmark MBPP-plus liegt Flash Base mit 73,7 hinter allen Vergleichsmodellen außer Hy4 Base (74,0).

3. **Faktenlastige Anwendungen mit Retrieval absichern.** Bei SimpleQA erreicht Flash Base 37,5, Hy4 Base 57,2. Auch Chinese-SimpleQA (74,6 zu 83,9) zeigt deutlich weniger gespeichertes Weltwissen. Eigene Ableitung aus den Herstellerzahlen: Für Recherche, Produktwissen oder Support sollte man Fakten per Retrieval zuführen, statt sich auf das Modellwissen zu verlassen.

4. **Hardware realistisch planen.** Beide Referenz-Setups nutzen FP8 mit Tensor Parallel 8, also acht GPUs. GPU-Typ und VRAM nennt die Karte nicht. Eigene Überschlagsrechnung aus 220,24B BF16-Parametern: rund 440 GB Gewichte in BF16, rund 220 GB in FP8, dazu KV-Cache und Aktivierungen. Die 12B aktiven Parameter senken die Rechenlast, nicht den Speicherbedarf.

5. **Mit vLLM ausrollen.** Offizielles Image `vllm/vllm-openai:hy4-flash`, Modell `tencent/Hy4-flash-FP8`. Wichtige Flags: `--tensor-parallel-size 8`, Speculative Decoding mit Methode `dfly` und 5 Tokens, `--attention-backend FLASHMLA_SPARSE`, Tool-Call- und Reasoning-Parser `hy_v4`, `--enable-auto-tool-choice`. Der Server spricht danach die OpenAI-kompatible API, bestehende Clients lassen sich also umhängen.

6. **Alternativ mit SGLang ausrollen.** Image `lmsysorg/sglang:hy4-flash` für x86 und Arm. Start mit `--tp 8`, `--speculative-algorithm DFLY`, `--speculative-dfly-block-size 6` und `--cuda-graph-backend-prefill disabled`. Rezepte liegen zusätzlich im vLLM-Recipes-Katalog und im SGLang-Cookbook.

7. **Reasoning pro Anfrage steuern.** `reasoning_effort` kennt `high` (Standard, Thinking an) und `no_think` (direkte Antwort). Über die API setzt man das per `extra_body` in `chat_template_kwargs`. Empfohlenes Sampling: temperature 0,9, top_p 1,0. Für einfache Extraktions- oder Klassifikationsschritte in Agenten spart `no_think` Tokens und Zeit.

8. **Speculative Decoding nicht abschalten.** Der eingebaute Drafter DFly2 (5 Schichten, 0,85B Parameter) teilt KV-Cache und die bis zu 2.048 ausgewählten Positionen mit dem Zielmodell. Laut Hersteller sieht jedes Draft-Token höchstens etwa 2K Keys, die Kosten bleiben bei langem Kontext also konstant. Ein zusätzlicher KV-Speicher entfällt, und getrennte Prefill/Decode-Infrastruktur wird unterstützt.

9. **Transformers nur für Tests.** Die Unterstützung ist noch nicht im Hauptzweig. Installiert wird aus dem offenen Pull-Request 50903, geladen über `AutoProcessor` und `AutoModelForImageTextToText`. Für Produktion ist das kein stabiler Pfad. Dasselbe gilt für das GGUF unter `AngelSlim/Hy4-flash-GGUF`, das Tencent ausdrücklich als Testversion beschreibt.

10. **Lizenz vor dem Einsatz lesen.** Die Karte nennt nur „Tencent Hy License“ (Metadaten: license other). Kommerzielle Nutzung, Gebietsausschlüsse und EU-Nutzung stehen nicht auf der Karte. Wer das Modell für souveräne KI oder in der EU einsetzen will, muss die LICENSE-Datei rechtlich prüfen lassen.

11. **Eigene Evaluation nach Tencent-Muster aufsetzen.** Tencent misst neben Public Benchmarks vor allem Qualität des Liefergegenstands, Ausgabelänge pro Turn und Durchlaufzeit, mit der Begründung, öffentliche Scores seien vom Arbeitsalltag entkoppelt. Das Muster lässt sich übertragen: eigene Aufgaben aus dem Arbeitsalltag, Blindbewertung durch Nutzer, Kosten und Dauer pro Task mitschreiben.

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 220B gesamt, 12B aktiv | Parameter, davon rund 64B Engram-Tabellen | Herstellerangabe |
| 1.048.576 Tokens | Maximaler Kontext, Eingabe Text und Bild, Ausgabe Text | Herstellerangabe |
| 16 von 512 | Aktivierte Routed Experts pro Token, plus 1 Shared Expert, 41 MoE-Schichten | Herstellerangabe |
| 1:3 | Verhältnis Sparse- zu Sliding-Window-Attention (12 zu 30 Schichten) | Herstellerangabe |
| 1/24 bzw. 1/6 | KV-Cache gegenüber Hy3 bzw. Hy4, ohne Kontextlänge oder Messaufbau | Herstellerangabe |
| über 150 Tokens/s | Decoding mit Megakernels, 4-Bit und DFly2; Hardware und Batchgröße fehlen | Herstellerangabe |
| minus 50 % | Durchschnittliche Ausgabe-Tokens nach Reinforcement Learning | Herstellerangabe |
| 42,1 / 39,7 / 51,4 | WorkIndex: Hy4 flash / Hy4 preview / Hy4 | Herstellerangabe, interner Benchmark |
| 1/13, 1/20, 1/8 | Kosten pro WorkIndex-Task gegenüber Hy4 preview, Hy4, DeepSeek-V4.1-Flash-1017 (Max-Stufe, Peak-Hour-Preise) | Herstellerangabe, ohne Tokenpreise |
| 2,79 zu 2,81 von 4 | Nutzerzufriedenheit Hy4 flash gegenüber Claude Haiku 5.5 | Herstellerangabe, 85 interne Nutzer, 259 Tasks, ohne Signifikanz |
| 6,7 Minuten, 0,26 RMB | Median-Dauer und Kosten pro Task in derselben Blindstudie | Herstellerangabe |
| 71,1 zu 68,6 | MMLU-Pro, Flash Base gegenüber DeepSeek-V4-flash-Base | Herstellerangabe, Few-Shot |
| 73,7 | MBPP-plus Flash Base, schwächster Wert der Vergleichsgruppe außer Hy4 Base | Herstellerangabe |
| 37,5 zu 57,2 | SimpleQA Flash Base gegenüber Hy4 Base | Herstellerangabe |
| 93,8 | Belebele, 5 Sprachen inklusive Deutsch, Flash Base | Herstellerangabe |
| 52,0 zu 59,6 | MMMU-Pro, Flash Base gegenüber Hy4 Base | Herstellerangabe |

## Wortlaute

- „Hy4 flash-base is a pre-trained base model, not an instruction-tuned chat model.“ (Model Card, Varianten) Steht für die Abgrenzung: Base nicht als Chat-Modell einsetzen.
- „For complex tasks such as long-horizon software engineering, we recommend Hy4 for its higher intelligence ceiling.“ (Model Card, Einsatz) Der Hersteller zieht die Leistungsgrenze selbst.
- „--speculative-config '{"num_speculative_tokens":5,"method":"dfly"}'“ (Model Card, vLLM-Deployment) Die Zeile, die den eingebauten Drafter im vLLM-Server aktiviert.
- „Recommended sampling parameters: temperature=0.9, top_p=1.0.“ (Model Card, Quickstart) Vorgabe für Instruct und FP8.
- „we have provided a GGUF compressed version for end-to-end testing purposes.“ (Model Card, Quantisierung) Markiert das GGUF als Testformat, nicht als Produktionsweg.

## Grenzen und Widerspruch

- **Nur Herstellerangaben.** Es gibt keine unabhängigen Reproduktionen und keine Diskussion zur Karte. WorkIndex ist intern, die Blindstudie lief mit 85 internen Nutzern des eigenen Produkts WorkBuddy. Die Aufgaben sind damit vom Hersteller ausgewählt.
- **„Nah an Claude Haiku 5.5“ ist dünn belegt.** 0,02 Punkte Abstand ohne Signifikanzangabe sagen wenig. Ob Flash auf den eigenen Aufgaben mithält, muss man selbst messen.
- **Instruct-Scores fehlen im Text.** Alle Werte der Instruct-Variante, auch die sieben öffentlichen Agent-Benchmarks (DeepSWE, ProgramBench, Terminal-Bench 4.0, APEX-Agents, AutomationBench, HLE, OSWorld 2.1), stehen nur in Grafiken. Die Texttabelle zeigt ausschließlich Base-Modelle.
- **Base-Zahlen eingeschränkt vergleichbar.** Laut Karte hält das Base-Modell wegen synthetischer Instruktionsdaten im Mid-Training in Few-Shot-Tests das Antwortformat gelegentlich nicht ein. ARC-Challenge und HellaSwag laufen auf Teilmengen (299 bzw. 3.000 Beispiele). Fettdruck markiert nur den Höchstwert, keine Signifikanz.
- **Kostenvergleich nicht nachrechenbar.** Tokenpreise, Wechselkurs und Rechenweg fehlen. Der DeepSeek-Vergleich gilt nur zu Peak-Hour-Preisen der Max-Stufe. Die 150 Tokens/s gelten für den Tencent-Stack, nicht zwingend für vLLM oder SGLang auf eigener Hardware.
- **Deutsch kaum geprüft.** Belebele ist ein Leseverständnistest mit Deutsch als einer von fünf Sprachen, Deutsch wird nicht einzeln ausgewiesen. Für deutschsprachige Textgenerierung gibt es keinen Beleg.
- **Lizenz offen.** Ohne Lektüre der LICENSE-Datei ist unklar, ob kommerzielle Nutzung oder Nutzung in der EU erlaubt ist. Für Sovereign-AI-Projekte ist das der erste Prüfschritt.
- **Weitere Lücken.** Trainingsdaten, Tokenzahl, Wissensstichtag, Sicherheits- und Alignment-Details fehlen. Das Verhältnis von Hy4, Hy4 preview und Hy3 preview und der Open-Weight-Status von Hy4 werden nicht erklärt. Bitbreiten und Qualitätsverlust des GGUF sind nicht angegeben, die 4-Bit-Variante der Tencent-Inferenz steht nicht zum Download.
- **Kleine Unstimmigkeit.** Die Tabelle nennt 63,5B Engram-Parameter, die Engram-Beschreibung 63,4B für die Embedding-Tabelle.
