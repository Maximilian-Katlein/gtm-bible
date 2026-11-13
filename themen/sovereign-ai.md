# Sovereign AI

Diese Seite sammelt, was Unternehmen beachten müssen, wenn sie KI-Modelle unabhängig von einzelnen Anbietern, Regionen und Vertragsbedingungen betreiben wollen. Sie fasst Belege zu Verfügbarkeit, Hardware- und Compute-Kosten, Lizenzen, Code-Prüfung und politischer Verzerrung offener Modelle zusammen.

Stand: 2026-11-13 · 7 Quellen · 15 Learnings

## Was mehrfach belegt ist

- **Mitgelieferten Modellcode vor dem Einsatz prüfen (2 Quellen).** Kimi K3.1 Pro bringt eigenen Code mit (custom_code), der vor dem Einsatz geprüft werden muss. LFM3-1.7B verlangt beim Laden mit Transformers „trust_remote_code=True,“. Dabei wird Modellcode aus dem Repo ausgeführt. In abgesicherten oder souveränen Umgebungen den Code vorher prüfen oder bei LFM3 auf GGUF, ONNX oder OpenVINO ausweichen. *Bedingung:* Selbst-Hosting in abgeschotteten oder regulierten Umgebungen; bei LFM3 nur die Transformers-Variante. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md)
- **Für deutschsprachigen Einsatz fehlen bei offenen Modellen oft die Belege (2 Quellen).** Die Card von Kimi K3.1 Pro nennt keine unterstützten Sprachen und sagt nichts zur Qualität auf Deutsch. Die Wirkung von Arete-27B ist nur für englischsprachige Prompts gemessen: „Prompts come from English-language government statutes, news and research reports“. Für Deutsch fehlt jeder Beleg, ebenso Werte mit aktiviertem Thinking-Modus. *Bedingung:* Deutschsprachige Anwendungen. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)
- **Agenten-Tools und Anleitungen sparen Datenhoheit aus (2 Quellen).** Das sichtbare AgentRun-README nennt nur OpenRouter, Anthropic und OpenAI als Modellquellen und sagt nichts zu EU-Hosting, Datenschutz oder Open-Weight-Modellen. Der Kurs „Building AI Agents“ leitet E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten über US-Cloud-Modelle (Claude, GPT, Gemini), ohne DSGVO, Auftragsverarbeitung oder lokale Alternativen anzusprechen. Wer souverän betreiben will, muss das vor dem Nachbau selbst klären. *Bedingung:* Teams mit Anforderungen an Datenhoheit, Firmen mit Sitz oder Kunden in der EU. *Beleglage:* Beim Kurs Einschätzung ohne Beleg, bei AgentRun aus dem README abgeleitet. [AgentRun (Show HN)](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md), [Building AI Agents (Kurs)](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)

## Taktiken und Abläufe

### Anbieterauswahl

