# Sovereign AI

Diese Seite sammelt, was Unternehmen beachten müssen, wenn sie KI-Modelle unabhängig von einzelnen Anbietern, Regionen und Vertragsbedingungen betreiben wollen. Sie fasst Belege zu Verfügbarkeit, Hardware- und Compute-Kosten, lokalem und Offline-Betrieb, Lizenzen und Offenheit, Code-Prüfung und politischer Verzerrung offener Modelle zusammen.

Stand: 2026-11-14 · 9 Quellen · 20 Learnings

## Was mehrfach belegt ist

- **Lizenz offener Modelle vor kommerziellem Einsatz selbst prüfen (3 Quellen).**
  - LFM3-1.7B steht unter der LFM Open License v1.0. Das ist keine Standardlizenz wie Apache 2.0 oder MIT, und die Card nennt keine Bedingungen zu kommerzieller Nutzung oder EU.
  - Edge0-145B nennt nach dem Material überhaupt keine Lizenz, die kommerzielle Nutzung ist damit offen.
  - Bei Mirage steht im Lizenzfeld „license: apache-2.0“, was kommerzielle Nutzung grundsätzlich erlaubt. Die Runtime liegt aber in einem separaten Repo (Cactus-Compute/cactus). Deren Lizenz und den Lizenztext im Modell-Repo getrennt prüfen.
  - In allen drei Fällen gilt: Vor dem Einsatz den LICENSE-Text im Repo lesen, bei Mirage zusätzlich den der Runtime.
  - *Bedingung:* Kommerzielle, souveräne und Sovereign-AI-Setups.
  - *Beleglage:* Bei LFM3 und Mirage Herstellerangaben, bei Edge0 Behauptung ohne Beleg.
  - [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md), [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
- **Trainingsdaten und Datenherkunft bleiben bei offenen Modellen unbelegt (2 Quellen).**
  - Edge0 veröffentlicht nach dem Material nur Gewichte, Framework und Tools, aber keine Trainingsdaten und keinen Trainingscode.
  - Die Mirage-Card enthält keine Angaben zu Trainingsdaten, Datenherkunft oder EU-Konformität.
  - Für Sovereign-AI-Anforderungen ist ein solches Modell auf Basis der Card allein nicht bewertbar.
  - *Bedingung:* Öffentliche Hand, regulierte Branchen, EU-Beschaffung, kommerzielle Umgebungen.
  - *Beleglage:* In beiden Quellen Behauptung ohne Beleg.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
- **Mitgelieferten Modellcode vor dem Einsatz prüfen (2 Quellen).**
  - Kimi K3.1 Pro bringt eigenen Code mit (custom_code), der vor dem Einsatz geprüft werden muss.
  - LFM3-1.7B verlangt beim Laden mit Transformers „trust_remote_code=True,“. Dabei wird Modellcode aus dem Repo ausgeführt.
  - In abgesicherten oder souveränen Umgebungen den Code vorher prüfen oder bei LFM3 auf GGUF, ONNX oder OpenVINO ausweichen.
  - *Bedingung:* Selbst-Hosting in abgeschotteten oder regulierten Umgebungen. Bei LFM3 gilt das nur für die Transformers-Variante.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md)
- **Für deutschsprachigen Einsatz fehlen bei offenen Modellen oft die Belege (2 Quellen).**
  - Die Card von Kimi K3.1 Pro nennt keine unterstützten Sprachen und sagt nichts zur Qualität auf Deutsch.
  - Die Wirkung von Arete-27B ist nur für englischsprachige Prompts gemessen: „Prompts come from English-language government statutes, news and research reports“.
  - Für Deutsch fehlt jeder Beleg, ebenso Werte mit aktiviertem Thinking-Modus.
  - *Bedingung:* Deutschsprachige Anwendungen.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)
- **Agenten-Tools und Anleitungen sparen Datenhoheit aus (2 Quellen).**
  - Das sichtbare AgentRun-README nennt nur OpenRouter, Anthropic und OpenAI als Modellquellen. Zu EU-Hosting, Datenschutz oder Open-Weight-Modellen sagt es nichts.
  - Der Kurs „Building AI Agents“ leitet E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten über US-Cloud-Modelle (Claude, GPT, Gemini). DSGVO, Auftragsverarbeitung oder lokale Alternativen spricht er nicht an.
  - Wer souverän betreiben will, muss das vor dem Nachbau selbst klären.
  - *Bedingung:* Teams mit Anforderungen an Datenhoheit, Firmen mit Sitz oder Kunden in der EU.
  - *Beleglage:* Beim Kurs Einschätzung ohne Beleg, bei AgentRun aus dem README abgeleitet.
  - [AgentRun (Show HN)](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md), [Building AI Agents (Kurs)](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)

## Taktiken und Abläufe

### Anbieterauswahl

