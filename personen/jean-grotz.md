# Jean Grotz

Jean Grotz ist COO von Vercel und zeigt aus eigener Praxis, wie ein B2B-Unternehmen Vertrieb, Marketing und Produkt auf KI-Agenten umbaut: Agenten als Werkzeug im eigenen GTM und Agenten als neuer Käufer- und Empfehlungskanal.

Stand: 2026-11-15 · 1 Quelle

Verkauft: Vercel (Developer-Plattform für Deployments, Hersteller des Frameworks Next.js). Viele Beispiele zeigen das eigene Produkt in gutem Licht, etwa die steigende Nutzung durch Agenten oder Empfehlungen durch KI-Assistenten.

## Kernideen

### 1. Agent-Led Growth: Agenten wählen und nutzen das Produkt

Grotz beschreibt den GTM von Vercel als Mischung aus Sales-Led, Product-Led und früher Framework-Led Growth über Next.js. Der dritte Teil ist inzwischen durch Agent-Led Growth (ALG) ersetzt: Coding-Agenten entscheiden, welche Infrastruktur sie nutzen, und deployen selbst.

> that FLG part has been replaced with what we call ALG, which is agent led growth

*Entwicklung über Zeit: Früher trug Framework-Led Growth über Next.js das Wachstum, heute (Stand der Aufnahme, Quelle vom 2026-11-15) beschreibt Grotz Agent-Led Growth als dessen Nachfolger.*

Belege: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (07:05, 06:40)

### 2. Von Agenten empfohlen werden ist eine eigene Disziplin

Wer will, dass Claude, Cursor oder ChatGPT das eigene Produkt empfehlen, muss das messen und gezielt bearbeiten. Vercel setzt dafür auf umfangreiche Dokumentation, Vorlagen, Guides und Community-Signale aus Open Source, misst die Empfehlungshäufigkeit mit AEO-Evals je Anwendungsfall und schreibt Landing- und Preisseiten um, wenn bei gleicher Leistung ein Mitbewerber gewählt wird. Dafür hat das Marketing eine deutlich größere Content-Engineering-Funktion als ein typisches B2B-Team vor 24 Monaten.

> what's the frequency with which Vercel gets recommended across, you know, Claude, Cursor

Belege: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (07:35, 09:55, 12:00)

### 3. Agenten und Menschen sind gleichwertige Nutzer

Inhalte und Produktfunktionen werden doppelt ausgeliefert: jeder Inhalt als Markdown über llms.txt und als menschenlesbare Version, jede Funktion im Dashboard, in der CLI und über MCP. Eine Funktion gilt erst als releasefähig, wenn beide Nutzergruppen sie erreichen.

> you're not ready to ship until you're available both

Belege: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (12:00, 12:15)

### 4. Der Agent recherchiert, der Mensch positioniert

Recherche, Vorbereitung und Vorarbeit gehen an Agenten. Value Proposition, Hypothese pro Account und Thought Leadership bleiben beim Menschen. Inhalte für Agenten schreiben Agenten, Thought Leadership schreiben Menschen selbst.

> I don't really want Claude deciding my value prop

*Entwicklung über Zeit: Vercel gab dem Prospecting-Agenten zunächst volle Schreibrechte inklusive Value Proposition und nahm das wieder zurück. Seitdem kommt die Positionierung aus von Menschen gestalteten Vorlagen je Käufertyp (Quelle vom 2026-11-15).*

Belege: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (01:51, 12:00, 21:20)

### 5. Garbage in, garbage out: erst Standards, dann Agenten

Bevor Agenten eingesetzt werden, müssen Best Practices, Prozesse und Inhaltsstandards schriftlich festgelegt sein. Bei Vercel heißt das: hunderte Seiten internes Material von Product Marketing, genau zehn definierte Discovery-Fragen für BDRs und viel Datenvorarbeit in Snowflake und einem Semantic Layer.

> agents are garbage in, garbage out

Belege: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (23:45, 26:35, 39:05)

### 6. KI-Eigenbau braucht zentrale Steuerung

Lässt man Fachteams unkoordiniert Agenten bauen, entstehen Doppelungen, Schatten-CRMs und breit verteilte API-Schlüssel mit Supply-Chain-Risiko. Grotz setzt stattdessen auf ein kleines zentrales GTM-Engineering-Team.