- **Drei Bausteine als Prüfraster für souveräne KI.** Laut Mistral braucht es eine gesicherte, laufend weiterentwickelte Modellquelle, Datenkontrolle auf dem eigenen Tenant ohne Rückfluss zum Anbieter und eigene Compute-Infrastruktur zur Kostenkontrolle. Zitat: „in sovereignty AI technology you need three things, you need to have a source of model that is secured“ (04:23). *Bedingung:* Enterprise und Public Sector mit KI in Kernprozessen. *Beleglage:* Behauptung ohne Beleg; das Raster stammt von einem Anbieter, der genau diese drei Bausteine verkauft. [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

### Prüfung auf politische Verzerrung

- **Faktentreue und Framing getrennt messen.** Ein Modell kann Fakten gut wiedergeben und trotzdem die Staatsdarstellung übernehmen. Nous Research trennt deshalb: „We separated factual recall, the ability to corroborate verified sources of truth, from framing“. Beispiel GLM 5.3: hoher Faktenwert von 3,10, trotzdem Staatsdarstellung in 15 Prozent der Antworten. *Bedingung:* Teams, die Open-Weight-Modelle auf Bias oder Staatsnähe prüfen. *Beleglage:* Eigene Daten der Autoren. [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

### Finanzierung und Förderung von Rechenzentren

- **Rechenzentren über Kundenzusagen statt über Schulden finanzieren.** Mistral nutzt Umsatz- und Abnahmezusagen von Kunden als Sicherheit. Kapazität vor der Nachfrage aufzubauen lasse sich leicht verkaufen, weil Enterprises selbst GPU-Engpässe haben: „if you're able to front capacity ahead of demand, you get something that is pretty easy to sell“ (18:10). *Bedingung:* Compute-Anbieter mit festen Kundenzusagen. *Beleglage:* Herstellerangabe. [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
- **Staatliche Förderung ohne Marktverzerrung.** Laut Mistral-Chef Mensch helfen schnellere Genehmigungen, staatliche Garantien für Mietverträge über 10 bis 15 Jahre und Ankeraufträge der öffentlichen Hand, vor allem Firmen mit kleiner Bilanz: „state guarantees on leasing data centers... on reserving space for 10 or 15 years, are super useful“ (20:25). *Bedingung:* Europäische Industriepolitik. *Beleglage:* Behauptung ohne Beleg, Forderung eines Begünstigten. [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

## Zahlen und Richtwerte

### Hardwarebedarf beim Selbst-Hosting

- **Kimi K3.1 Pro braucht mehrere Server.** Rechnerisch belegen allein die Gewichte rund 2,84 TB, der KV-Cache kommt noch dazu. Ein Server mit 8 GPUs zu je 141 GB hat zusammen etwa 1,1 TB und reicht deshalb nicht. Ohne API muss das Modell über mehrere Knoten verteilt laufen. In den Safetensors-Metadaten steht: „"total": 2780110363392“. *Bedingung:* Die Zahl ist eine eigene Ableitung aus den Metadaten des Original-Checkpoints und gilt für den souveränen Betrieb ohne API. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)

### Kosten von Compute

- **Energie macht etwa 10 % der Gesamtkosten von Compute aus.** Chippreise und Kapitalkosten dominieren, ein günstiger Strompreis am Standort hat deshalb begrenzte Hebelwirkung: „energy is around 10% of the bill in the total cost of ownership of compute.“ (13:46). *Bedingung:* Planung von KI-Rechenzentren. *Beleglage:* Behauptung ohne Beleg. [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

### Politische Verzerrung offener Modelle

- **Chinesische Modelle rahmen 15 bis 22 Prozent der Antworten propagandistisch, westliche 0,3 bis 0,6 Prozent.** Gemessen an GLM 5.3, DeepSeek V4.1 Flash und Qwen3.8-27B gegenüber Mistral Large 4, Nemotron 3 Ultra und Gemma 4 31B. Tabellenzeile: „GLM 5.3 (thinking off) | 3.10 ± 0.06 | 15%“. *Bedingung:* Eigene Evaluation der Autoren, Vergleichsmodelle bei Temperatur 0,6, chinesische Modelle mit Thinking aus, nur englische Prompts. *Beleglage:* Herstellerangabe. [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

## Werkzeuge

- **Arete-27B ist ein bewusster Perspektivwechsel, keine Neutralität.** Nous Research positioniert das Modell ausdrücklich in Richtung westlicher Werte und begründet das mit Wahlfreiheit für Nutzer offener Modelle: „The users of a model deserve optionality in which values they work with.“ Neue westliche Einseitigkeiten werden nicht gemessen. *Bedingung:* Normative Position; die Messung deckt nur sieben Kategorien ab. *Beleglage:* Behauptung ohne Beleg. [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

## Warnungen und Fehler

### Verfügbarkeit nach Region und Vertrag

- **Die Region oder der Vertrag kann ein Modell ausschließen, auch wenn es fachlich gut ist.** Goldman Sachs nahm Claude im April in Hongkong von seiner internen Plattform, JPMorgan folgte im Juni. ChatGPT und Gemini blieben bei Goldman in Hongkong verfügbar. Laut einem Anthropic-Sprecher war Claude „had never been officially supported in Hong Kong“. *Bedingung:* Das betrifft multinationale Unternehmen mit Standorten außerhalb der Regionen, die ein Anbieter offiziell unterstützt. *Beleglage:* Die Quelle stellt das nur als Behauptung dar und belegt es nicht. [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)

### Lücken in Model Cards

- **Bei Kimi K3.1 Pro bleibt vieles offen, das man für den Betrieb selbst klären muss.** Die Card nennt keine unterstützten Sprachen, keine Inferenz-Engine und keine Hardwareanforderungen. Angegeben ist nur „library_name: transformers“. Zum mitgelieferten Code siehe „Was mehrfach belegt ist“. Wer das Modell souverän in Europa betreiben will, muss Sprache, Laufzeitumgebung und Code-Prüfung selbst klären. *Bedingung:* Das gilt für Selbst-Hosting in abgeschotteten oder regulierten Umgebungen. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)

### Lizenzen

- **LFM3-1.7B steht unter einer eigenen Lizenz.** Die LFM Open License v1.0 ist keine Standardlizenz wie Apache 2.0 oder MIT. Die Card nennt keine Bedingungen zu kommerzieller Nutzung oder EU. Vor dem Einsatz den LICENSE-Text im Repo prüfen. *Bedingung:* Kommerzielle und Sovereign-AI-Setups. [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md)

## Offene Fragen

- **Mit welcher Genauigkeit wurden die 2,84 TB gerechnet?** Der Wert in den Metadaten (2.780.110.363.392) ist vermutlich die Zahl der Parameter. Wie viel Speicher die Gewichte brauchen, hängt von den angenommenen Datentypen ab. Mit quantisierten Gewichten kann der Bedarf deutlich anders ausfallen. Das Learning ist als Herstellerangabe eingestuft, die Rechnung selbst ist aber eine eigene Ableitung. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Wie gut ist Kimi K3.1 Pro auf Deutsch?** Die Card sagt dazu nichts, eigene Tests stehen noch aus. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Wurde Claude ganz entfernt oder nur Claude Code, und in welchem Jahr?** Der Titel der Quelle spricht von Claude Code, das Learning von Claude. Die Monate April und Juni stehen ohne Jahr. [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- **Wie verhalten sich Arete-27B und die Vergleichsmodelle auf Deutsch und mit Thinking-Modus?** Gemessen ist nur Englisch, die chinesischen Modelle nur mit Thinking aus. [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)
- **Was erlaubt die LFM Open License v1.0 kommerziell und in der EU?** Die Card schweigt dazu, der LICENSE-Text ist noch nicht ausgewertet. [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md)
