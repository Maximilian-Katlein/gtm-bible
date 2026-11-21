# Justin Schroeder

Gründer von Standard Agents. Man hört Schroeder zu, um zu verstehen, warum Unternehmen trotz MCP und Skill-Dateien eng zugeschnittene Prozess-Agenten bauen und wie sich solche Agenten mit begrenzten Befugnissen, günstigen Modellen und einer gemeinsamen Runtime-Spezifikation sauber konstruieren lassen.

Stand: 2026-11-17 · 1 Quelle

Verkauft: Standard Agents, Anbieter der Standard Agent Specification (standardagentspec.org) und der im Vortrag vorgeführten Agenten-Plattform mit Admin-Dashboard. Die gezeigten Kosten enthalten eine Router-Gebühr, die Plattform leitet also Modellaufrufe weiter. Fast alle technischen Empfehlungen auf dieser Seite beschreiben zugleich das eigene Produkt.

## Kernideen

### 1. Dedizierte Agenten schlagen immer mehr Skills im Großmodell

Schroeder argumentiert, dass Unternehmen weiter eigene Agenten bauen, statt einem Großmodell nur Tools und Skills zu geben. Er nennt drei Gründe: Integration in tief eingebettete Geschäftsprozesse, Vertrauen durch begrenzte Befugnisse und Wirksamkeit im konkreten Prozess.

> there's three primary reasons why people are still building agents

Daraus folgt die Empfehlung, eng gefasste Einzelaufgaben mit einem kleinen, günstigen Modell (im Beispiel DeepSeek V4.1 Flash) in einem eigenen Agenten zu lösen.

> a Gmail agent beats a Gmail skill

Dazu passt die Umdeutung von Benchmark-Optimierung: Bei Großmodellen ein Problem, bei einem Agenten für genau eine Aufgabe erwünscht, weil die Evaluation dort die Wirksamkeit im eigenen Prozess misst.

> within an agent that is fine-tuned for a very specific task, that benchmaxing is actually a positive.

Ebenso gilt: Herstellerunabhängigkeit bei der Infrastruktur, aber feste Bindung jedes Agenten an das Modell, mit dem er am besten funktioniert.

> An individual agent is almost always best when it's paired with a specific model.

Belege: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (01:20, 06:50, 07:45, 14:25)

### 2. Begrenzte Befugnisse schaffen Vertrauen, unbegrenzte sind Haftung

Ein Agent, der alles darf, tut im Fehlerfall womöglich etwas Unerwünschtes. Schroeders Anekdote: Ein Agent legt eigenmächtig ein neues Konto im Garantieportal an, statt abzubrechen.

> if an agent can do anything, it might do anything and that is a liability

Die Gegenmaßnahme zieht sich durch den ganzen Vortrag: Prozess-Agenten bekommen nur die Tools, die der Prozess braucht, und laufen in einer Sandbox pro Thread mit sperrbarem Internetzugriff und Import-Whitelist.

Belege: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (04:20, 05:20, 25:10)

### 3. Für die Agenten-Runtime fehlt ein Standard

Schroeder ordnet das Ökosystem in Schichten: Für Tools gibt es MCP, für Prompts Skills und AGENTS.md, für Agent-zu-Agent-Kommunikation A2A und ACP, für Zahlungen X402. Für den Harness selbst gebe es nichts.

> nothing for the harness itself.

Wer den Harness selbst baut, unterschätzt laut Schroeder den Aufwand: Schleifen-Orchestrierung, parallele asynchrone Tool-Ausführung und Wiederaufnahme nach Fehlern. Die Eigenbauten verschiedener Teams passen dann nicht zusammen. Wer stattdessen Inferenz in MCP-Tools packt, baut unbemerkt ein zweites Agentensystem.

> all of a sudden you've recreated another agent system just within MCP.

Seine Antwort darauf ist das eigene Produkt, die Standard Agent Specification.

Belege: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (09:30, 10:05, 11:40)

### 4. Agenten sind deterministische Software um ein nicht-deterministisches Modell

