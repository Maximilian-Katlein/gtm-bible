# Show HN: TrnRT, eine Open-Source-Inferenz-Engine für LLMs auf AWS Trainium

> **Quelle:** [Show HN: TrnRT (open-source LLM inference engine for AWS Trainium)](https://github.com/RunanywhereAI/trnrt) · RunAnywhere (GitHub: RunanywhereAI/trnrt), Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50533270) · Diskussion mit README · 2026-11-18
> **Sprecher verkauft:** Open-Source-Engine unter Apache 2.0, kein kommerzielles Produkt im Material genannt · **Zielmarkt der Aussagen:** Teams, die offene LLMs für Coding-Agenten mit sehr langem Kontext auf AWS Trainium2 statt auf Nvidia-GPUs betreiben wollen · **Beweislage:** nur Messungen der Autoren selbst, mit einem früheren Build, ohne unabhängige Reproduktion und ohne GPU-Vergleich.

## Worum es geht
Kann man ein großes offenes Modell mit 1M-Token-Kontext wirtschaftlich auf einer einzelnen AWS-Trainium2-Instanz für Coding-Agenten betreiben? TrnRT ist ein unabhängiges Projekt von RunAnywhere, nicht von AWS unterstützt. Es richtet sich an Infrastruktur-Teams, die eine Alternative zum GPU-Stack prüfen.

## Was man anwenden kann
1. **Voraussetzungen prüfen, bevor man plant.** Unterstützt ist genau ein Modell, GLM-5.3-Flash von Z.ai (320B Mixture-of-Experts, 18B aktiv, FP8, 1M Kontext), und genau eine Instanz, trn2.48xlarge (16 Chips). Weitere Modelle sind nur angekündigt. Wer ein anderes Modell oder eine andere Trainium- oder Inferentia-Instanz braucht, kann TrnRT derzeit nicht nutzen.
2. **Kompilieren vom Serven trennen.** Alle Graphen werden auf einem beliebigen x86_64-Host ohne NeuronCore gebaut, die Trainium-Box lädt sie nur. Der Compile-Schritt dauert laut README Stunden. So bezahlt man die teure Instanz nicht für Compile-Zeit. Kopiert werden zwei Verzeichnisse: der Cache (nach /cache) und der NKI-Zwischencache (nach /var/tmp/nki-intermediate-cache).
3. **Quickstart in vier Schritten.** Docker-Image bauen (Neuron SDK 2.32, neuronx-cc 2.27, Python 3.13). Compile-Cache mit `trnrt compile` auf dem CPU-Host erzeugen. Auf der trn2.48xlarge die Gewichte per `hf download` laden, Caches kopieren und per `docker run` auf Port 8000 serven. Dann mit jedem OpenAI-Client aufrufen.
4. **Modellrevision pinnen.** Der Quickstart fixiert eine bestimmte Hugging-Face-Revision beim Kompilieren und beim Download. Daraus folgt (eigene Schlussfolgerung): Ein Modellupdate verlangt einen neuen Compile-Lauf von mehreren Stunden. Das gehört in die Release-Planung.
5. **Session-ID mitschicken.** Pro Box laufen zwei Engines mit einem sitzungsfesten Router davor. Der Client übergibt in `extra_body` eine `session_id`, damit eine Konversation auf dem Prefix-Cache derselben Engine bleibt. Ohne sie verfehlen Folgeanfragen vermutlich den Cache. Relevant für Agenten und Mehrfach-Turn-Dialoge.
6. **Batchgröße bewusst wählen.** Dokumentiert sind Batch 4, 8 und 12 (Standard). Größerer Batch senkt die Kosten pro Token und die Wartezeit bis zum ersten Token in der gemessenen Last, halbiert aber die Generierungsgeschwindigkeit pro Nutzer. Die Wahl hängt davon ab, ob ein Mensch live mitliest oder ein Agent im Hintergrund arbeitet.
7. **API selbst absichern.** Die OpenAI-kompatible Schnittstelle deckt Chat, Completions, Streaming, Tool Calls und Reasoning-Ausgabe ab. Im Beispiel ist der API-Key beliebig, es gibt keine Authentifizierung. Wer die Box im Netz betreibt, braucht eine eigene Absicherung davor.
8. **Prefix-Cache für Agenten-Workloads nutzen.** Der Cache ist ein Radix-Baum über FP8-KV-Pages mit einer zusätzlichen Stufe im Host-Speicher. Das zahlt sich bei langen, wiederkehrenden Präfixen aus, typisch für Coding-Agenten, die immer wieder dasselbe Repository im Kontext haben.

## Zahlen und ihre Herkunft
Alle Benchmarkwerte: SemiAnalysis AgentX (Wiedergabe echter Coding-Agent-Sitzungen), eine trn2.48xlarge, 1M Kontext, 32 gleichzeitige Agenten, je Messpunkt eine Stunde, gemessen mit einem früheren Build.

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 28,9 Requests/min, 3,57 Mio. Tokens/min | Batch 12, Gesamtdurchsatz der Box | Herstellerangabe |
| 22,3 Tokens/s pro Nutzer (p50) | Batch 12, Decode-Geschwindigkeit | Herstellerangabe |
| 6,53 s | Batch 12, Zeit bis zum ersten Token bei Cache-Treffer (p50) | Herstellerangabe |
| 0,040 US-Dollar pro Mio. Tokens | Batch 12, Spot-Preis 8,60 US-Dollar/h, us-east-2, 3. Nov. 2026 | Herstellerangabe, nachgerechnet konsistent |
| 0,167 US-Dollar pro Mio. Tokens | Batch 12, Capacity Block zu 35,76 US-Dollar/h | Herstellerangabe |
| 25,2 Req/min, 29,4 Tok/s, 28,82 s, 0,047 US-Dollar | Batch 8, gleiche Reihenfolge | Herstellerangabe |
| 19,3 Req/min, 46,6 Tok/s, 76,73 s, 0,061 US-Dollar | Batch 4, gleiche Reihenfolge | Herstellerangabe |
| rund 50 % mehr Requests, rund 34 % niedrigere Kosten, rund 52 % weniger Tokens/s pro Nutzer | Wechsel von Batch 4 auf Batch 12 | eigene Rechnung aus Herstellerzahlen |
| über 99 % Eingabe-Tokens | Anteil am gezählten Durchsatz bei Batch 12, falls der Batch pro Engine gilt | eigene Rechnung unter Annahme |
| 157 Graphen, 32 Ranks, 384 von 384 Requests byte-identisch | Prüfung des aktuellen Repos gegen den gemessenen Build, nur Batch 12 | Herstellerangabe |

Wichtig für den Vergleich: „Tokens“ zählt Eingabe, gecachte Eingabe und Ausgabe zusammen. Der Preis pro Million Tokens ist deshalb nicht mit Output-Preisen von API-Anbietern vergleichbar. Grob gerechnet liegt die reine Ausgabe bei Batch 12 bei höchstens etwa 535 Tokens/s für die ganze Box, der Rest des gezählten Durchsatzes ist überwiegend gecachte Eingabe.

## Wortlaute
- „Decode is not limited by memory bandwidth here; small instructions, kernel boundaries and exposed collectives dominate it.“ Die zentrale technische These hinter den Megakernels. Im README ohne Messung.
- „Every graph is built on a CPU host; the serving box loads them and compiles nothing by default.“ Das Betriebsprinzip der Offline-Kompilierung.
- „Tokens count input (cached input included) and output.“ Die Fußnote, die bestimmt, wie man alle Durchsatz- und Kostenzahlen lesen muss.

## Grenzen und Widerspruch
- **Keine Vergleichswerte.** Kein Vergleich mit SGLang, vLLM, Nvidia oder AMD. In der Diskussion fragen badmonster0 nach SGLang und kevo1ution nach Kosten pro Token gegenüber Nvidia und AMD. Antworten liegen im Material nicht vor.
- **Ungewohnte Metrik.** bookernath hält „Tokens pro Minute“ für schwer vergleichbar und wünscht Tokens pro Sekunde. Der Einwand trifft zu, zumal gecachte Eingabe mitgezählt wird.
- **Latenz.** Selbst mit Cache-Treffer liegt die Zeit bis zum ersten Token zwischen 6,5 und 77 Sekunden. Das passt zu Agenten und Batch-Jobs, kaum zu interaktivem Chat (eigene Einordnung). Kaltstart-Werte stehen nur in docs/RESULTS.md, das nicht vorliegt.
- **Früherer Build.** Die Zahlen stammen nicht vom aktuellen Repo-Stand. Die Äquivalenzprüfung deckt nur Batch 12 ab.
- **Spot-Preise.** Die günstigste Zahl setzt Spot-Kapazität voraus, die schwankt und nicht garantiert ist. Planbar kostet derselbe Betrieb rund das 4,2-Fache.
- **Qualität und Lizenz.** Keine Genauigkeitsmessung des FP8-Betriebs gegenüber einer Referenz. Die Lizenz von GLM-5.3-Flash nennt das Material nicht, Apache 2.0 gilt nur für die Engine.
- **Souveränität.** Engine und Modell sind offen, die Hardware bleibt an AWS gebunden. Preise sind nur für us-east-2 angegeben. Ob trn2.48xlarge in EU-Regionen verfügbar ist, steht nicht im Material.
- **Ökosystem.** coredog64 wundert sich, wie dünn das Trainium-Ökosystem trotz Amazons Größe ist, und sieht einen nahtlosen Nvidia-Ersatz als strategischen Hebel. Das ist Meinung.
- **Unerklärte Begriffe.** KDA, DSA, mHC, SBUF und LNC werden im README nicht erklärt. Es gibt keine Kundenfälle und keine Betriebsberichte.
