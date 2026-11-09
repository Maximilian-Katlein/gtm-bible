# Kimi K3.1 Pro: Model Card auf Hugging Face

> **Quelle:** [moonshotai/Kimi-K3.1-Pro (Model Card auf Hugging Face)](https://huggingface.co/moonshotai/Kimi-K3.1-Pro) · Moonshot AI, Moonshot AI · Model Card · 2026-11-09
> **Sprecher verkauft:** Open-Weight-Sprachmodell (multimodal, agentisch), zusätzlich nutzbar über Kimi-Chat und API · **Zielmarkt der Aussagen:** Entwickler und Unternehmen, die ein Modell nahe an der Spitzenklasse für Coding, Agenten, Büro- und Finanzrecherche selbst betreiben oder per API nutzen wollen · **Beweislage:** Alle Zahlen sind Herstellerangaben, mehrere Benchmarks sind hauseigen, das Material bricht mitten in der Tabelle ab.

## Worum es geht
Die Card beantwortet eine Frage: Wie nah kommt ein Open-Weight-Modell der 3T-Klasse an die geschlossenen Spitzenmodelle heran, und wo nicht? Sie richtet sich an Teams, die zwischen Selbst-Hosting, API und Closed-Anbietern wählen. Für souveränen Betrieb liefert sie die Architekturdaten, aus denen sich der Hardwarebedarf ableiten lässt. Lizenz und Deployment-Anleitung stehen nicht im vorliegenden Auszug.

## Was man anwenden kann
1. **Hardwarebedarf vor dem Pilot rechnen.** Laut Safetensors-Metadaten liegen rund 2,72 Billionen Einträge in U8, 57,4 Milliarden in BF16 und 11 Millionen in F32 vor. Daraus ergeben sich rechnerisch etwa 2,84 TB nur für die Gewichte, ohne KV-Cache. Ein Server mit 8 GPUs zu je 141 GB hat rund 1,1 TB. Selbst-Hosting erfordert also einen Verbund aus mehreren Knoten. Das ist eine eigene Ableitung, die Card nennt keine Hardwareanforderungen.
2. **Rechenaufwand und Speicher getrennt bewerten.** Mixture-of-Experts mit 2,8T Gesamtparametern, davon 104B aktiv pro Token (rund 3,7 Prozent). Pro Token rechnet das Modell ungefähr wie ein 100B-Modell, beim Speicher verhält es sich aber wie ein 2,8T-Modell. Für eine Kostenschätzung zählt bei geringer Last vor allem der Speicher, bei hoher Last eher der Durchsatz.
3. **Das ausgelieferte Format ist die Zielquantisierung.** Gewichte in MXFP4, Aktivierungen in MXFP8, mit quantization-aware training trainiert. Eine eigene Nachquantisierung ist damit nicht der erste Schritt. Unklar bleibt, warum der Hub den Tag „8-bit“ führt, während die Card MXFP4-Gewichte nennt. Das sollte man vor der Wahl der Inferenz-Engine klären.
4. **Lizenz vor jedem B2B-Einsatz lesen.** Die Lizenz heißt „other“ (kimi-k3.1-pro). Die Bedingungen stehen in einer separaten LICENSE-Datei. Es handelt sich nicht um Apache-2.0 oder MIT. Kommerzielle Nutzung, EU-Einsatz und Namensnennung lassen sich aus dem Auszug nicht ableiten.
5. **Benchmarks nach Einsatzfall lesen, nicht nach Gesamtsieg.** Stärken laut Tabelle: SWE Marathon (51,7, vorn), OfficeQA Pro v2 (64,4, vorn), Automation Bench-AA (73,3, vorn), HLE-Full mit Tools (70,0, vorn), BrowseComp (92,1, knapp vorn). Schwächen: Program Bench (31,5 gegenüber 65,0 bei Claude Opus 5.5) und Terminal-Bench-Science (38,1 gegenüber 68,1 bei GPT-6 Astra). Wer Dokumenten- und Recherche-Workflows baut, sollte auf die Gruppe Büro und Websuche schauen. Für Programmsynthese ist das Modell laut eigener Tabelle schwächer.
6. **Scores gelten nur für maximalen Reasoning-Aufwand.** Alle Kimi-Werte wurden mit Reasoning-Effort max, temperature 1.0 und top-p 0.95 gemessen. Für niedrigere Stufen, Latenz und Tokenverbrauch nennt die Card keine Zahlen. Im eigenen Pilot sollte man deshalb dieselben Einstellungen nutzen und die Kosten pro Aufgabe selbst messen.
7. **Halluzinationsrate selbst nachprüfen.** Auf dem hauseigenen Kimi Hallu Bench Hard (mit Tools, niedriger ist besser) erreicht Kimi 8,3. Claude Opus 5.5 kommt auf 15,0, Claude Fable 5.1 auf 23,3, GPT-6 Astra auf 5,5. Für Sales-Research und Faktenrecherche ist das die wichtigste Zahl. Sie stammt aber aus einem internen Test und braucht einen eigenen Abgleich mit echten Kundenfragen.
8. **Zwei Zugangswege vergleichen.** Neben den Gewichten bietet Moonshot Kimi-Chat (kimi.ai) und eine API (Quickstart unter platform.kimi.ai) an. Preise und Rate-Limits nennt die Card nicht. Ein API-Test ist der günstigere Weg, um die Qualität zu prüfen, bevor man über Multi-Node-Hardware entscheidet. Für den souveränen Betrieb ist die gehostete API aber kein Ersatz für Selbst-Hosting.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 2,8T / 104B | Gesamtparameter / aktive Parameter pro Token | Herstellerangabe |
| 896 / 16 / 2 | Experten / gewählte Experten pro Token / Shared Experts | Herstellerangabe |
| 93 Layer, 69 KDA + 24 Gated DSA | Schichtaufbau; Gated DSA ersetzt Gated MLA aus K3 | Herstellerangabe |
| Top-K 2048 | ausgewählte Positionen pro Anfrage in den DSA-Layern | Herstellerangabe |
| 1.048.576 Token | Kontextlänge | Herstellerangabe, kein Long-Context-Benchmark im Auszug |
| 401M | Vision-Encoder MoonViT-V2, Modalitäten Text und Bild | Herstellerangabe |
| ca. 2,84 TB | Gewichte auf Platte bzw. im Speicher | eigene Ableitung aus Hub-Metadaten |
| 65,7 / 66,4 | Terminal-Bench 4.0: Kimi / Opus 5.5 | Herstellerangabe |
| 31,5 / 65,0 | Program Bench: Kimi / Opus 5.5 | Herstellerangabe |
| 64,4 / 62,2 | OfficeQA Pro v2: Kimi / Opus 5.5 | Herstellerangabe |
| 73,3 / 69,5 | Automation Bench-AA: Kimi / Opus 5.5 | Herstellerangabe |
| 79,6 / 81,8 | OSWorld V2.1 (Computer Use): Kimi / Opus 5.5 | Herstellerangabe |
| 1678 / 1803 | AA-Briefcase (Elo): Kimi / Opus 5.5 | Herstellerangabe |
| 8,3 / 5,5 / 15,0 | Hallu Bench Hard: Kimi / GPT-6 Astra / Opus 5.5 | interner Benchmark |
| 23,7 | Harvey Legal Agent, Kimi (bester berichteter Wert) | Herstellerangabe |
| 1.787 / 27.926 | Likes / Downloads auf dem Hub beim Abruf | Hub-Metadaten |

## Grenzen und Widerspruch
- **Nur Herstellerzahlen.** Es gibt keine unabhängige Replikation, keine Konfidenzintervalle und keine Kosten pro Aufgabe. Sechs Benchmarks sind ausdrücklich intern: Kimi Code Bench 2.0 und 3.0, Business Operation, DECK-Arena, Design Bench und Hallu Bench.
- **Unklare Vergleichsbasis.** Die Closed-Modelle tragen den Zusatz „max, w/ fallback“, die Kimi-Spalte nicht. Was „fallback“ bedeutet, erklärt die Card nicht. Viele Zellen sind leer, bei BrowseComp fehlen zum Beispiel drei der fünf Vergleichsmodelle.
- **Kein Vergleich mit K3.** Moonshot behauptet substanzielle Verbesserungen bei Coding, 3D-Erstellung, Finanzrecherche und Faktentreue, zeigt aber keine Werte des Vorgängers. Der Gewinn ist nicht nachprüfbar.
- **Gemischtes Bild.** Claude Opus 5.5 liegt bei Terminal-Bench 4.0, Program Bench, APEX-Agents, AA-Briefcase, GDPval-AA und OSWorld vorn. GPT-6 Astra führt bei Terminal-Bench-Science und hat die niedrigste Halluzinationsrate. Bei DeepSWE liegt das Open-Weight-Modell DeepSeek-V4.1-Flash-1017 vor Kimi (77,0 gegenüber 75,5).
- **Unterschiede oft im Rauschbereich.** Bei BrowseComp, BioMysteryBench und den Multimodal-Tests liegen die Abstände häufig unter 2 bis 3 Punkten.
- **Recht schwach abgedeckt.** Beim Harvey Legal Agent erreicht kein gelistetes Modell mehr als 23,7.
- **Fehlende Angaben.** Unterstützte Sprachen fehlen, die Deutschqualität ist nicht belegt. Es gibt keine Inferenz-Engine, keinen Beispielcode, kein Chat-Template und keine Hinweise zum Tool-Calling. Die Abkürzungen KDA und SiTU-GLU werden nicht erklärt. Das Material endet nach der Zeile GDP.pdf ohne Tools.
- **Modellcode.** Der Tag custom_code bedeutet, dass das Modell eigenen Code mitbringt. In abgeschotteten Umgebungen braucht das eine Prüfung.