Die Definition aus der Spezifikation trennt klar zwischen dem Modell als unberechenbarem Teil und dem Agenten als berechenbarer Hülle.

> agents are deterministic software that harness the non-deterministic results produced by models in pursuit of a desired objective.

Konsequent weitergedacht: Schritte ohne Urteilsbedarf laufen als deterministische Handler ganz ohne Modellaufruf, Modelle und Fallbacks werden fest im Code gepinnt, und Prüfschritte sind fest in den Ablauf eingebaut.

Belege: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (13:40, 18:05, 22:38, 22:48)

## Methoden und Abläufe

**Prozess-Agent zuschneiden**
1. Den Agenten durch ein konkretes Ereignis auslösen, etwa einen eingehenden Garantiefall.
2. Nur die nötigen Tools vergeben, beim Garantie-Agenten etwa Geräte-Lookup, Fotoanhang und Anspruch-Übermittlung.
3. Ein kleines, günstiges Modell wählen und für genau diese Aufgabe evaluieren.

> that agent has very specific tools like looking up equipment, attaching photos, submitting a claim.

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (05:20, 07:45). Bedingung: B2B-Prozessautomatisierung mit klar abgegrenzter Aufgabe und eigener Evaluation.

**Erst den Prompt tunen, dann das Modell**
Bevor in Fine-Tuning investiert wird, den Systemprompt des Agenten optimieren. Schroeder hält das für wirksamer und verweist auf ein Paper, nennt aber keine Zahlen.

> fine tuning the prompt of an agent, than fine tuning a model.

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (08:20)

**Modelle pinnen und Fallback-Kette festlegen**
Pro Agent ein exaktes Modell festlegen, dazu eine explizite Fallback-Kette sowie Ein- und Ausgabepreise im Code. So bleiben Verhalten und Kosten nachvollziehbar. Beispiel aus der Spezifikation: `defineModel({ name: 'triage_fast', provider: 'openai', model: 'gpt-4o', fallbacks: ['gpt-4-turbo', 'gpt-3.5-turbo'] })`.

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (18:05)

**Worker und Reviewer im selben Agenten**
Seite A arbeitet, Seite B prüft und beendet den Lauf über ein Freigabe-Tool. Eine Rundengrenze (im Beispiel 40) verhindert Endlosschleifen: `maxSessionTurns: 40, sideA: { label: 'worker', ... }, sideB: { label: 'reviewer', ... }`.

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (22:48). Bedingung: automatisierte Erzeugung mit Prüfschritt.

**Deterministische Handler für Relay-Schritte**
Reine Weiterleitungsschritte ohne Modellaufruf umsetzen. Die Spezifikation sieht In-Order-Zustellung pro Thread und null LLM-Kosten vor („Zero model calls“).

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (22:38)

**Thread als Sandbox**
Jeder Thread bekommt eigene Dateien, Key-Value-Speicher und Code-Ausführung. Internetzugriff lässt sich sperren, Imports laufen nur über eine Whitelist.

> You can even say you don't have access to the internet

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (25:10)

**Agent aus Prozessdokument generieren lassen**
In der Live-Demo erzeugte Claude Code aus einer PDF-Prozessbeschreibung einen Akku-Garantie-Agenten für E-Bikes mit sechs Tools (u. a. `check_battery`, `escalate_to_lead`, `ship_replacement`) auf DeepSeek V4.1 Flash.

> It took 5 minutes and 21 seconds in order to produce this agent.

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (30:40). Bedingung: schriftlich dokumentierter Prozess.

**Ein Agent, zwei Zugänge**
Denselben Agenten parallel als Chat-Widget auf der Website und als MCP-Server bereitstellen. So können auch Agenten der Kunden, etwa aus ChatGPT heraus, direkt mit ihm sprechen.

> expose the same agent because it's a standard as an MCP server.

Quelle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (32:55). Bedingung: Kundenservice-Prozesse mit Web-Frontend.

## Formulierungen und Formate

