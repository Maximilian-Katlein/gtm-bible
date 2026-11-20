# Sovereign AI

Diese Seite sammelt, was Unternehmen beachten müssen, wenn sie KI-Modelle unabhängig von einzelnen Anbietern, Regionen und Vertragsbedingungen betreiben wollen. Sie fasst Belege zu Verfügbarkeit, Exit-Strategien, Hardware- und Compute-Kosten, Bindung an Cloud-Hardware, lokalem, hybridem und Offline-Betrieb, Lizenzen und Offenheit, Herkunft und Rechtsstatus von Trainingsdaten, Code-Prüfung, Hintertüren in Modellen, Cloud-Bindung und Datenabfluss von Agenten-Tools und Anwendungen, Telemetrie in Entwickler-Werkzeugen und unter Windows, politischer Verzerrung offener Modelle und Regulierung von KI in der Abschlussprüfung zusammen.

Stand: 2026-11-20 · 34 Quellen · 69 Learnings

## Was mehrfach belegt ist

### Lizenz, Herkunft und Dokumentation

- **Lizenz offener Modelle vor kommerziellem Einsatz selbst prüfen (9 Quellen).**
  - LFM3-1.7B steht unter der LFM Open License v1.0. Das ist keine Standardlizenz wie Apache 2.0 oder MIT, und die Card nennt keine Bedingungen zu kommerzieller Nutzung oder EU.
  - Edge0-145B nennt nach dem Material überhaupt keine Lizenz, die kommerzielle Nutzung ist damit offen.
  - Bei Mirage steht im Lizenzfeld „license: apache-2.0“, was kommerzielle Nutzung grundsätzlich erlaubt. Die Runtime liegt aber in einem separaten Repo (Cactus-Compute/cactus). Deren Lizenz und den Lizenztext im Modell-Repo getrennt prüfen.
  - Die Unsloth-Seite zu Qwen3.8-27B nennt weder Lizenz noch Bedingungen für kommerzielle Nutzung. Das muss man an anderer Stelle prüfen.
  - Das DSpine-Draft-Modell für Qwen3.8-27B steht unter Apache 2.0 („license: apache-2.0“), ohne zusätzliche Einschränkungen zu kommerzieller Nutzung oder EU. Für den Betrieb zählt aber auch die Lizenz von Qwen3.8-27B, die diese Karte nicht nennt.
  - Bei TrnRT steht die Inferenz-Engine unter Apache 2.0. Die Lizenz des eingesetzten Modells GLM-5.3-Flash nennt das Material nicht. Wie bei DSpine zählt für den Betrieb auch die Lizenz des Modells.
  - Inkling 2 Small steht unter Apache 2.0. Die Karte verlinkt daneben eine separate Acceptable Use Policy, ohne Inhalt oder Verhältnis zur Lizenz zu erklären.
  - LongCat-2.5 steht unter MIT-Lizenz ohne Einschränkung nach Branche oder Region, also ohne EU-Ausschluss. Marken und Patente sind ausgenommen: „This license does not grant any rights to use Meituan trademarks or patents.“ Eine Patentlizenz wie bei Apache 2.0 fehlt, das sollte rechtlich geprüft werden. Diese Bewertung ist eine Einordnung, kein Teil der Karte.
  - Hy4 flash steht unter der Tencent Hy License, deren Inhalt nicht auf der Karte steht: „Hy4 flash is released under the Tencent Hy License. See LICENSE for details.“ Kommerzielle Nutzung und EU-Einsatz müssen anhand der LICENSE-Datei rechtlich geprüft werden.
  - In allen Fällen gilt: Vor dem Einsatz den LICENSE-Text im Repo lesen. Zusätzlich bei Mirage die Lizenz der Runtime, bei DSpine und TrnRT die des Modells, bei Inkling die Acceptable Use Policy.
  - Zu Qwen4-Max, bei dem schon offen ist, ob es überhaupt offene Gewichte gibt, siehe „Warnungen und Fehler“. Zur ebenfalls ungenannten Lizenz von Mastra Factory siehe „Werkzeuge“.
  - *Bedingung:* Kommerzielle, souveräne und Sovereign-AI-Setups, insbesondere in der EU. Bei Inkling alle, die das Modell in Produkten einsetzen oder weitergeben. Bei Hy4 flash vor jedem kommerziellen oder EU-Einsatz.
  - *Beleglage:* Bei LFM3, Mirage, DSpine, TrnRT, LongCat und Hy4 flash Herstellerangaben, bei Edge0, Unsloth und Inkling Behauptung ohne Beleg.
  - [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md), [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md), [Unsloth Qwen3.8-27B](../quellen/2026/11/2026-11-14-unsloth-qwen3-8-27b-quantizations-dynamic-v3-1-update.md), [DSpine for Qwen3.8-27B](../quellen/2026/11/2026-11-14-tencent-qwen3-8-27b-dspine-b16-dspine-for-qwen3-8-27b.md), [TrnRT (Show HN)](../quellen/2026/11/2026-11-18-show-hn-trnrt-open-source-llm-inference-engine-for-aws-train.md), [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md), [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md), [Hy4 flash Model Card](../quellen/2026/11/2026-11-20-hy4-flash-tencent-hy4-flash-model-card.md)
- **Trainingsdaten, Datenherkunft und Evaluierung bleiben bei offenen Modellen unbelegt (6 Quellen).**
  - Edge0 veröffentlicht nach dem Material nur Gewichte, Framework und Tools, aber keine Trainingsdaten und keinen Trainingscode.
  - Die Mirage-Card enthält keine Angaben zu Trainingsdaten, Datenherkunft oder EU-Konformität.
  - Die Card von Inkling 2 Small nennt keine Datenmenge, keinen Wissensstichtag, keinen Rechenaufwand und keine Sicherheitsevaluierung. Datenquellen stehen nur grob da (öffentlich, zugekauft, intern, synthetisch), zur Aufbereitung heißt es nur: „may include deduplication and filtering to remove junk or other low-quality data“.
  - Die LongCat-2.5-Card enthält keine Angaben zu Trainingsdaten, Datenrechten, Safety-Evaluation oder EU-Regulierung. Datenschutz, Privatsphäre und Inhaltssicherheit liegen ausdrücklich beim Betreiber.
  - Das CCORE-Modell Qwen3.5-4B-GLB-3D-Coder ist ein Feintuning auf Qwen/Qwen3.5-4B. Für die Herkunft zählen die Basisgewichte, zu deren Trainingsdaten die Karte nichts sagt. Zur Bezeichnung „independently developed“ siehe „Warnungen und Fehler“.
  - Für SenseNova-Loop-9B fehlen Angaben zu Trainingsdaten und Sicherheitsbewertung. Auch Laufzeiten jenseits von transformers (vLLM, llama.cpp, GGUF) sind nicht genannt. Für einen EU-Einsatz bleiben damit neben der Datenherkunft auch der Betriebsweg ungeklärt. Zum mitgelieferten Code siehe unten.
  - Für Sovereign-AI-Anforderungen und Dokumentationspflichten etwa nach AI Act ist ein solches Modell auf Basis der Card allein nicht bewertbar.
  - *Bedingung:* Öffentliche Hand, regulierte Branchen, EU-Beschaffung, kommerzielle Umgebungen, Compliance-Dokumentation, Herkunfts- und Lizenzkettenprüfung. Bei SenseNova Einsatz in der EU oder in abgeschotteten Umgebungen.
  - *Beleglage:* Bei Edge0 und Mirage Behauptung ohne Beleg, bei Inkling, LongCat, CCORE und SenseNova Herstellerangabe.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md), [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md), [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md), [CCORE Qwen3.5-4B-GLB-3D-Coder](../quellen/2026/11/2026-11-15-ccore-qwen3-5-4b-glb-3d-coder.md), [SenseNova-Loop-9B](../quellen/2026/11/2026-11-19-sensenova-sensenova-loop-9b.md)
