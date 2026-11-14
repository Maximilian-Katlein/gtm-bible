# Sovereign AI

Diese Seite sammelt, was Unternehmen beachten müssen, wenn sie KI-Modelle unabhängig von einzelnen Anbietern, Regionen und Vertragsbedingungen betreiben wollen. Sie fasst Belege zu Verfügbarkeit, Hardware- und Compute-Kosten, lokalem und Offline-Betrieb, Lizenzen und Offenheit, Code-Prüfung, Cloud-Bindung von Agenten-Tools und politischer Verzerrung offener Modelle zusammen.

Stand: 2026-11-14 · 15 Quellen · 33 Learnings

## Was mehrfach belegt ist

- **Lizenz offener Modelle vor kommerziellem Einsatz selbst prüfen (7 Quellen).**
  - LFM3-1.7B steht unter der LFM Open License v1.0. Das ist keine Standardlizenz wie Apache 2.0 oder MIT, und die Card nennt keine Bedingungen zu kommerzieller Nutzung oder EU.
  - Edge0-145B nennt nach dem Material überhaupt keine Lizenz, die kommerzielle Nutzung ist damit offen.
  - Bei Mirage steht im Lizenzfeld „license: apache-2.0“, was kommerzielle Nutzung grundsätzlich erlaubt. Die Runtime liegt aber in einem separaten Repo (Cactus-Compute/cactus). Deren Lizenz und den Lizenztext im Modell-Repo getrennt prüfen.
  - Die Unsloth-Seite zu Qwen3.8-27B nennt weder Lizenz noch Bedingungen für kommerzielle Nutzung. Das muss man an anderer Stelle prüfen.
  - Das DSpine-Draft-Modell für Qwen3.8-27B steht unter Apache 2.0 („license: apache-2.0“), ohne zusätzliche Einschränkungen zu kommerzieller Nutzung oder EU. Für den Betrieb zählt aber auch die Lizenz von Qwen3.8-27B, die diese Karte nicht nennt.
  - Inkling 2 Small steht unter Apache 2.0. Die Karte verlinkt daneben eine separate Acceptable Use Policy, ohne Inhalt oder Verhältnis zur Lizenz zu erklären.
  - LongCat-2.5 steht unter MIT-Lizenz ohne Einschränkung nach Branche oder Region, also ohne EU-Ausschluss. Marken und Patente sind ausgenommen: „This license does not grant any rights to use Meituan trademarks or patents.“ Eine Patentlizenz wie bei Apache 2.0 fehlt, das sollte rechtlich geprüft werden. Diese Bewertung ist eine Einordnung, kein Teil der Karte.
  - In allen Fällen gilt: Vor dem Einsatz den LICENSE-Text im Repo lesen. Zusätzlich bei Mirage die Lizenz der Runtime, bei DSpine die des Basismodells, bei Inkling die Acceptable Use Policy.
  - *Bedingung:* Kommerzielle, souveräne und Sovereign-AI-Setups, insbesondere in der EU. Bei Inkling alle, die das Modell in Produkten einsetzen oder weitergeben.
  - *Beleglage:* Bei LFM3, Mirage, DSpine und LongCat Herstellerangaben, bei Edge0, Unsloth und Inkling Behauptung ohne Beleg.
  - [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md), [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md), [Unsloth Qwen3.8-27B](../quellen/2026/11/2026-11-14-unsloth-qwen3-8-27b-quantizations-dynamic-v3-1-update.md), [DSpine for Qwen3.8-27B](../quellen/2026/11/2026-11-14-tencent-qwen3-8-27b-dspine-b16-dspine-for-qwen3-8-27b.md), [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md), [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md)