- **„a Gmail agent beats a Gmail skill“**: Kurzformel für die These, dass ein dedizierter Agent einer Skill-Erweiterung im Großmodell überlegen ist (07:45).
- **„if an agent can do anything, it might do anything“**: Begründung für begrenzte Tool-Sets (04:20).
- **„benchmaxing is actually a positive“**: Umdeutung von Benchmark-Optimierung für Einzelaufgaben-Agenten (06:50).
- **„nothing for the harness itself“**: Schroeders Positionierung der Lücke im Standard-Stapel (11:40).
- **Agenten-Definition**: „deterministic software that harness the non-deterministic results produced by models“ (13:40).
- **Format Live-Build**: Prozessdokument rein, lauffähiger Agent raus, mit Stoppuhr und Kosten-Dashboard als Beweisführung (30:40, 32:05).

Quelle für alle: [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md)

## Zahlen, die sie nennt

| Zahl | Kontext | Belegart | Quelle |
|---|---|---|---|
| 0,65 $ (37 Mio. Tokens, 13 Minuten) | 3D-Zengarten mit Hunyuan 3 (Tencent), Projekt Model Zen Garden | eigene Daten | [Every Company Is Building Agents](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) (18:45) |
| 19,95 $ | dieselbe Aufgabe mit Opus 5.5 | eigene Daten | ebd. |
| 30,28 $ | dieselbe Aufgabe mit Fable 5.1 | eigene Daten | ebd. |
| 5:21 Minuten | Claude Code generiert Garantie-Agenten aus PDF | Herstellerangabe | ebd. (30:40) |
| 854 ms, 2.665 Tokens, 94 % Cache-Treffer, 0,00070 $ | ein Aufruf des Demo-Agenten auf DeepSeek V4.1 Flash, inkl. Router-Gebühr | Herstellerangabe | ebd. (32:05) |
| 40 Runden | Rundengrenze im Worker-Reviewer-Beispiel | Herstellerangabe | ebd. (22:48) |

> Hunyuan 3 was spectacular at producing 3D gardens at a fraction of the cost

## Wo Vorsicht geboten ist

*Interessenkonflikt: Schroeder verkauft die Standard Agent Specification und die Plattform, mit der die Demo läuft. Die Diagnose „für den Harness gibt es keinen Standard“ und die Lösung kommen aus derselben Hand.*

*Die Kernthesen (drei Gründe für eigene Agenten, „Gmail-Agent schlägt Gmail-Skill“, Prompt-Tuning vor Fine-Tuning) sind im Vortrag Behauptungen ohne Beleg. Für Prompt-Tuning wird ein Paper erwähnt, aber weder benannt noch mit Zahlen unterlegt.*

*Der Zengarten-Vergleich ist ein einzelner Benchmark mit einer visuellen Aufgabe. Wie die Qualität bewertet wurde, erklärt Schroeder nicht. Als allgemeine Aussage über Modellkosten taugt er nicht.*

*Die Demo-Zahlen (5:21 Minuten Generierung, 0,00070 $ pro Aufruf) stammen aus einem einzigen Lauf im eigenen Dashboard. Sie zeigen den günstigsten Fall, nicht den Durchschnitt im Betrieb.*

*Das Code-Beispiel zum Modell-Pinning nennt ältere Modelle (gpt-4o, gpt-3.5-turbo). Es illustriert die Syntax und ist keine Modellempfehlung.*

*Zur Sicherheit nennt der Vortrag nur Sandbox, Internetsperre und Import-Whitelist. Rechteverwaltung, Audit oder Prompt-Injection-Schutz kommen nicht vor.*

*Alle Kernideen stammen aus einer einzigen Quelle. „Wiederkehrend“ heißt hier: mehrfach im selben Vortrag, nicht über mehrere Auftritte hinweg.*

## Alle Quellen

- 2026-11-17 · [Every Company Is Building Agents That Can't Work Together (Justin Schroeder, Standard Agents)](../quellen/2026/11/2026-11-17-every-company-is-building-agents-that-can-t-work-together-ju.md) · Learnings L-20261117-062 bis L-20261117-080