- **Für deutschsprachigen Einsatz fehlen bei offenen Modellen oft die Belege (3 Quellen).**
  - Die Card von Kimi K3.1 Pro nennt keine unterstützten Sprachen und sagt nichts zur Qualität auf Deutsch.
  - Die Unsloth-Seite zu Qwen3.8-27B nennt ebenfalls keine unterstützten Sprachen.
  - Die Wirkung von Arete-27B ist nur für englischsprachige Prompts gemessen: „Prompts come from English-language government statutes, news and research reports“.
  - Für Deutsch fehlt jeder Beleg, bei Arete ebenso Werte mit aktiviertem Thinking-Modus.
  - *Bedingung:* Deutschsprachige Anwendungen, produktiver Einsatz selbst gehosteter Modelle.
  - *Beleglage:* Bei Unsloth Behauptung ohne Beleg.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [Unsloth Qwen3.8-27B](../quellen/2026/11/2026-11-14-unsloth-qwen3-8-27b-quantizations-dynamic-v3-1-update.md), [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

### Betrieb, Hardware und Code

- **Mitgelieferten Modellcode vor dem Einsatz prüfen (4 Quellen).**
  - Kimi K3.1 Pro bringt eigenen Code mit (custom_code), der vor dem Einsatz geprüft werden muss.
  - LFM3-1.7B verlangt beim Laden mit Transformers „trust_remote_code=True,“. Dabei wird Modellcode aus dem Repo ausgeführt.
  - Der dokumentierte Startbefehl von DSpine für Qwen3.8-27B setzt ebenfalls „--trust-remote-code“ und führt damit Code aus dem Repository aus.
  - SenseNova-Loop-9B trägt die Metadaten „"library_name": "transformers", tags: custom_code“. Modelle mit diesem Tag bringen eigenen Python-Code mit und brauchen meist trust_remote_code=True.
  - In abgesicherten oder souveränen Umgebungen den Code vorher prüfen und das Modell auf einen festen Commit pinnen. Bei LFM3 kann man auf GGUF, ONNX oder OpenVINO ausweichen.
  - *Bedingung:* Selbst-Hosting in abgeschotteten, On-Premise- oder regulierten Umgebungen. Bei LFM3 gilt das nur für die Transformers-Variante. Bei SenseNova ist das trust_remote_code-Erfordernis aus dem Tag geschlossen, nicht aus einer Anleitung belegt.
  - *Beleglage:* Bei DSpine und SenseNova Herstellerangabe.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [LFM3-1.7B Model Card](../quellen/2026/11/2026-11-13-liquidai-lfm3-1-7b-model-card-auf-hugging-face.md), [DSpine for Qwen3.8-27B](../quellen/2026/11/2026-11-14-tencent-qwen3-8-27b-dspine-b16-dspine-for-qwen3-8-27b.md), [SenseNova-Loop-9B](../quellen/2026/11/2026-11-19-sensenova-sensenova-loop-9b.md)
- **Eigener Betrieb hängt an großer oder spezieller Hardware (5 Quellen).**
  - Kimi K3.1 Pro: Rechnerisch belegen allein die Gewichte rund 2,84 TB, der KV-Cache kommt noch dazu. Ein Server mit 8 GPUs zu je 141 GB hat zusammen etwa 1,1 TB und reicht deshalb nicht. Ohne API muss das Modell über mehrere Knoten verteilt laufen. In den Safetensors-Metadaten steht: „"total": 2780110363392“.
  - DeepSeek Ultrafast: Der Selbstbetrieb der Engine setzt 4 bis 8 Blackwell-Rechenzentrums-GPUs voraus. Die HN-Diskussion spottet: „I'll just go get my 8 x B300 (TP8) from the shed and start this up real quick“. Für kleine Teams bleibt praktisch nur die gehostete Variante.
  - Hy4 flash: Beide Referenz-Setups brauchen acht GPUs. Überschlag aus 220,24B Parametern: rund 440 GB Gewichte in BF16, rund 220 GB in FP8, dazu der KV-Cache. Die 12B aktiven Parameter senken die Rechenlast, nicht den Speicherbedarf.
  - LongCat-2.5 dokumentiert Deployment nur für NPU-Plattformen über einen Branch von SGLang-FluentLLM: „LongCat-2.5 can be deployed on NPU platforms.“ Eine Anleitung für NVIDIA-GPUs, vLLM, llama.cpp oder GGUF fehlt. Die beworbenen Effizienzvorteile hängen an inländischen Beschleunigern des Herstellers, deren Chiphersteller nicht genannt wird.
  - TrnRT: Die Inferenz-Engine ist offen (Apache 2.0) und läuft mit einem offenen Modell, die Hardware bleibt aber an AWS Trainium gebunden. Preise nennt das Material nur für us-east-2. Ob trn2.48xlarge in der EU verfügbar ist, steht nicht drin.
  - Offene Gewichte und offene Engines heißen deshalb nicht souveräner Betrieb. Eigene Kontrolle über die Inferenz ist an große Hardware-Budgets, an Portierungsaufwand oder an einen einzelnen Cloud-Anbieter gebunden.
  - *Bedingung:* Kimi: souveräner Betrieb ohne API, die Zahl ist eine eigene Ableitung aus den Metadaten des Original-Checkpoints. DeepSeek: Einzelpersonen und kleine Teams ohne eigenen GPU-Cluster. Hy4 flash: Die Speicherzahlen sind eine Überschlagsrechnung auf Basis der Herstellerangaben. LongCat: Betreiber in der EU mit GPU-Infrastruktur, die die Portierung selbst leisten müssten. TrnRT: Einsatz mit Datenhoheitsanforderungen, Region und Bedingungen vorher bei AWS und beim Modellanbieter prüfen.
  - *Beleglage:* Bei Kimi eigene Ableitung, bei DeepSeek Anekdote, bei Hy4 flash, LongCat und TrnRT Herstellerangabe.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [DeepSeek Ultrafast](../quellen/2026/11/2026-11-14-deepseek-ultrafast.md), [Hy4 flash Model Card](../quellen/2026/11/2026-11-20-hy4-flash-tencent-hy4-flash-model-card.md), [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md), [TrnRT (Show HN)](../quellen/2026/11/2026-11-18-show-hn-trnrt-open-source-llm-inference-engine-for-aws-train.md)
- **Lokaler Betrieb heißt nicht offline (2 Quellen).**
  - Mirage: Das Paket cactus-compute lädt Engine und Gewichte beim ersten Aufruf automatisch aus dem Netz: „The package downloads and caches the engine and weights on first use.“ Für Air-Gap- oder souveräne Umgebungen müssen Engine und Gewichte vorab bezogen werden. Den Offline-Betrieb muss man selbst verifizieren, die Card beschreibt ihn nicht.
  - CCORE Qwen3.5-4B-GLB-3D-Coder: Das Modell läuft lokal, die erzeugten Three.js-Seiten laden Bibliotheken aber unter Umständen per CDN: „The page may load Three.js and its add-ons from a CDN.“ Für Offline- oder Air-Gap-Betrieb müssen Three.js und Add-ons selbst lokal bereitgestellt werden.
  - Netzabhängigkeiten können also in der Runtime und im erzeugten Output stecken. Beides vor dem Einsatz in abgeschotteten Umgebungen prüfen. Zur Prüfung von mitgeliefertem Code siehe oben, zum Datenabfluss bei selbst gehosteter Agenten-Infrastruktur und zu Telemetrie trotz Local-first-Werbung siehe unten.
  - *Bedingung:* Abgeschottete, regulierte oder souveräne Infrastruktur, Vorgaben ohne externe Abhängigkeiten.
  - *Beleglage:* Herstellerangabe bei beiden.
  - [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md), [CCORE Qwen3.5-4B-GLB-3D-Coder](../quellen/2026/11/2026-11-15-ccore-qwen3-5-4b-glb-3d-coder.md)
- **Lokale Inferenz lohnt sich bei sensiblen Daten, Offline-Bedarf und hohen API-Kosten, ist aber nicht kostenlos (2 Quellen).**
  - Lokaler Betrieb vermeidet Token- und API-Gebühren, hält Daten auf dem Rechner und erlaubt Offline-Betrieb (Edge0).
  - Als Einsatzfälle, in denen sich lokale KI vor allem lohnt, nennt ein zweiter Beitrag: sensible Kundendaten, Offline- und Feldarbeit, niedrige Latenz, Audio- oder Kamera-Eingaben, hohe API-Kosten und häufig wiederholte interne Abläufe (02:10).
  - Hardware und Strom kosten weiter Geld: „Hardware and electricity still cost money.“ Eine Gesamtkostenrechnung liefert keine der beiden Quellen.
  - Zum Hybrid-Muster aus lokalem und Cloud-Modell siehe „Taktiken und Abläufe“, zum Anteil der Energie an den Compute-Kosten siehe „Zahlen und Richtwerte“, zum Hardwarebedarf großer Modelle siehe oben, zum lokalen Server mit kompatiblen Endpunkten siehe „Werkzeuge“.
  - *Bedingung:* Bei Edge0 entsteht ein Kostenvorteil nur, wenn passende Hardware bereits vorhanden ist. Der zweite Beitrag richtet sich an Produktentwicklung und Gründer.
  - *Beleglage:* Bei Edge0 Herstellerangabe, beim Beitrag zu lokaler KI Behauptung ohne Beleg.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [I'm Obsessed With Local AI](../quellen/2026/11/2026-11-16-i-m-obsessed-with-local-ai-here-s-why.md)

### Agenten und Datenhoheit

- **Agenten-Tools und Anleitungen setzen Anbieter-Clouds voraus und sparen Datenhoheit aus (5 Quellen).**
  - Das sichtbare AgentRun-README nennt nur OpenRouter, Anthropic und OpenAI als Modellquellen. Zu EU-Hosting, Datenschutz oder Open-Weight-Modellen sagt es nichts.
  - Der Kurs „Building AI Agents“ leitet E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten über US-Cloud-Modelle (Claude, GPT, Gemini). DSGVO, Auftragsverarbeitung oder lokale Alternativen spricht er nicht an.
  - Threads in Claude Code Projects laufen derzeit nur in der Anthropic Cloud. Lokale Ausführung ist ohne Datum angekündigt: „Threads run in the cloud today; running on your machine alongside your local tools and code and behind your network is coming very soon.“ Für Organisationen mit Vorgaben zur Datenhaltung ist das Produkt vorerst ungeeignet.
  - Eine Demo zu Google AI Studio preist die Bildschirmfreigabe an ein Cloud-Modell als Produktivitätsgewinn um das 1,5- bis 3-Fache an: „I see this is the future of work“ (24:52). Ob Eingaben im Free Tier zum Training genutzt werden und wo die Daten verarbeitet werden, sagt die Folge nicht.
  - Claude Cowork läuft nur auf Anthropic-Modellen. Eine Demo zu Cowork und Claude Code behandelt weder Datenresidenz noch EU-Betrieb noch die Frage, welche Inhalte aus lokalen Dateien und Browsersitzungen bei Anthropic landen. Für regulierte Daten ist das vor dem Einsatz separat zu klären.
  - Wer souverän betreiben will, muss das vor dem Nachbau oder der Einführung selbst klären. Zur selbst gehosteten Variante von Anthropic siehe „Werkzeuge“, zum Lock-in und zu Anwendungen, die Anbieter und Modell ihrer KI nicht nennen, siehe „Warnungen und Fehler“.
  - *Bedingung:* Teams mit Anforderungen an Datenhoheit, Firmen mit Sitz oder Kunden in der EU, Unternehmen, die Code oder Daten nicht in einer Anbieter-Cloud verarbeiten dürfen. Bei AI Studio Unternehmenseinsatz mit vertraulichen Daten. Bei Cowork Unternehmen mit Datenschutz- oder Souveränitätsanforderungen.
  - *Beleglage:* Beim Kurs Einschätzung ohne Beleg, bei AgentRun aus dem README abgeleitet, bei Projects Herstellerangabe, bei AI Studio und Cowork Behauptung ohne Beleg.
  - [AgentRun (Show HN)](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md), [Building AI Agents (Kurs)](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md), [Google AI Studio (Demo)](../quellen/2026/11/2026-11-17-google-ai-studio-replaces-your-ai-tech-stack-full-demo.md), [Claude Cowork und Claude Code (Lektion)](../quellen/2026/11/2026-11-19-i-got-a-private-lesson-on-claude-cowork-claude-code.md)
- **Selbst gehostete Agenten-Infrastruktur hält Daten nur bis zum Modellaufruf intern (2 Quellen).**
  - Coral wirbt als selbst gehostetes Agenten-Gateway mit „zero data egress“. Das gilt nur für das Gateway. Was nach dem Filtern an ein externes LLM geht, verlässt trotzdem die eigene Infrastruktur.
  - Bei Self-hosted Claude Managed Agents liegen Agents, Credentials und Session History beim Kunden. Das Modell bleibt aber Claude, die Anfragen gehen an einen Endpunkt außerhalb der eigenen Gewichte (siehe „Werkzeuge“).
  - Vollständig intern bleibt ein solches Setup nur mit einem selbst gehosteten Modell.
  - *Bedingung:* Teams mit Anforderungen an Datenhoheit, die Agenten-Infrastruktur selbst betreiben, das Modell aber extern beziehen.
  - *Beleglage:* Bei Coral Behauptung ohne Beleg, bei Claude Managed Agents Herstellerangabe.
  - [Coral (Show HN)](../quellen/2026/11/2026-11-17-show-hn-coral-open-source-gateway-where-agents-write-their-o.md), [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)

### Telemetrie in Entwickler-Werkzeugen

- **Telemetrie ist ab Werk aktiv, auch bei Werkzeugen mit Local-first-Anspruch (2 Quellen).**
  - Onlook wirbt mit Local-first, im offiziellen Download sind Produkt-Analytics trotzdem standardmäßig aktiv: „In the official download they are on by default; a build from source asks first.“ Abschalten lässt sich das in den Einstellungen oder mit `STUDIO_TELEMETRY=0`. Der Source-Build fragt vorher und braucht laut README keinen Account.
  - Windows 11: Bei einer sauberen Installation von Windows 11 Home ARM64, Region USA, waren optionale Diagnosedaten schon ab Werk aktiv. Nach dem Setup mit Standardwerten stand AllowTelemetry auf 3: „After completing setup with those defaults, AllowTelemetry was 3“. Firmen sollten diesen Wert auf Entwicklerrechnern zentral prüfen.
  - In beiden Fällen ist die datensparsame Einstellung nicht der Standard. Telemetrie-Einstellungen deshalb vor dem Rollout je Werkzeug prüfen und zentral setzen.
  - Zur Erfassung der Agent-Nutzung unter Windows siehe „Warnungen und Fehler“, zum Abschalten der Diagnosedaten „Taktiken und Abläufe“.
  - *Bedingung:* Teams mit Datenschutz- oder Souveränitätsanforderungen. Bei Windows nur für eine US-Home-Installation belegt, EU sowie Pro und Enterprise sind nicht geprüft.
  - *Beleglage:* Bei Onlook Herstellerangabe, bei Windows eigene Daten des Autors.
  - [Onlook (Launch HN)](../quellen/2026/11/2026-11-20-launch-hn-onlook-yc-w25-an-open-source-developer-tool-for-de.md), [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)

## Taktiken und Abläufe

### Anbieterauswahl und Exit-Strategie

- **Drei Bausteine als Prüfraster für souveräne KI.**
  - Laut Mistral braucht es drei Dinge:
    - eine gesicherte, laufend weiterentwickelte Modellquelle,
    - Datenkontrolle auf dem eigenen Tenant ohne Rückfluss zum Anbieter,
    - eigene Compute-Infrastruktur zur Kostenkontrolle.
  - Zitat: „in sovereignty AI technology you need three things, you need to have a source of model that is secured“ (04:23).
  - *Bedingung:* Enterprise und Public Sector mit KI in Kernprozessen.
  - *Beleglage:* Behauptung ohne Beleg. Das Raster stammt von einem Anbieter, der genau diese drei Bausteine verkauft.
  - [Mistral-CEO-Interview](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
- **Workloads nach geopolitischem Risiko einstufen.**
  - Gartners Ablauf zur Geopatriation:
    - Workloads nach Sensibilität und geopolitischem Risiko bewerten,
    - souveräne Angebote der Hyperscaler gegen lokale Anbieter vergleichen,
    - souveräne Cloud mit On-Premises oder Colocation kombinieren,
    - Attestierung und Souveränitätsrahmen einführen,
    - die Platzierung laufend nachziehen.
  - Die Optionen reichen von der souveränen Hyperscaler-Region über partnerbetriebene Regionen bis zum eigenen Rechenzentrum.
  - Zur Prognose, wie viele Unternehmen Workloads verlagern, siehe „Strittig“.
  - *Bedingung:* Unternehmen mit Workloads bei globalen Hyperscalern.
  - *Beleglage:* Behauptung ohne Beleg. Gartner verkauft Beratung und Research-Abos.
  - [Gartner 2026](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2026.md)
- **SovereignTech heißt Ausstieg ermöglichen.**
  - Gartner definiert SovereignTech als Hardware, Software, Datenbanken und Modelle, die technisch und rechtlich realistische Exit-Strategien von kritischen Anbietern erlauben und dauerhaft verfügbar bleiben.
  - Begründung: der US CLOUD Act, DORA mit vertraglich verlangten Cloud-Exit-Strategien und CADA, dazu der Wertabfluss durch Abo- und API-Gebühren an ausländische Anbieter.
  - *Bedingung:* EU-Unternehmen, besonders Finanzsektor unter DORA.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Gartner 2027](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2027.md)
- **Anbieter nach Abschaltrisiko fragen.**
  - Gartners Schritte zu SovereignTech:
    - private, On-Premises- und Ökosystem-Alternativen zur Public Cloud bewerten,
    - Technik der Vorgeneration kreativ nutzen und mit vertrauenswürdigen Partnern teilen,
    - Trusted Tech Alliance und EU Tech Sovereignty Package beobachten,
    - Anbieter nach souveränen Lieferoptionen und Zusagen ohne Abschaltmöglichkeit fragen.
  - Der Einkauf bewertet nach Exit-Optionen, nicht nur nach Kosten und Funktion.
  - *Bedingung:* Einkauf und Architektur kritischer Dienste.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Gartner 2027](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2027.md)
- **Von Datenstandort zu Ausstiegsfähigkeit.**
  - Im Vergleich der beiden Gartner-Listen verschiebt sich die Frage. 2026 ging es bei Geopatriation darum, wo Workloads laufen. 2027 geht es bei SovereignTech darum, ob man aussteigen kann, wenn ein Anbieter Modelle einschränkt, ändert oder zurückzieht.
  - Gartner warnt zusätzlich, dass eigene Daten dauerhaft in fremde Modellgewichte eingehen können.
  - *Bedingung:* EU-Unternehmen mit KI auf fremden Modellen.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Gartner 2027](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2027.md)

