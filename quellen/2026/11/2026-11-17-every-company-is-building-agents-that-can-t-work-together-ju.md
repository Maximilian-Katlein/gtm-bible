# Jede Firma baut Agenten, die nicht zusammenarbeiten können

> **Quelle:** [Every Company Is Building Agents That Can't Work Together - Justin Schroeder, Standard Agents](https://www.youtube.com/watch?v=3Krz7Rdd4JI) · Justin Schroeder, Standard Agents · Video (Konferenzvortrag, Kanal AI Engineer) · 2026-11-17
> **Sprecher verkauft:** Standard Agent Specification (Open Source) und Standard Agent Builder (Runtime, lokal oder als kostenpflichtige Cloud) · **Zielmarkt der Aussagen:** Unternehmen und Entwickler von KI-Agenten (01:29) · **Beweislage:** Thesen und eine Live-Demo des eigenen Produkts, keine unabhängigen Vergleiche.

## Worum es geht
Warum bauen Unternehmen weiter eigene, eng begrenzte Agenten, statt ein großes Modell mit MCP-Servern und Skill-Dateien zu füttern? Und wie lassen sich diese Agenten so bauen, dass sie zwischen Teams, Hosts und Modellen austauschbar bleiben? Der Vortrag richtet sich an Entwickler, die Agenten für Geschäftsprozesse bauen, und stellt dafür die eigene Spezifikation vor.

## Was man anwenden kann
1. **Agenten nach Geschäftsprozess schneiden, nicht nach Modell.** Schroeder nennt drei Gründe für dedizierte Agenten: Integration in tief eingebettete Prozesse, Vertrauen durch begrenzte Befugnisse und Wirksamkeit im Prozess (01:20). Beispiele sind Garantieansprüche und Einsatzplanung bei einem HVAC-Betrieb (01:40) oder Studienfinanzierung an Hochschulen (02:20). Prüffrage: Welcher Prozess muss wiederholbar und kontrollierbar laufen?

2. **Werkzeuge pro Agent hart begrenzen.** Ein Garantie-Agent wird durch ein Ereignis ausgelöst und bekommt nur Geräte-Lookup, Fotoanhang und Anspruch-Übermittlung (05:20). Begründung: Ein Agent, der alles kann, kann auch Unerwünschtes tun, etwa bei fehlgeschlagenem Login eigenmächtig ein neues Konto im Garantieportal anlegen (04:40). Gilt für jeden Agenten mit Schreibzugriff auf Fremdsysteme.

3. **Kleines Modell für die Einzelaufgabe statt großes Modell mit vielen Skills.** These: Ein Gmail-Agent schlägt einen Gmail-Skill auf einem Großmodell. Für eng gefasste Aufgaben reiche ein günstiges Modell wie DeepSeek V4.1 Flash (07:45). Bei so engen Aufgaben sei Überanpassung an den eigenen Test („Benchmaxing“) sogar erwünscht (06:50). Voraussetzung: eine eigene Evaluation der einen Aufgabe.

4. **Kosten-Ausreißer günstiger Modelle gezielt nutzen.** Im Projekt Model Zen Garden baute Hunyuan 3 (Tencent) 3D-Zengärten für 0,65 $, Opus 5.5 kostete 19,95 $ (18:45). Lehre laut Sprecher: Spezialisierte Agenten können solche Stärken einzelner Modelle ausnutzen. Belegt ist das nur für diese eine Aufgabe.

5. **Zuerst den Prompt optimieren, dann erst das Modell.** Schroeder sagt, Prompt-Tuning eines Agenten sei wirksamer als Fine-Tuning des Modells, und verweist auf ein Paper (im Transkript als „JEPA“ wiedergegeben) (08:20). Zahlen nennt er nicht. Als Arbeitsreihenfolge trotzdem prüfbar und billig.

6. **Kleine Agenten hierarchisch zusammensetzen.** Ein Domänen-Agent lässt sich als MCP-Server einem Großmodell anbieten oder unter einen Orchestrierungs-Agenten hängen (08:40). Wer in MCP-Tools selbst mehrstufige Inferenz einbaut, baut versehentlich ein zweites Agentensystem (10:05).

7. **Den Aufwand eines eigenen Harness realistisch ansetzen.** Modell, Systemprompt, Tools und Verlauf wirken simpel. Hinzu kommen Schleifen-Orchestrierung, parallele asynchrone Tool-Ausführung und Wiederaufnahme nach Fehlern (09:30). Eigenbauten verschiedener Teams sind untereinander nicht austauschbar (10:25).

8. **Modell pinnen, Fallback-Kette explizit festlegen.** In der Spezifikation wird jedes Modell exakt benannt, mit Fallback-Liste und hinterlegten Ein- und Ausgabepreisen (18:05). Das macht Verhalten und Kosten pro Agent nachvollziehbar.

9. **Worker und Reviewer als zwei Seiten eines Agenten.** Jede Konversation hat Seite A und B. Prompt gegen Prompt ergibt automatisierte Qualitätsprüfung: Der Reviewer beendet den Lauf über ein Tool wie approve_asset, eine Rundengrenze (maxSessionTurns: 40) verhindert Endlosschleifen (21:05, 22:48). Deterministische Handler ersetzen Modellaufrufe dort, wo nur weitergeleitet wird (22:38).

10. **Thread als Sandbox konfigurieren.** Jeder Thread hat eigene Nachrichten, Dateien, Key-Value-Speicher und Code-Ausführung. Internetzugriff lässt sich sperren, Imports per Whitelist erlauben (25:10). Ein Entscheidungsmodell kann prüfen, ob ein Kunde verärgert ist, und an einen Menschen eskalieren (26:25).

11. **Einen Agenten, mehrere Kanäle.** In der Demo läuft derselbe Garantie-Agent als Chat-Widget im Shop und zugleich als MCP-Server, damit externe Agenten (etwa aus ChatGPT heraus) direkt mit ihm sprechen (32:55). Verpackt wird er als NPM-Paket mit eigenen HTTP-, WebSocket- und OAuth-Endpunkten (26:45).

12. **Agenten aus Prozessdokumenten generieren lassen.** Claude Code erzeugte aus einer PDF-Prozessbeschreibung in 5:21 Minuten einen Akku-Garantie-Agenten für E-Bikes mit sechs Tools (30:40, 31:15). Bedingung: Der Prozess ist schriftlich und klar beschrieben, und die Spezifikation ist reiner TypeScript-Code, den Agenten schreiben und sofort ausführen können (15:40, 16:55).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 0,65 $ / 37 Mio. Tokens / 13 Min. | Hunyuan 3, Bau eines 3D-Zengartens, Model Zen Garden (18:45) | Eigenes Benchmark-Projekt, eine Aufgabe |
| 19,95 $ / 44,9 Mio. Tokens | Opus 5.5, gleiche Aufgabe (18:45) | wie oben |
| 30,28 $ | Fable 5.1, gleiche Aufgabe (18:45) | wie oben |
| 5 Min. 21 Sek. | Generierung des Garantie-Agenten mit Claude Code aus einer PDF (30:40) | Live-Demo, Herstellerangabe |
| 6 Tools | Umfang des generierten Agenten (31:15) | Demo |
| 854 ms, 2.665 Tokens, 94 % Cache | Ein Aufruf des Garantie-Agenten mit DeepSeek V4.1 Flash (32:05) | Dashboard des eigenen Produkts |
| 0,00070 $ | Gesamtkosten dieses Aufrufs inkl. Router-Gebühr (32:05) | Dashboard; die gezeigten Einzelposten summieren sich auf rund 0,00072 $ |
| 40 | maxSessionTurns im Worker-Reviewer-Beispiel (22:48) | Codefolie, Beispielwert |

## Wortlaute
- „agents are deterministic software that harness the non-deterministic results produced by models in pursuit of a desired objective“ (13:40). Die Agenten-Definition der Spezifikation.
- „if an agent can do anything, it might do anything and that is a liability“ (04:20). Kernargument für begrenzte Werkzeuge.
- `export default defineModel({ name: 'triage_fast', provider: 'openai', model: 'gpt-4o', fallbacks: ['gpt-4-turbo', 'gpt-3.5-turbo'] })` (18:05). Modell-Pinning mit Fallback-Kette.
- `defineAgent({ name: 'asset_subagent', maxSessionTurns: 40, sideA: { label: 'worker', prompt: 'asset_worker' }, sideB: { label: 'reviewer', prompt: 'asset_reviewer' } })` (22:48). Zwei Modelle in einem Agenten.
- `subagents: [{ agent: 'calendar_agent', as: 'work_calendar' }, { agent: 'calendar_agent', as: 'personal_calendar' }]` (23:05). Ein Agent, zweimal instanziiert mit getrennten Umgebungen.

## Grenzen und Widerspruch
- Der Vortrag ist Produktvorstellung. Die Demo-Zahlen stammen aus dem eigenen Dashboard, unabhängige Messungen fehlen.
- Dass Unternehmen generische Agenten für Kernprozesse ablehnen (03:20), wird als Erfahrung berichtet, nicht mit Kunden oder Zahlen belegt.
- Prompt-Tuning schlägt Fine-Tuning: nur ein beiläufiger Verweis auf ein Paper, dessen Name im Transkript unsicher ist.
- Der Zengarten-Vergleich deckt eine einzige, visuelle Aufgabe ab. Wie die Qualität bewertet wurde, bleibt offen.
- Spannung im Konzept: herstellerunabhängig sein, aber jeden Agenten an ein bestimmtes Modell koppeln (14:25). Portabel ist damit der Code, nicht zwingend das Verhalten nach einem Modellwechsel.
- Runtimes in Rust oder Go müssen TypeScript ausführen (33:25). Zu Leistung und Latenz gibt es keine Angaben.
- Sicherheit der Code-Ausführung in Threads wird nur über Netzsperre und Import-Whitelist beschrieben.
- Ob sich die Spezifikation neben MCP, A2A und Skills durchsetzt, ist offen. Der Vergleich mit den Browserkriegen (34:00) ist ein Bild, kein Beleg.