- **Trainingsdaten, Datenherkunft und Evaluierung bleiben bei offenen Modellen unbelegt (4 Quellen).**
  - Edge0 veröffentlicht nach dem Material nur Gewichte, Framework und Tools, aber keine Trainingsdaten und keinen Trainingscode.
  - Die Mirage-Card enthält keine Angaben zu Trainingsdaten, Datenherkunft oder EU-Konformität.
  - Die Card von Inkling 2 Small nennt keine Datenmenge, keinen Wissensstichtag, keinen Rechenaufwand und keine Sicherheitsevaluierung. Datenquellen stehen nur grob da (öffentlich, zugekauft, intern, synthetisch), zur Aufbereitung heißt es nur: „may include deduplication and filtering to remove junk or other low-quality data“.
  - Die LongCat-2.5-Card enthält keine Angaben zu Trainingsdaten, Datenrechten, Safety-Evaluation oder EU-Regulierung. Datenschutz, Privatsphäre und Inhaltssicherheit liegen ausdrücklich beim Betreiber.
  - Für Sovereign-AI-Anforderungen und Dokumentationspflichten etwa nach AI Act ist ein solches Modell auf Basis der Card allein nicht bewertbar.
  - *Bedingung:* Öffentliche Hand, regulierte Branchen, EU-Beschaffung, kommerzielle Umgebungen, Compliance-Dokumentation.
  - *Beleglage:* Bei Edge0 und Mirage Behauptung ohne Beleg, bei Inkling und LongCat Herstellerangabe.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md), [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md), [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md)
- **Mitgelieferten Modellcode vor dem Einsatz prüfen (3 Quellen).**
  - Kimi K3.1 Pro bringt eigenen Code mit (custom_code), der vor dem Einsatz geprüft werden muss.
  - LFM3-1.7B verlangt beim Laden mit Transformers „trust_remote_code=True,“. Dabei wird Modellcode aus dem Repo ausgeführt.
  - Der dokumentierte Startbefehl von DSpine für Qwen3.8-27B setzt ebenfalls „--trust-remote-code“ und führt damit Code aus dem Repository aus.
  - In abgesicherten oder souveränen Umgebungen den Code vorher prüfen und eine feste Version pinnen. Bei LFM3 kann man auf GGUF, ONNX oder OpenVINO ausweichen.
  - *Bedingung:* Selbst-Hosting in abgeschotteten, On-Premise- oder regulierten Umgebungen. Bei LFM3 gilt das nur für die Transformers-Variante.
  - *Beleglage:* Bei DSpine Herstellerangabe.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md), [DSpine for Qwen3.8-27B](../quellen/2026/11/2026-11-14-tencent-qwen3-8-27b-dspine-b16-dspine-for-qwen3-8-27b.md)
- **Eigener Betrieb hängt an großer oder spezieller Hardware (3 Quellen).**
  - Kimi K3.1 Pro: Rechnerisch belegen allein die Gewichte rund 2,84 TB, der KV-Cache kommt noch dazu. Ein Server mit 8 GPUs zu je 141 GB hat zusammen etwa 1,1 TB und reicht deshalb nicht. Ohne API muss das Modell über mehrere Knoten verteilt laufen. In den Safetensors-Metadaten steht: „"total": 2780110363392“.
  - DeepSeek Ultrafast: Der Selbstbetrieb der Engine setzt 4 bis 8 Blackwell-Rechenzentrums-GPUs voraus. Die HN-Diskussion spottet: „I'll just go get my 8 x B300 (TP8) from the shed and start this up real quick“. Für kleine Teams bleibt praktisch nur die gehostete Variante.
  - LongCat-2.5 dokumentiert Deployment nur für NPU-Plattformen über einen Branch von SGLang-FluentLLM: „LongCat-2.5 can be deployed on NPU platforms.“ Eine Anleitung für NVIDIA-GPUs, vLLM, llama.cpp oder GGUF fehlt. Die beworbenen Effizienzvorteile hängen an inländischen Beschleunigern des Herstellers, deren Chiphersteller nicht genannt wird.
  - Offene Gewichte heißen deshalb nicht souveräner Betrieb. Eigene Kontrolle über die Inferenz ist an große Hardware-Budgets oder an Portierungsaufwand gebunden.
  - *Bedingung:* Kimi: souveräner Betrieb ohne API, die Zahl ist eine eigene Ableitung aus den Metadaten des Original-Checkpoints. DeepSeek: Einzelpersonen und kleine Teams ohne eigenen GPU-Cluster. LongCat: Betreiber in der EU mit GPU-Infrastruktur, die die Portierung selbst leisten müssten.
  - *Beleglage:* Bei Kimi eigene Ableitung, bei DeepSeek Anekdote, bei LongCat Herstellerangabe.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [DeepSeek Ultrafast](../quellen/2026/11/2026-11-14-deepseek-ultrafast.md), [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md)