### Daten schützen, wenn Cloud-Modelle beteiligt sind

- **Hybrid-Muster: lokal bereinigen, in der Cloud weiterdenken.**
  - Ein lokales Modell liest sensible Dokumente und entfernt private Details. Erst die bereinigte Fassung geht für tieferes Reasoning an ein Cloud-Modell.
  - Zitat: „strip or summarize all the private details“ (13:20).
  - Wann sich lokale KI generell lohnt, steht unter „Was mehrfach belegt ist“.
  - *Bedingung:* Unternehmen mit Datenschutzanforderungen.
  - *Beleglage:* Behauptung ohne Beleg.
  - [I'm Obsessed With Local AI](../quellen/2026/11/2026-11-16-i-m-obsessed-with-local-ai-here-s-why.md)
- **Confidential Computing für Daten in Verarbeitung.**
  - Confidential Computing schützt Daten während der Verarbeitung in hardwarebasierten Trusted Execution Environments, auch gegenüber dem Cloud-Anbieter.
  - Schritte laut Gartner: betroffene Workloads kartieren, TEEs mit eigenen und offenen Modellen testen, eigene Schlüsselverwaltung aufbauen.
  - Mehr Kontrolle heißt mehr Kosten und Betriebsaufwand. Zur Prognose für 2029 siehe „Zahlen und Richtwerte“.
  - *Bedingung:* Sensible Workloads in fremder Infrastruktur.
  - *Beleglage:* Prognose ohne Methodik.
  - [Gartner 2026](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2026.md)

### Entwicklerrechner unter Windows 11

- **Optionale Diagnosedaten abschalten, um die Erfassung der Agent-Nutzung zu verhindern.**
  - Unter Einstellungen, Datenschutz und Sicherheit, Diagnose und Feedback die optionalen Diagnosedaten abschalten oder sie schon beim Setup ablehnen.
  - Der Report ist als optional markiert. Den abgeschalteten Fall hat der Autor nicht selbst getestet.
  - In Firmen zusätzlich den Wert AllowTelemetry auf Entwicklerrechnern zentral prüfen, weil optionale Diagnosedaten ab Werk aktiv sein können (siehe „Was mehrfach belegt ist“). Zu Befund und Grenzen siehe „Warnungen und Fehler“.
  - *Bedingung:* Windows 11. Die Wirkung des Abschaltens ist nicht gemessen.
  - *Beleglage:* Eigene Daten des Autors, der abgeschaltete Fall ungetestet.
  - [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)

### Kontrolle von Modellausgaben

- **Ausgaben von Modellen unabhängiger Anbieter gegenseitig prüfen lassen.**
  - Mehrere LLMs von verschiedenen Anbietern kontrollieren die Ausgaben der jeweils anderen.
  - Zwei Instanzen desselben Anbieters gelten laut Sprecher nicht als unabhängige Kontrolle: „Two different versions of chat GPT can't police each other and the same goes for two instances of Claude.“ (08:58).
  - Kosten und Latenz des Ansatzes nennt die Quelle nicht. Zur Frage, für wen Hintertüren ein ernstes Risiko sind, siehe „Warnungen und Fehler“.
  - *Bedingung:* Kritische Agenten-Workflows mit Budget für mehrere Modellanbieter.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md)

