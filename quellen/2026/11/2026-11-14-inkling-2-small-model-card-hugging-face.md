# Inkling 2 Small (Modellkarte, Hugging Face)

> **Quelle:** [Inkling 2 Small (Model Card, Hugging Face)](https://huggingface.co/thinkingmachines/Inkling-2-Small) · Thinking Machines · Model Card · 2026-11-14
> **Sprecher verkauft:** das Open-Weight-Modell Inkling 2 Small unter Apache 2.0 und die eigene Plattform Tinker (Playground, API, Fine-Tuning) · **Zielmarkt der Aussagen:** Entwickler von Agenten, Coding-Assistenten, Chatbots und RAG-Systemen · **Beweislage:** ausschließlich Herstellerangaben, Benchmarks ohne unabhängige Prüfung, das Material bricht mitten in der Benchmark-Tabelle ab

## Worum es geht
Die Karte beantwortet, was Inkling 2 Small ist, welche Hardware es braucht und wie es sich in Herstellertests gegen offene und geschlossene Modelle schlägt. Sie richtet sich an Teams, die ein offenes, multimodales Modell selbst betreiben, nachtrainieren oder über einen API-Anbieter nutzen wollen. Inkling 2 Small nimmt Text und Bilder an und gibt Text aus, mit 594 Mrd. Parametern gesamt und 17 Mrd. aktiv pro Token.

## Was man anwenden kann
1. **Hardware nach Checkpoint planen.** Der Hauptcheckpoint in NVFP4 braucht laut Karte mindestens 500 GB aggregierten VRAM, als Beispiele nennt sie 2x NVIDIA B300 oder 4x NVIDIA H200. Der MXFP8-Checkpoint (eigenes Repo Inkling-2-Small-MXFP8) braucht mindestens 800 GB, etwa 4x B300 oder 8x H200. Ein Einzelrechner mit Consumer-GPU reicht in keinem Fall.

2. **NVFP4 nehmen, nicht MXFP8.** Das Modell wurde in NVFP4 vortrainiert, midtrainiert und posttrainiert, das ist seine native Präzision. MXFP8 bringt laut Hersteller auf seinen Evals nur 1 bis 2 Prozentpunkte. Für 300 GB mehr VRAM lohnt sich der Wechsel nach Herstellerangabe in keinem praktischen Fall. Das gilt für die Evals des Herstellers, eigene Aufgaben sollte man stichprobenartig gegenprüfen.

3. **Dateigröße vor der Beschaffung nachrechnen.** Aus den Safetensors-Metadaten ergibt sich rechnerisch eine Dateigröße von rund 601 GB (U8, F8_E4M3, BF16, F32 aufsummiert). Das passt nicht sauber zur Angabe „mindestens 500 GB VRAM“ für NVFP4. Vor einer Clusterplanung die tatsächlichen Dateigrößen im Repo prüfen und den KV-Cache für die gewünschte Kontextlänge hinzurechnen.

4. **Inferenz-Framework aus der Liste wählen.** Für den Betrieb auf eigener Hardware nennt die Karte SGLang, vLLM, TokenSpeed und Unsloth mit eigenen Recipe-Seiten, dazu Hugging Face Transformers. Wer schon einen dieser Stacks betreibt, startet dort.

5. **Ohne eigenen Cluster über API testen.** Gehostet bieten das Modell laut Karte NVIDIA, Fireworks, Together, Baseten, Nebius, Modal und Cloudflare (Workers AI) an, dazu der Tinker Playground. Preise, Durchsatz, Latenz und Hosting-Regionen stehen nicht in der Karte. Wer EU-Hosting oder souveränen Betrieb braucht, muss die Region beim jeweiligen Anbieter separat klären.

6. **Fine-Tuning-Werkzeug passend zum Setup wählen.** Weitertrainieren lässt sich das Modell mit Miles, SkyRL und Snowflake Cortex Training. Für Fine-Tuning auf Tinker braucht man zusätzlich das PyPI-Paket tml-renderers. Der API-Zugriff ist im Tinker Cookbook auf GitHub (thinking-machines-lab/tinker-cookbook) beschrieben.

7. **Benchmarks nur mit ihrem Harness lesen.** Jede Coding- und Agenten-Zeile nennt ihr Agent-Harness: stirrup v0.2.1, mini-swe-agent v2.4.6, openhands (Vals-Variante), Claude Code, pi v0.83.0, terminus v2. Wer die Zahlen reproduzieren will, braucht genau diese Versionen. Auf ein anderes Agenten-Setup sind die Werte nicht übertragbar.

8. **DeepSeek-V4.1-Flash-1017 als Prüfmaßstab mitlaufen lassen.** In der Herstellertabelle liegt das ähnlich große DeepSeek-V4.1-Flash-1017 (16/552 Mrd.) in neun Zeilen vor Inkling 2 Small, darunter Vals Index (61,3 zu 56,1 %) und DeepSWE (77,0 zu 72,1 %). Inkling führt nur bei PostTrainBench (31,9 zu 30,5 %). Wer eine Auswahl trifft, sollte beide Modelle auf eigenen Aufgaben gegeneinander testen.

9. **Lizenz und Nutzungsrichtlinie getrennt prüfen.** Die Gewichte stehen unter Apache 2.0, freigegeben laut Karte für Forschung, Fine-Tuning und Integration in Produkte Dritter. Daneben verlinkt die Karte eine Acceptable Use Policy, deren Inhalt und rechtliches Verhältnis zur Apache-Lizenz sie nicht erklärt. Für kommerziellen und regulierten Einsatz das Dokument vor der Entscheidung lesen.

10. **Deutsch selbst testen.** Hauptsprache ist Englisch, dazu „allgemeine mehrsprachige Fähigkeiten“. Eine Sprachliste, Aussagen zu Deutsch oder mehrsprachige Benchmarks fehlen. Für deutschsprachige Anwendungen ist ein eigener Test Pflicht.

11. **Bildeingaben im empfohlenen Bereich halten.** Bilder sind in jedem Pixelformat erlaubt, ideal sind 40 bis 4096 Pixel pro Kante. Außerhalb dieses Bereichs ist die Leistung nicht zugesichert. Video steht nicht als Eingabe auf der Liste, obwohl die Trainingsdaten laut Karte Video enthalten.

12. **Die 1 Mio. Token Kontext unter Last prüfen.** Die Karte nennt ein Kontextfenster bis 1 Mio. Token, im vorliegenden Teil aber weder Long-Context-Benchmarks noch den Speicherbedarf des KV-Cache. Wer lange Dokumente oder große RAG-Kontexte plant, muss Qualität und Speicher bei voller Länge selbst messen.

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 594 Mrd. / 17 Mrd. | Parameter gesamt / aktiv pro Token | Herstellerangabe |
| 48 Schichten, 8 von 384 Experten | Decoder-Tiefe, Mixture-of-Experts-Routing pro Token | Herstellerangabe |
| 1 Mio. Token | maximales Kontextfenster | Herstellerangabe |
| 40 bis 4096 px | empfohlene Bildgröße pro Kante | Herstellerangabe |
| ≥ 500 GB VRAM | NVFP4-Hauptcheckpoint (2x B300 oder 4x H200) | Herstellerangabe |
| ≥ 800 GB VRAM | MXFP8-Checkpoint (4x B300 oder 8x H200) | Herstellerangabe |
| 1 bis 2 Prozentpunkte | Vorsprung MXFP8 gegenüber NVFP4 auf Hersteller-Evals | Herstellerangabe |
| rund 601 GB | Dateigröße, eigene Summe aus den Safetensors-Metadaten | eigene Rechnung aus Herstellerdaten |
| 30,6 | AA Index v5.0 (Bestwert Claude Haiku 5.5: 36,5) | Herstellerangabe |
| 56,1 % | Vals Index v2.2 (Bestwert DeepSeek-V4.1-Flash-1017: 61,3 %) | Herstellerangabe |
| 25,4 % | FrontierCode v2.0, Harness stirrup v0.2.1 (Bestwert Haiku 5.5: 34,9 %) | Herstellerangabe |
| 72,1 % | DeepSWE v1.1, mini-swe-agent v2.4.6 (Bestwert DeepSeek: 77,0 %) | Herstellerangabe |
| 5,7 % | Terminal Bench Science v0.1 (Bestwert Haiku 5.5: 20,0 %) | Herstellerangabe |
| 81,6 % | Vibe Code Bench v1.1, openhands/Vals (Bestwert Haiku 5.5: 90,4 %) | Herstellerangabe |
| 61,9 % | SWE-Atlas v1.1, zweitbester Wert, nur 7 von 13 Modellen mit Wert | Herstellerangabe |
| 86,3 % | SWEBench Pro v2 Hard (Bestwert 89,7 %, Haiku 5.5 52,9 %, Gemini 3.8 Flash 58,8 %) | Herstellerangabe |
| 14,1 % | Sudo L7, Bestwert, nur 5 von 13 Modellen mit Wert | Herstellerangabe |
| 31,9 % | PostTrainBench v1.2 in Claude Code, nur 5 Modelle mit Wert | Herstellerangabe |
| 494,27 | PMPP-Hard, Fläche unter der Kurve über 0 bis 10 h, keine Prozentzahl | Herstellerangabe |
| 70,0 % | BioMysteryBench, terminus v2 (Bestwert Kimi K3: 72,6 %) | Herstellerangabe |
| 274 bis 277 Likes, 1064 Downloads | Stand der Hugging-Face-Seite zum Erfassungszeitpunkt, Repo angelegt 04.11.2026 | Seitenmetadaten |

## Grenzen und Widerspruch
- **Unvollständiges Material.** Die Erfassung bricht in der Benchmark-Tabelle bei der Zeile BrowseComp (Abschnitt Search and Tools) ab. Tool- und Suchbenchmarks, mögliche Abschnitte zu Long Context, multimodalen Tests, Sicherheit und Limitierungen sowie empfohlene Sampling-Einstellungen und Chat-Template fehlen.
- **Nur Herstellerzahlen.** Auswahl der zwölf Vergleichsmodelle, leere Zellen und Eval-Setup (Reasoning-Aufwand, Sampling, Prompts) stammen von Thinking Machines. Eine unabhängige Nachprüfung enthält die Karte nicht. Der „AA Index“ wird nur mit Kürzel benannt.
- **Auffällige Ausreißer.** Bei SWEBench Pro v2 Hard liegen die offenen Modelle bei 82 bis 90 %, Claude Haiku 5.5 und Gemini 3.8 Flash aber bei 53 bzw. 59 %. Bei Vibe Code Bench fällt GLM-5.3-Flash auf 30,8 %. Die Karte erklärt beides nicht. Inklings Vorsprung gegen Haiku 5.5 bei SWEBench Pro hängt an diesem Ausreißer.
- **Dünne Zeilen.** Sudo L7, PostTrainBench, PMPP-Hard und BioMysteryBench haben nur fünf bis sechs Werte. Ein „Bestwert“ dort sagt wenig über das ganze Feld. In Terminal Bench Science sind die absoluten Werte so niedrig, dass Abstände von wenigen Punkten kaum aussagekräftig sind.
- **Effizienz nur selektiv.** Mit 17 Mrd. aktiven Parametern liegt Inkling beim AA Index vor Mistral Large 4 (49 Mrd. aktiv, 26,1) und Muse Spark Open (42 Mrd. aktiv, 24,9) und schlägt bei FrontierCode alle fünf Pro-Modelle. Bei Terminal Bench Science und SWEBench Pro liegen dagegen mehrere Pro-Modelle vorn.
- **Hardware unklar.** Die rechnerische Dateigröße von rund 601 GB passt nicht klar zu „mindestens 500 GB VRAM“. Offen bleiben KV-Cache bei 1 Mio. Token, Durchsatz und Latenz auf B300 oder H200 und ob NVFP4 auf H200 nativ oder per Umrechnung läuft. Die Seitentags „8-bit“ und „modelopt“ deuten auf eine Quantisierung mit NVIDIA Model Optimizer hin, die Karte sagt das nicht.
- **Keine Trainingstransparenz.** Datenquellen werden nur grob genannt (öffentlich, zugekauft, intern, synthetisch). Datenmenge, Token-Zahl, Wissensstichtag, Rechenaufwand und Sicherheitsevaluierung fehlen. Einen Vorgänger oder Neuerungen gegenüber einer früheren Version nennt die Karte nicht.
- **Souveränität offen.** Keine Aussage zu EU-Einsatz, AI-Act-Pflichten, Hosting-Regionen der API-Anbieter oder Preisen für Tinker und Drittanbieter. Für regulierte deutsche Unternehmen ist das Modell erst nach eigener Klärung von Lizenzrichtlinie, Region und Sprachqualität einsetzbar.