> handing out API keys left and right which is quite problematic particularly for supply chain risk

Belege: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (36:40)

## Methoden und Abläufe

### Outbound mit Agenten nach Firmengröße
- Kleinere Zielkunden: E-Mail allein bucht die meisten Meetings.
- Enterprise und Fortune 500: Kombination aus E-Mail, Anruf und Social Outreach.
- Der Agent recherchiert, die Botschaft kommt aus menschlich gestalteten Vorlagen je Käufertyp.

> more companies need a collection of different types of outreach. So email, call, and basically social outreach

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (01:51, 02:40)

### Produktnutzung als Intent-Signal
1. Ein Entscheider legt selbst ein Konto an, etwa ein Fortune-500-CTO am Wochenende.
2. Ein Agent stößt Outreach an und kombiniert Recherche mit Vorlagen zu „Why now“ und „Why Vercel“.
3. Mails an C-Level gehen im Namen der COO raus und werden vor Versand persönlich gelesen.

> On a Sunday, a CTO of a Fortune 500 will create a Vercel account.

*Voraussetzung: ein Self-Service-Zugang, den auch Entscheider tatsächlich nutzen.*

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (03:21)

### Menschliche Hypothese vor KI-Outreach
Reps legen pro Account vor dem KI-gestützten Outreach eine eigene Hypothese fest. Ein Enterprise-Team verbesserte damit laut Grotz die Konversion deutlich.

> we have them actively put a hypothesis on the account... their conversion rates have meaningfully improved

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (21:20)

### AEO-Evals und Seiten-Iteration
1. Je Anwendungsfall messen, wie oft Claude, Cursor, OpenAI und andere Systeme das eigene Produkt empfehlen.
2. Fälle finden, in denen bei gleicher Leistung ein Mitbewerber gewählt wird.
3. Landing- und Preisseiten umschreiben, bis der Agent den Wert erfasst.

*Den Aufbau der Evals zeigt die Quelle nicht.*

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (09:55)

### Doppelte Auslieferung von Inhalten und Funktionen
- Jeder Inhalt: Markdown für LLMs über llms.txt plus menschenlesbare Version.
- Jede Funktion: Dashboard, CLI und MCP, sonst kein Release.

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (12:00, 12:15)

### Wissensbasis für den Sales-Agenten
Product Marketing hat hunderte Seiten internes Material geschrieben: Tonalität sowie die Value Proposition je Produkt in vier Längen (ein Satz, drei Sätze, ein Absatz, Essay).

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (23:45)

### Kampagnen-Agent im Marketing Ops
Aus strukturiertem Input erstellt ein von Marketing Ops gebauter Agent binnen 24 Stunden eine Kampagne mit Mails, Empfängerliste und Landingpage. Voraussetzung war viel Vorarbeit in Snowflake und ein Semantic Layer.

> we have a three-person MOPs team for, you know, the entire, uh, org

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (26:35)

### Interner Vertriebsagent „Index“
Übernimmt Recherche, Vorbereitung, Follow-up und Account-Planung und schiebt proaktiv Aufgaben an Reps, etwa wenn ein Deal in Phase 3 steht, ohne dass ein Economic Buyer kontaktiert wurde.

> you're in stage three, but you still haven't ever talked to an economic buyer

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (27:28)

### Vertriebsorganisation mit Agenten
- Mehr Reps pro Manager, weil Manager weniger Zeit mit Call-Aufnahmen und Forecasts verbringen.
- Quoten werden etwa alle sechs Monate angehoben.
- Bei sieben- bis achtstelligen Deals bleiben Manager aktiv auf mehreren Kundenebenen präsent.

> we're planning to increase our rep to manager ratio next year

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (28:55)

### Steuerung von KI-Eigenbau
Ein fünfköpfiges GTM-Engineering-Team baut zentral und startet jede Lösung mit genau einem Fachteam, statt jeden selbst bauen zu lassen.

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (36:40)

## Formulierungen und Formate