### Prüfung auf politische Verzerrung

- **Faktentreue und Framing getrennt messen.**
  - Ein Modell kann Fakten gut wiedergeben und trotzdem die Staatsdarstellung übernehmen.
  - Nous Research trennt deshalb: „We separated factual recall, the ability to corroborate verified sources of truth, from framing“.
  - Beispiel GLM 5.3: Es erreicht einen hohen Faktenwert von 3,10 und übernimmt trotzdem in 15 Prozent der Antworten die Staatsdarstellung.
  - *Bedingung:* Teams, die Open-Weight-Modelle auf Bias oder Staatsnähe prüfen.
  - *Beleglage:* Eigene Daten der Autoren.
  - [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)
- **Vor EU-Einsätzen mit sensiblen Themen über den tatsächlichen Zugangsweg selbst testen.**
  - Ein informeller Test von Qwen4-Max zeigt: Das Modell beantwortet Alltagsthemen, scheitert aber an politisch heiklen Fragen und sogar an einfachen Fakten wie dem Sitz von TSMC.
  - Zitat: „It'll gush about how to make moon cakes and where the tallest and longest bridges are“.
  - Getestet werden sollte über denselben Zugangsweg, den man später produktiv nutzt. Zur systematischen Messung chinesischer Modelle siehe „Zahlen und Richtwerte“.
  - *Bedingung:* Zugangsweg und Systemprompt des Tests sind unbekannt.
  - *Beleglage:* Anekdote.
  - [Qwen4-Max](../quellen/2026/11/2026-11-17-qwen4-max.md)

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