- **Für deutschsprachigen Einsatz fehlen bei offenen Modellen oft die Belege (3 Quellen).**
  - Die Card von Kimi K3.1 Pro nennt keine unterstützten Sprachen und sagt nichts zur Qualität auf Deutsch.
  - Die Unsloth-Seite zu Qwen3.8-27B nennt ebenfalls keine unterstützten Sprachen.
  - Die Wirkung von Arete-27B ist nur für englischsprachige Prompts gemessen: „Prompts come from English-language government statutes, news and research reports“.
  - Für Deutsch fehlt jeder Beleg, bei Arete ebenso Werte mit aktiviertem Thinking-Modus.
  - *Bedingung:* Deutschsprachige Anwendungen, produktiver Einsatz selbst gehosteter Modelle.
  - *Beleglage:* Bei Unsloth Behauptung ohne Beleg.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [Unsloth Qwen3.8-27B](../quellen/2026/11/2026-11-14-unsloth-qwen3-8-27b-quantizations-dynamic-v3-1-update.md), [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)
- **Agenten-Tools und Anleitungen setzen Anbieter-Clouds voraus und sparen Datenhoheit aus (3 Quellen).**
  - Das sichtbare AgentRun-README nennt nur OpenRouter, Anthropic und OpenAI als Modellquellen. Zu EU-Hosting, Datenschutz oder Open-Weight-Modellen sagt es nichts.
  - Der Kurs „Building AI Agents“ leitet E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten über US-Cloud-Modelle (Claude, GPT, Gemini). DSGVO, Auftragsverarbeitung oder lokale Alternativen spricht er nicht an.
  - Threads in Claude Code Projects laufen derzeit nur in der Anthropic Cloud. Lokale Ausführung ist ohne Datum angekündigt: „Threads run in the cloud today; running on your machine alongside your local tools and code and behind your network is coming very soon.“ Für Organisationen mit Vorgaben zur Datenhaltung ist das Produkt vorerst ungeeignet.
  - Wer souverän betreiben will, muss das vor dem Nachbau oder der Einführung selbst klären. Zur selbst gehosteten Variante von Anthropic siehe „Werkzeuge“, zum Lock-in siehe „Warnungen und Fehler“.
  - *Bedingung:* Teams mit Anforderungen an Datenhoheit, Firmen mit Sitz oder Kunden in der EU, Unternehmen, die Code oder Daten nicht in einer Anbieter-Cloud verarbeiten dürfen.
  - *Beleglage:* Beim Kurs Einschätzung ohne Beleg, bei AgentRun aus dem README abgeleitet, bei Projects Herstellerangabe.
  - [AgentRun (Show HN)](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md), [Building AI Agents (Kurs)](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)

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
  - Eine Gesamtkostenrechnung liefert der Hersteller nicht. Zum Anteil der Energie an den Compute-Kosten siehe „Zahlen und Richtwerte“, zum Hardwarebedarf großer Modelle siehe „Was mehrfach belegt ist“.
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

- **Kimi K3.1 Pro braucht rund 2,84 TB allein für die Gewichte, DeepSeek Ultrafast 4 bis 8 Blackwell-GPUs.**
  - Die Herleitung und die Einordnung zusammen mit LongCat-2.5 stehen unter „Was mehrfach belegt ist“.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [DeepSeek Ultrafast](../quellen/2026/11/2026-11-14-deepseek-ultrafast.md)

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
- **Self-hosted Claude Managed Agents: Agenten, Credentials und Verlauf in der eigenen Infrastruktur.**
  - Anthropic hat am 12.11.2026 Self-hosted Claude Managed Agents angekündigt. Agents, Credentials und Session History liegen in der eigenen Cloud oder on premise.
  - Der Kunde wählt, wohin Requests an Claude gehen: „You host the agents, credentials, and session history, and choose where requests to Claude are sent.“
  - Das Modell selbst bleibt Claude, die Anfragen gehen weiter an einen Endpunkt außerhalb der eigenen Gewichte.
  - *Bedingung:* Eigenes Produkt, kein Ersatz für Projects. Zur Cloud-Bindung von Projects siehe „Was mehrfach belegt ist“.
  - *Beleglage:* Herstellerangabe.
  - [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)