- **ALG, Agent-Led Growth:** Ergänzung zu SLG und PLG, ersetzt bei Vercel das frühere FLG (Framework-Led Growth).
- **„The average dollar value of a human touch“:** Kennzahl für KI-Wirkung im Vertrieb. Der durchschnittliche Dollarwert eines menschlichen Touchpoints bei gewonnenen Deals soll steigen, während die Zahl der Touches sinkt. Ergänzend: produktive Kundengespräche pro Rep und Woche.
- **„Agents are garbage in, garbage out“:** Begründung dafür, Standards vor dem Agenteneinsatz festzuschreiben.
- **„Not ready to ship until you're available both“:** Release-Kriterium für Mensch und Agent.
- **„Why now“ und „Why Vercel“:** die zwei Vorlagenbausteine im Enterprise-Outreach.
- **Value Proposition in vier Längen:** ein Satz, drei Sätze, Absatz, Essay.

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md) (03:21, 05:25, 07:05, 12:15, 23:45, 39:05)

## Zahlen, die sie nennt

| Zahl | Kontext | Zeit |
|---|---|---|
| 3 % → über 60 % | Anteil der von KI-Agenten ausgelösten Deployments auf Vercel, von Januar bis zur Aufnahme | 06:40 |
| 1 % → 10 % | Kennwert über ChatGPT, vermutlich Anteil der Sign-ups | 08:40 |
| 70 % | Anteil des Geschäfts über Agenten-Empfehlungen, Zuordnung zu Grotz unklar | 08:40 |
| 24 Monate | Vergleichszeitraum: Content Engineering heute deutlich größer als im typischen B2B-Team damals | 07:35 |
| 10 | definierte Discovery-Fragen für BDRs im ersten Gespräch | 39:05 |
| 24 Stunden | vom strukturierten Input zur fertigen Kampagne | 26:35 |
| 3 Personen | Marketing Ops für die ganze Firma | 26:35 |
| ca. 90 % | Anteil der Account-Pläne, den der Agent erstellt | 27:28 |
| ca. alle 6 Monate | Anhebung der Vertriebsquoten | 28:55 |
| 5 Personen | GTM-Engineering-Team | 36:40 |

Quelle: [Vercel COO zu KI-Agenten](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md)

## Wo Vorsicht geboten ist

*Alle Aussagen stammen aus einer einzigen Quelle und beruhen auf eigenen Daten von Vercel ohne offengelegte Methodik. Grotz spricht als COO eines Unternehmens, das von Agent-Led Growth direkt profitiert; Zahlen zur Agentennutzung sind daher auch Werbung für das eigene Produkt.*

- **3 % auf über 60 % Agenten-Deployments:** Das Jahr des Ausgangswerts nennt das Video nicht, eine Definition von „durch einen Agenten ausgelöst“ fehlt. Gilt nur für Developer-Infrastruktur, in der Coding-Agenten direkt deployen.
- **ChatGPT-Kennwert 1 % auf 10 %:** Das Transkript ist an dieser Stelle fehlerhaft („chat TBC sign offs“). Was genau gemessen wird, ist nicht eindeutig. Die 70 % Agenten-Empfehlungen lassen sich im Transkript nicht sicher Grotz zuordnen. Beides ist eine Behauptung ohne Beleg.
- **Konversionsverbesserung durch Account-Hypothesen:** Nur ein Team, keine konkreten Werte.
- **AEO-Evals:** Der Aufbau der Evals wird nicht gezeigt, die Methode ist so nicht nachbaubar.
- **24-Stunden-Kampagnen und 3-Personen-MOPs:** Nur mit sauberer Datenbasis (Snowflake, Semantic Layer) möglich. Ohne diese Vorarbeit nicht übertragbar.
- **Intent-Signale aus Produktnutzung:** Funktioniert nur bei Self-Service-Produkten, die Entscheider selbst ausprobieren.
- **Übertragbarkeit:** Viele Taktiken (Open-Source-Community, Dokumentation als Empfehlungshebel, MCP-Verfügbarkeit) setzen eine Entwickler-Zielgruppe voraus.

## Alle Quellen

- 2026-11-15 · [How to Get AI Agents to Recommend Your Business (Vercel COO)](../quellen/2026/11/2026-11-15-how-to-get-ai-agents-to-recommend-your-business-vercel-coo.md)