- **Drei Bausteine als Prüfraster für souveräne KI.**
  - Laut Mistral braucht es drei Dinge:
    - eine gesicherte, laufend weiterentwickelte Modellquelle,
    - Datenkontrolle auf dem eigenen Tenant ohne Rückfluss zum Anbieter,
    - eigene Compute-Infrastruktur zur Kostenkontrolle.
  - Zitat: „in sovereignty AI technology you need three things, you need to have a source of model that is secured“ (04:23).
  - *Bedingung:* Enterprise und Public Sector mit KI in Kernprozessen.
  - *Beleglage:* Behauptung ohne Beleg. Das Raster stammt von einem Anbieter, der genau diese drei Bausteine verkauft.
  - [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

### Lokale Inferenz

- **Lokale Inferenz spart API-Gebühren, ist aber nicht kostenlos.**
  - Lokaler Betrieb vermeidet Token- und API-Gebühren, hält Daten auf dem Rechner und erlaubt Offline-Betrieb.
  - Hardware und Strom kosten weiter Geld: „Hardware and electricity still cost money.“
  - Eine Gesamtkostenrechnung liefert der Hersteller nicht. Zum Anteil der Energie an den Compute-Kosten siehe „Zahlen und Richtwerte“.
  - *Bedingung:* Ein Kostenvorteil entsteht nur, wenn passende Hardware bereits vorhanden ist.
  - *Beleglage:* Herstellerangabe.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md)

### Prüfung auf politische Verzerrung