## Warnungen und Fehler

### Verfügbarkeit nach Region und Vertrag

- **Die Region oder der Vertrag kann ein Modell ausschließen, auch wenn es fachlich gut ist.**
  - Goldman Sachs nahm Claude im April in Hongkong von seiner internen Plattform, JPMorgan folgte im Juni.
  - ChatGPT und Gemini blieben bei Goldman in Hongkong verfügbar.
  - Laut einem Anthropic-Sprecher war Claude „had never been officially supported in Hong Kong“.
  - *Bedingung:* Das betrifft multinationale Unternehmen mit Standorten außerhalb der Regionen, die ein Anbieter offiziell unterstützt.
  - *Beleglage:* Die Quelle stellt das nur als Behauptung dar und belegt es nicht.
  - [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- **Viele Hosting-Anbieter heißt nicht geklärte Region.**
  - Inkling 2 Small ist gehostet bei NVIDIA, Fireworks, Together, Baseten, Nebius, Modal und Cloudflare Workers AI verfügbar: „API access is also available through third party inference providers“.
  - Die Karte nennt weder Preise noch Hosting-Regionen. Für EU-konforme oder souveräne Nutzung muss die Region bei jedem Anbieter einzeln geklärt werden.
  - *Bedingung:* Unternehmen mit EU-Datenresidenz- oder Souveränitätsanforderungen.
  - *Beleglage:* Herstellerangabe.
  - [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md)

### Lock-in bei Anbieter-Clouds

- **Je mehr Dev-Setup und Memory in der Anbieter-Cloud liegt, desto schwerer der Ausstieg.**
  - Kommentatoren sehen in der Verlagerung in Claude Code Projects einen wachsenden Lock-in: „The more of your development setup is running in the cloud, I think it will be really hard to justify leaving.“
  - *Bedingung:* Teams, die Entwicklungsprozess und Projektwissen komplett in Projects ablegen.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)

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
- **Unter welcher Lizenz steht Qwen3.8-27B selbst?**
  - Die Unsloth-Seite nennt keine Lizenz, die DSpine-Karte nur die Apache-2.0-Lizenz des Draft-Modells.
  - [Unsloth Qwen3.8-27B](../quellen/2026/11/2026-11-14-unsloth-qwen3-8-27b-quantizations-dynamic-v3-1-update.md), [DSpine for Qwen3.8-27B](../quellen/2026/11/2026-11-14-tencent-qwen3-8-27b-dspine-b16-dspine-for-qwen3-8-27b.md)
- **Was regelt die Acceptable Use Policy von Inkling 2 Small, und in welchen Regionen hosten die Drittanbieter?**
  - Die Karte verlinkt die Policy ohne Inhalt und nennt weder Regionen noch Preise.
  - [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md)
- **Läuft LongCat-2.5 mit vertretbarem Aufwand auf NVIDIA-GPUs, und auf welchen Chips beruhen die Effizienzangaben?**
  - Die Card dokumentiert nur NPU-Deployment und nennt den Chiphersteller nicht.
  - [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md)
- **Wann laufen Projects-Threads lokal hinter dem eigenen Netzwerk?**
  - Angekündigt ist „coming very soon“, ein Datum fehlt.
  - [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)
- **Ab wann rechnet sich lokale Inferenz gegenüber API-Gebühren?**
  - Edge0 liefert keine Gesamtkostenrechnung für Hardware und Strom.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md)
- **Läuft Mirage nach dem Vorab-Download vollständig offline?**
  - Die Card beschreibt keinen Offline-Betrieb, ein eigener Test steht aus.
  - [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