- **Kimi K3.1 Pro braucht rund 2,84 TB allein für die Gewichte, DeepSeek Ultrafast 4 bis 8 Blackwell-GPUs, Hy4 flash acht GPUs bei rund 440 GB (BF16) oder 220 GB (FP8) Gewichten.**
  - Die Herleitung und die Einordnung zusammen mit LongCat-2.5 und TrnRT stehen unter „Was mehrfach belegt ist“.
  - [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [DeepSeek Ultrafast](../quellen/2026/11/2026-11-14-deepseek-ultrafast.md), [Hy4 flash Model Card](../quellen/2026/11/2026-11-20-hy4-flash-tencent-hy4-flash-model-card.md)

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
  - Zu einem informellen Test von Qwen4-Max siehe „Taktiken und Abläufe“.
  - *Bedingung:* Eigene Evaluation der Autoren mit Vergleichsmodellen bei Temperatur 0,6, chinesischen Modellen mit Thinking aus und nur englischen Prompts.
  - *Beleglage:* Herstellerangabe.
  - [Arete-27B Model Card](../quellen/2026/11/2026-11-13-arete-27b-model-card-nousresearch-arete-27b.md)

### Analystenprognosen

*Gartner-Prognosen nennen Zieljahr und Prozentwert, die Methodik ist nicht offengelegt. Gartner verkauft Beratung und Research-Abos.*

- **Über 75 % der Organisationen außerhalb der USA setzen bis 2030 Strategien für digitale Souveränität um.**
  - Sie verlagern laut Gartner kritische Workloads, um geopolitische Risiken und Lock-in zu senken.
  - *Bedingung:* Organisationen außerhalb der USA.
  - *Beleglage:* Prognose ohne Methodik.
  - [Gartner 2027](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2027.md)
- **Bis 2029 sollen 75 % der Verarbeitung auf nicht vertrauenswürdiger Infrastruktur per Confidential Computing geschützt sein.**
  - Zu Ablauf und Aufwand siehe „Taktiken und Abläufe“.
  - *Beleglage:* Prognose ohne Methodik.
  - [Gartner 2026](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2026.md)

## Werkzeuge

- **edge0-infer serve: lokaler Server mit OpenAI- und Anthropic-kompatiblen Endpunkten.**
  - Der Befehl startet einen Server auf 127.0.0.1:8000: „and then serves OpenAI- and Anthropic-compatible endpoints“.
  - Bestehende Clients lassen sich per Basis-URL umstellen, ohne dass Daten die eigene Maschine verlassen.
  - Zur fehlenden Lizenzangabe von Edge0 und zu den laufenden Kosten lokaler Inferenz siehe „Was mehrfach belegt ist“.
  - *Bedingung:* NVIDIA mit CUDA 13 (Linux, Windows) oder Apple Silicon mit Metal, dort nur Q3_K.
  - *Beleglage:* Herstellerangabe.
  - [Edge0-145B-NVFP4 Model Card](../quellen/2026/11/2026-11-15-edge0-edge0-145b-nvfp4-model-card-auf-hugging-face.md)
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
  - Das Modell selbst bleibt Claude, die Anfragen gehen weiter an einen Endpunkt außerhalb der eigenen Gewichte. Dieselbe Grenze zeigt das Gateway Coral, siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Eigenes Produkt, kein Ersatz für Projects. Zur Cloud-Bindung von Projects siehe „Was mehrfach belegt ist“.
  - *Beleglage:* Herstellerangabe.
  - [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)
- **Mastra Factory: offene Software-Factory für den Betrieb auf eigener Infrastruktur.**
  - Start mit `npm create factory`, Vorlage im Repo mastra-ai/template-factory.
  - Laut Hersteller vollständig auf eigener Infrastruktur betreibbar, daneben gibt es eine gehostete Version: „It's fully open-source, so you can run it entirely on your infra (we also offer a hosted version).“
  - Lizenz, nötige Modelle, Sandbox-Anbieter und EU-Hosting nennt der Beitrag nicht. Zur Grenze selbst gehosteter Agenten-Infrastruktur beim Modellaufruf siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Vor souveränem Einsatz Lizenz und Modellabhängigkeiten selbst prüfen.
  - *Beleglage:* Herstellerangabe.
  - [Mastra Factory (Show HN)](../quellen/2026/11/2026-11-19-show-hn-mastra-factory-the-open-source-software-factory-we-u.md)

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
  - Ähnlich offen ist die Region bei TrnRT auf AWS Trainium, siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Unternehmen mit EU-Datenresidenz- oder Souveränitätsanforderungen.
  - *Beleglage:* Herstellerangabe.
  - [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md), [TrnRT (Show HN)](../quellen/2026/11/2026-11-18-show-hn-trnrt-open-source-llm-inference-engine-for-aws-train.md)

### Herkunft chinesischer Modelle im Einkauf

- **Bei Qwen und DeepSeek mit Einkaufs-, Sicherheits- und geopolitischen Bedenken rechnen.**
  - Im Enterprise-Vertrieb haben manche Käufer Vorbehalte: „some buyers will have procurement, security, or geopolitical concerns.“ (15:25).
  - In regulierten Branchen die lokale Ausführung offener Gewichte klar vom gehosteten Dienst des Herstellers trennen.
  - Zur gemessenen politischen Verzerrung chinesischer Modelle siehe „Zahlen und Richtwerte“.
  - *Bedingung:* Enterprise-Vertrieb, regulierte B2B-Märkte.
  - *Beleglage:* Behauptung ohne Beleg.
  - [I'm Obsessed With Local AI](../quellen/2026/11/2026-11-16-i-m-obsessed-with-local-ai-here-s-why.md)

### Lock-in bei Anbieter-Clouds

- **Je mehr Dev-Setup und Memory in der Anbieter-Cloud liegt, desto schwerer der Ausstieg.**
  - Kommentatoren sehen in der Verlagerung in Claude Code Projects einen wachsenden Lock-in: „The more of your development setup is running in the cloud, I think it will be really hard to justify leaving.“
  - Zur Exit-Fähigkeit als Einkaufskriterium siehe „Taktiken und Abläufe“, zur Bindung offener Inferenz an AWS-Hardware siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Teams, die Entwicklungsprozess und Projektwissen komplett in Projects ablegen.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)

### Datenweitergabe an KI in Anwendungen

- **Eine „privat“-Option verrät, dass alle übrigen Inhalte an eine KI gehen.**
  - Foolscap sagt zu: „Mark a book private, and nothing of it goes to any AI at all.“ Im Umkehrschluss werden nicht private Inhalte an eine KI übermittelt.
  - Wer so formuliert, sollte Anbieter, Modell und Speicherort nennen. Foolscap tut das nicht.
  - Zu ähnlichen Lücken bei Agenten-Tools siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Relevant für DSGVO-Prüfung und souveräne KI.
  - *Beleglage:* Herstellerangabe.
  - [Foolscap (Show HN)](../quellen/2026/11/2026-11-20-show-hn-foolscap-a-writing-app-that-reads-your-book-and-neve.md)

### Telemetrie über Coding-Agenten unter Windows 11

- **Windows 11 erkennt, welche Coding-Agenten genutzt werden, und reiht das als Diagnosedaten zum Upload ein.**
  - Die Systemkomponente MissionControlAggregator.dll erkennt, ob Coding-Agenten wie Claude, Codex, Copilot oder Cursor genutzt werden, und stellt das Ergebnis als optionale Diagnosedaten in die DiagTrack-Upload-Queue.
  - Belegt ist das Einreihen, nicht der Empfang bei Microsoft.
  - Die Erkennung ist nicht auf WSL beschränkt. Die Komponente hört auf bestehende Windows-Events (KernelProcess.AppStateChangeSummary, Win32kTraceLogging.AppInteractivitySummary, Lxss.Manager.Exec), sodass auch ein normales Windows-codex.exe erfasst wird.
  - Zitat: „Why would a Windows system DLL need a list of coding agents and developer tools?“
  - Zum Abschalten siehe „Taktiken und Abläufe“. Dass optionale Diagnosedaten ab Werk aktiv sein können, steht unter „Was mehrfach belegt ist“.
  - *Bedingung:* Windows 11 mit aktivem Feature CLICodingAgentUsage und erlaubten optionalen Diagnosedaten.
  - *Beleglage:* Eigene Daten des Autors.
  - [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)
- **Der Report enthält keine Prompts, verrät aber das Werkzeugprofil.**
  - Der Report Segments.SubCohorts enthält keine Programmnamen, Prompts oder Quellcode, sondern ein Bit pro Kategorie, ob ein Werkzeug im Berichtsfenster beobachtet wurde.
  - Laufzeit und Interaktionszähler der Quell-Events scheinen verworfen zu werden.
  - Zitat: „Although I found no prompt text or source code in this report, collecting which agents and developer tools someone uses already has significant privacy implications.“
  - *Bedingung:* Gilt nur für diesen Report, nicht für die gesamte Windows-Telemetrie.
  - *Beleglage:* Eigene Daten des Autors.
  - [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)
- **Nicht belegt ist, dass die Erfassung auf jeder Windows-11-Installation läuft.**
  - Das Feature CLICodingAgentUsage war in einer VM als Service Experiment ohne manuelles Zutun aktiv, im ISO-Baseline-Image aber deaktiviert.
  - Zitat: „the evidence does not support saying that it is active on every Windows installation.“
  - *Bedingung:* Rollout-Umfang unbekannt.
  - *Beleglage:* Eigene Daten des Autors.
  - [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)

### Hintertüren in Modellen

- **LLM-Hintertüren sind vor allem für Organisationen mit wertvollen Systemen ein ernstes Problem.**
  - Für alle anderen bedeuten sie in erster Linie, bekannte Sicherheitsgrundlagen konsequent umzusetzen.
  - Zitat: „people who have lots of really expensive things to protect are going to find it to be a nightmare.“ (09:40).
  - Zur gegenseitigen Prüfung durch Modelle unabhängiger Anbieter siehe „Taktiken und Abläufe“.
  - *Bedingung:* Enterprise mit wertvollen digitalen Assets und komplexer Agenten-Infrastruktur.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md)