- **Faktentreue und Framing getrennt messen.**
  - Ein Modell kann Fakten gut wiedergeben und trotzdem die Staatsdarstellung übernehmen.
  - Nous Research trennt deshalb: „We separated factual recall, the ability to corroborate verified sources of truth, from framing“.
  - Beispiel GLM 5.3: Es erreicht einen hohen Faktenwert von 3,10 und übernimmt trotzdem in 15 Prozent der Antworten die Staatsdarstellung.
  - *Bedingung:* Teams, die Open-Weight-Modelle auf Bias oder Staatsnähe prüfen.
  - *Beleglage:* Eigene Daten der Autoren.
  - [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

### Finanzierung und Förderung von Rechenzentren

- **Rechenzentren über Kundenzusagen statt über Schulden finanzieren.**
  - Mistral nutzt Umsatz- und Abnahmezusagen von Kunden als Sicherheit.
  - Kapazität vor der Nachfrage aufzubauen lasse sich leicht verkaufen, weil Enterprises selbst GPU-Engpässe haben: „if you're able to front capacity ahead of demand, you get something that is pretty easy to sell“ (18:10).
  - *Bedingung:* Compute-Anbieter mit festen Kundenzusagen.
  - *Beleglage:* Herstellerangabe.
  - [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
- **Staatliche Förderung ohne Marktverzerrung.**
  - Laut Mistral-Chef Mensch helfen drei Maßnahmen, vor allem Firmen mit kleiner Bilanz:
    - schnellere Genehmigungen,
    - staatliche Garantien für Mietverträge über 10 bis 15 Jahre,
    - Ankeraufträge der öffentlichen Hand.
  - Zitat: „state guarantees on leasing data centers... on reserving space for 10 or 15 years, are super useful“ (20:25).
  - *Bedingung:* Europäische Industriepolitik.
  - *Beleglage:* Behauptung ohne Beleg, Forderung eines Begünstigten.
  - [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

## Zahlen und Richtwerte

### Hardwarebedarf beim Selbst-Hosting

- **Kimi K3.1 Pro braucht mehrere Server.**
  - Rechnerisch belegen allein die Gewichte rund 2,84 TB, der KV-Cache kommt noch dazu.
  - Ein Server mit 8 GPUs zu je 141 GB hat zusammen etwa 1,1 TB und reicht deshalb nicht. Ohne API muss das Modell über mehrere Knoten verteilt laufen.
  - In den Safetensors-Metadaten steht: „"total": 2780110363392“.
  - *Bedingung:* Die Zahl ist eine eigene Ableitung aus den Metadaten des Original-Checkpoints. Sie gilt für den souveränen Betrieb ohne API.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)

### Kosten von Compute

- **Energie macht etwa 10 % der Gesamtkosten von Compute aus.**
  - Chippreise und Kapitalkosten dominieren. Ein günstiger Strompreis am Standort hat deshalb begrenzte Hebelwirkung.
  - Zitat: „energy is around 10% of the bill in the total cost of ownership of compute.“ (13:46).
  - *Bedingung:* Planung von KI-Rechenzentren.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

### Politische Verzerrung offener Modelle

- **Chinesische Modelle rahmen 15 bis 22 Prozent der Antworten propagandistisch, westliche 0,3 bis 0,6 Prozent.**
  - Gemessen wurden GLM 5.3, DeepSeek V4.1 Flash und Qwen3.8-27B im Vergleich zu Mistral Large 4, Nemotron 3 Ultra und Gemma 4 31B.
  - Tabellenzeile: „GLM 5.3 (thinking off) | 3.10 ± 0.06 | 15%“.
  - *Bedingung:* Eigene Evaluation der Autoren mit Vergleichsmodellen bei Temperatur 0,6, chinesischen Modellen mit Thinking aus und nur englischen Prompts.
  - *Beleglage:* Herstellerangabe.
  - [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

## Werkzeuge

- **Arete-27B ist ein bewusster Perspektivwechsel, keine Neutralität.**
  - Nous Research positioniert das Modell ausdrücklich in Richtung westlicher Werte.
  - Die Begründung ist Wahlfreiheit für Nutzer offener Modelle: „The users of a model deserve optionality in which values they work with.“
  - Neue westliche Einseitigkeiten werden nicht gemessen.
  - *Bedingung:* Normative Position. Die Messung deckt nur sieben Kategorien ab.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

## Warnungen und Fehler

### Verfügbarkeit nach Region und Vertrag

- **Die Region oder der Vertrag kann ein Modell ausschließen, auch wenn es fachlich gut ist.**
  - Goldman Sachs nahm Claude im April in Hongkong von seiner internen Plattform, JPMorgan folgte im Juni.
  - ChatGPT und Gemini blieben bei Goldman in Hongkong verfügbar.
  - Laut einem Anthropic-Sprecher war Claude „had never been officially supported in Hong Kong“.
  - *Bedingung:* Das betrifft multinationale Unternehmen mit Standorten außerhalb der Regionen, die ein Anbieter offiziell unterstützt.
  - *Beleglage:* Die Quelle stellt das nur als Behauptung dar und belegt es nicht.
  - [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)

### Offline- und Air-Gap-Betrieb

- **Mirage lädt Engine und Gewichte beim ersten Aufruf aus dem Netz.**
  - Das Paket cactus-compute lädt beim ersten Aufruf automatisch nach: „The package downloads and caches the engine and weights on first use.“
  - Für Air-Gap- oder souveräne Umgebungen müssen Engine und Gewichte vorab bezogen werden.
  - Den Offline-Betrieb muss man selbst verifizieren, die Card beschreibt ihn nicht.
  - Zur Prüfung von mitgeliefertem Code siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Abgeschottete, regulierte oder souveräne Infrastruktur.
  - *Beleglage:* Herstellerangabe.
  - [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)

### Lücken in Model Cards

- **Bei Kimi K3.1 Pro bleibt vieles offen, das man für den Betrieb selbst klären muss.**
  - Die Card nennt keine unterstützten Sprachen, keine Inferenz-Engine und keine Hardwareanforderungen. Angegeben ist nur „library_name: transformers“.
  - Zum mitgelieferten Code siehe „Was mehrfach belegt ist“.
  - Wer das Modell souverän in Europa betreiben will, muss Sprache, Laufzeitumgebung und Code-Prüfung selbst klären.
  - *Bedingung:* Selbst-Hosting in abgeschotteten oder regulierten Umgebungen.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)

### Lizenzen und Offenheit

- **„Open Source“ heißt bei Edge0 nur offene Gewichte.**
  - Edge0 nennt das Modell Open Source. Nach dem Material sind aber nur Gewichte, Framework und Tools veröffentlicht.
  - Zitat: „This is not open source, this is open weights“.
  - Zu fehlender Lizenz und fehlenden Trainingsdaten siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Vor Einsatz in souveränen oder kommerziellen Umgebungen die Lizenz prüfen.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md)

## Offene Fragen

- **Mit welcher Genauigkeit wurden die 2,84 TB gerechnet?**
  - Der Wert in den Metadaten (2.780.110.363.392) ist vermutlich die Zahl der Parameter.
  - Wie viel Speicher die Gewichte brauchen, hängt von den angenommenen Datentypen ab. Mit quantisierten Gewichten kann der Bedarf deutlich anders ausfallen.
  - Das Learning ist als Herstellerangabe eingestuft, die Rechnung selbst ist aber eine eigene Ableitung.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Wie gut ist Kimi K3.1 Pro auf Deutsch?**
  - Die Card sagt dazu nichts, eigene Tests stehen noch aus.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Wurde Claude ganz entfernt oder nur Claude Code, und in welchem Jahr?**
  - Der Titel der Quelle spricht von Claude Code, das Learning von Claude.
  - Die Monate April und Juni stehen ohne Jahr.
  - [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- **Wie verhalten sich Arete-27B und die Vergleichsmodelle auf Deutsch und mit Thinking-Modus?**
  - Gemessen ist nur Englisch, die chinesischen Modelle nur mit Thinking aus.
  - [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)
- **Was erlaubt die LFM Open License v1.0 kommerziell und in der EU?**
  - Die Card schweigt dazu, der LICENSE-Text ist noch nicht ausgewertet.
  - [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md)
- **Unter welcher Lizenz stehen Edge0-145B und die Cactus-Runtime?**
  - Edge0 nennt keine Lizenz.
  - Bei Mirage ist nur das Lizenzfeld des Modells bekannt, nicht die Lizenz des separaten Runtime-Repos.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
- **Ab wann rechnet sich lokale Inferenz gegenüber API-Gebühren?**
  - Edge0 liefert keine Gesamtkostenrechnung für Hardware und Strom.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md)
- **Läuft Mirage nach dem Vorab-Download vollständig offline?**
  - Die Card beschreibt keinen Offline-Betrieb, ein eigener Test steht aus.
  - [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