### Lücken in Model Cards

- **Bei Kimi K3.1 Pro bleibt vieles offen, das man für den Betrieb selbst klären muss.**
  - Die Card nennt keine unterstützten Sprachen, keine Inferenz-Engine und keine Hardwareanforderungen. Angegeben ist nur „library_name: transformers“.
  - Zum mitgelieferten Code siehe „Was mehrfach belegt ist“. Ähnliche Lücken bei Laufzeiten und Trainingsdaten zeigt SenseNova-Loop-9B, ebenfalls dort.
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
- **„Independently developed“ heißt nicht eigene Basis.**
  - Das CCORE-Modell wird als unabhängig entwickelt bezeichnet, ist technisch aber ein Feintuning von Qwen/Qwen3.5-4B: „This independently developed CCORE model was trained using Qwen/Qwen3.5-4B as its base.“
  - Für Herkunfts-, Lizenzketten- und Souveränitätsprüfungen zählen die Basisgewichte. Zu deren Trainingsdaten sagt die Karte nichts, siehe „Was mehrfach belegt ist“.
  - *Bedingung:* Bewertung von Herkunft und Compliance bei Open-Weight-Modellen.
  - *Beleglage:* Herstellerangabe.
  - [CCORE Qwen3.5-4B-GLB-3D-Coder](../quellen/2026/11/2026-11-15-ccore-qwen3-5-4b-glb-3d-coder.md)
- **Qwen4-Max hat vermutlich keine offenen Gewichte.**
  - Laut Kommentaren wäre das Modell nur über Qwen oder Partner nutzbar, eventuell über Bedrock: „oh, I guess this isn't open weights, so presumably I'll have to get it through Qwen or whoever they might partner with (Bedrock?).“
  - Selbsthosting nicht einplanen, bevor die Lizenz bestätigt ist.
  - *Bedingung:* Teams mit Selbsthosting- oder Souveränitätsanforderungen. Die Lizenz ist unbestätigt.
  - *Beleglage:* Behauptung ohne Beleg.
  - [Qwen4-Max](../quellen/2026/11/2026-11-17-qwen4-max.md)

### Rechtsstatus von Trainingsdaten

- **In den USA gemeinfreie Texte sind außerhalb der USA nicht automatisch frei.**
  - Trainingstexte, die in den USA gemeinfrei sind, können anderswo einen anderen Rechtsstatus haben: „Public-domain status outside the US may differ.“
  - Für eigene Nachtrainings in der EU ist das gesondert zu prüfen.
  - *Bedingung:* Nutzung US-gemeinfreier Korpora außerhalb der USA. Im Projekt selbst nicht geprüft.
  - *Beleglage:* Eigene Daten des Projekts.
  - [DeepSeek V3 in Jax (Show HN)](../quellen/2026/11/2026-11-15-show-hn-deepseek-v3-in-200-lines-of-pure-jax.md)

### Regulierung von KI in der Abschlussprüfung

- **KI darf Unabhängigkeit, Integrität und professionelle Skepsis des Prüfers nicht untergraben.**
  - Der britische Financial Reporting Council warnt laut Artikel davor: „AI must not undermine auditor independence, integrity or professional scepticism“.
  - Die Verantwortung für das Prüfungsurteil bleibt beim menschlichen Prüfer, auch wenn KI-Agenten im Prüfungsablauf eingesetzt werden.
  - Eine konkrete FRC-Publikation zitiert der Artikel nicht.
  - *Bedingung:* Britischer Prüfungsmarkt.
  - *Beleglage:* Behauptung ohne Beleg.
  - [KI-Agenten im KPMG-Prüfungstest](../quellen/2026/11/2026-11-19-ai-agents-ask-better-questions-than-kpmg-accountants-in-audi.md)

## Strittig

- **Geopatriation: Gilt Gartners 75-%-Prognose global oder nur für Europa und den Nahen Osten?**
  - E-Book: 75 % der Unternehmen verlagern Workloads bis 2030 aus globalen Clouds in souveräne oder lokale Umgebungen.
  - Pressemitteilung zur selben Liste: über 75 % der Unternehmen in Europa und dem Nahen Osten, von unter 5 % im Jahr 2025.
  - *Vermutete Ursache:* unterschiedliche Grundgesamtheit (Markt). Für europäische Planung ist die Lesart der Pressemitteilung die passende.
  - *Beleglage:* Prognose ohne Methodik.
  - [Gartner 2026](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2026.md)

## Offene Fragen

- **Welche Grundgesamtheit gilt für Gartners Geopatriation-Prognose?**
  - Alle Unternehmen (E-Book) oder Europa und Naher Osten mit Ausgangswert unter 5 % (Pressemitteilung), siehe „Strittig“.
  - [Gartner 2026](../quellen/2026/11/2026-11-15-gartner-top-10-strategic-technology-trends-for-2026.md)
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
- **Was erlaubt die Tencent Hy License für Hy4 flash kommerziell und in der EU?**
  - Die Karte verweist nur auf die LICENSE-Datei, deren Inhalt noch nicht ausgewertet ist.
  - [Hy4 flash Model Card](../quellen/2026/11/2026-11-20-hy4-flash-tencent-hy4-flash-model-card.md)
- **Unter welcher Lizenz stehen Edge0-145B und die Cactus-Runtime?**
  - Edge0 nennt keine Lizenz.
  - Bei Mirage ist nur das Lizenzfeld des Modells bekannt, nicht die Lizenz des separaten Runtime-Repos.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
- **Unter welcher Lizenz steht Qwen3.8-27B selbst?**
  - Die Unsloth-Seite nennt keine Lizenz, die DSpine-Karte nur die Apache-2.0-Lizenz des Draft-Modells.
  - [Unsloth Qwen3.8-27B](../quellen/2026/11/2026-11-14-unsloth-qwen3-8-27b-quantizations-dynamic-v3-1-update.md), [DSpine for Qwen3.8-27B](../quellen/2026/11/2026-11-14-tencent-qwen3-8-27b-dspine-b16-dspine-for-qwen3-8-27b.md)
- **Unter welcher Lizenz steht GLM-5.3-Flash, und ist trn2.48xlarge in EU-Regionen verfügbar?**
  - Das Material zu TrnRT nennt Preise nur für us-east-2 und schweigt zu Modelllizenz und EU-Verfügbarkeit.
  - [TrnRT (Show HN)](../quellen/2026/11/2026-11-18-show-hn-trnrt-open-source-llm-inference-engine-for-aws-train.md)
- **Hat Qwen4-Max offene Gewichte, und über welche Anbieter und Regionen ist es nutzbar?**
  - Kommentare vermuten, dass es keine offenen Gewichte gibt und der Zugang nur über Qwen oder Partner läuft. Eine Lizenz ist nicht bestätigt.
  - [Qwen4-Max](../quellen/2026/11/2026-11-17-qwen4-max.md)
- **Verhält sich Qwen4-Max je nach Zugangsweg und Systemprompt anders bei politisch heiklen Fragen?**
  - Der informelle Test nennt weder Zugangsweg noch Systemprompt.
  - [Qwen4-Max](../quellen/2026/11/2026-11-17-qwen4-max.md)
- **Was regelt die Acceptable Use Policy von Inkling 2 Small, und in welchen Regionen hosten die Drittanbieter?**
  - Die Karte verlinkt die Policy ohne Inhalt und nennt weder Regionen noch Preise.
  - [Inkling 2 Small Model Card](../quellen/2026/11/2026-11-14-inkling-2-small-model-card-hugging-face.md)
- **Läuft LongCat-2.5 mit vertretbarem Aufwand auf NVIDIA-GPUs, und auf welchen Chips beruhen die Effizienzangaben?**
  - Die Card dokumentiert nur NPU-Deployment und nennt den Chiphersteller nicht.
  - [LongCat-2.5 Model Card](../quellen/2026/11/2026-11-14-longcat-2-5-model-card-meituan-longcat-longcat-2-5.md)
- **Braucht SenseNova-Loop-9B tatsächlich trust_remote_code=True, und läuft es mit vLLM, llama.cpp oder als GGUF?**
  - Das Erfordernis ist nur aus dem Tag custom_code geschlossen. Laufzeiten jenseits von transformers sind nicht genannt.
  - [SenseNova-Loop-9B](../quellen/2026/11/2026-11-19-sensenova-sensenova-loop-9b.md)
- **Wann laufen Projects-Threads lokal hinter dem eigenen Netzwerk?**
  - Angekündigt ist „coming very soon“, ein Datum fehlt.
  - [Claude Code Projects](../quellen/2026/11/2026-11-14-anthropic-upgrades-claude-code-projects-to-run-parallel-ai-w.md)
- **Welche Inhalte aus lokalen Dateien und Browsersitzungen landen bei Claude Cowork bei Anthropic, und gibt es EU-Betrieb?**
  - Die Demo behandelt weder Datenresidenz noch EU-Betrieb.
  - [Claude Cowork und Claude Code (Lektion)](../quellen/2026/11/2026-11-19-i-got-a-private-lesson-on-claude-cowork-claude-code.md)
- **An welchen Anbieter und welches Modell gehen bei Foolscap die nicht privaten Inhalte, und wo werden sie gespeichert?**
  - Die Zusage nennt nur, dass private Bücher an keine KI gehen. Anbieter, Modell und Speicherort fehlen.
  - [Foolscap (Show HN)](../quellen/2026/11/2026-11-20-show-hn-foolscap-a-writing-app-that-reads-your-book-and-neve.md)
- **Unter welcher Lizenz steht Mastra Factory, und welche Modelle und Sandbox-Anbieter setzt sie voraus?**
  - Der Beitrag nennt weder Lizenz noch Modelle, Sandbox-Anbieter oder EU-Hosting.
  - [Mastra Factory (Show HN)](../quellen/2026/11/2026-11-19-show-hn-mastra-factory-the-open-source-software-factory-we-u.md)
- **Nutzt Google AI Studio Eingaben im Free Tier zum Training, und wo werden die Daten verarbeitet?**
  - Die Demo nennt beides nicht.
  - [Google AI Studio (Demo)](../quellen/2026/11/2026-11-17-google-ai-studio-replaces-your-ai-tech-stack-full-demo.md)
- **Kommen die Windows-Daten zur Agent-Nutzung bei Microsoft an, und gilt das auch für EU-Installationen sowie Pro und Enterprise?**
  - Belegt sind nur das Einreihen in die Upload-Queue und die Werkseinstellung bei einer US-Home-Installation. Der Rollout-Umfang des Features ist unbekannt.
  - [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)
- **Verhindert das Abschalten optionaler Diagnosedaten die Erfassung tatsächlich?**
  - Der Autor hat den abgeschalteten Fall nicht selbst getestet.
  - [Windows-11-Telemetrie zu Coding-Agenten](../quellen/2026/11/2026-11-17-windows-11-is-collecting-data-on-which-coding-agents-and-dev.md)
- **Ab wann rechnet sich lokale Inferenz gegenüber API-Gebühren?**
  - Edge0 liefert keine Gesamtkostenrechnung für Hardware und Strom. Auch der Beitrag zu lokaler KI nennt hohe API-Kosten als Grund, aber keine Schwelle.
  - [Edge0-145B](../quellen/2026/11/2026-11-14-edge0-145b-frontier-ai-capabilities-on-your-own-computer.md), [I'm Obsessed With Local AI](../quellen/2026/11/2026-11-16-i-m-obsessed-with-local-ai-here-s-why.md)
- **Was kostet die gegenseitige Prüfung durch Modelle mehrerer Anbieter an Geld und Latenz?**
  - Die Quelle empfiehlt den Ansatz, lässt Kosten und Latenz aber offen.
  - [Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md)
- **Läuft Mirage nach dem Vorab-Download vollständig offline?**
  - Die Card beschreibt keinen Offline-Betrieb, ein eigener Test steht aus.
  - [Mirage (Cactus-Compute)](../quellen/2026/11/2026-11-14-mirage-cactus-compute-mirage.md)
- **Welchen Rechtsstatus haben US-gemeinfreie Trainingskorpora in der EU?**
  - Die Quelle weist nur auf mögliche Unterschiede hin und hat sie selbst nicht geprüft.
  - [DeepSeek V3 in Jax (Show HN)](../quellen/2026/11/2026-11-15-show-hn-deepseek-v3-in-200-lines-of-pure-jax.md)
- **Auf welche Veröffentlichung des FRC stützt sich die Warnung zu KI in der Abschlussprüfung?**
  - Der Artikel zitiert keine konkrete FRC-Publikation.
  - [KI-Agenten im KPMG-Prüfungstest](../quellen/2026/11/2026-11-19-ai-agents-ask-better-questions-than-kpmg-accountants-in-audi.md)
