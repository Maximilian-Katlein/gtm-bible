# Wie man KI-Agenten dazu bringt, das eigene Unternehmen zu empfehlen (Vercel COO)

> **Quelle:** [How to Get AI Agents to Recommend Your Business (Vercel COO)](https://www.youtube.com/watch?v=Z0IjcAYzYBQ) · Jean Grotz, Vercel · Video (Podcast „Marketing Against the Grain“) · 2026-11-15
> **Sprecher verkauft:** Cloud- und Deployment-Plattform für Entwickler sowie Infrastruktur für agentische Anwendungen · **Zielmarkt der Aussagen:** Enterprise und schnell wachsende Startups, Developer Tools (03:00, 13:28) · **Beweislage:** durchweg Aussagen über eigene Zahlen und Abläufe, extern nicht überprüft, ohne Methodik.

## Worum es geht
Wie ein Developer-Tool-Anbieter seinen Go-to-Market umbaut, wenn KI-Agenten zugleich Kunden (sie lösen Deployments aus), Empfehlungsgeber (sie wählen Anbieter aus) und Mitarbeiter (sie recherchieren, schreiben, planen) sind. Relevant für B2B-Software-Firmen mit Entwickler-Zielgruppe und Enterprise-Vertrieb. Für Firmen ohne technische Käufer oder ohne saubere Datenbasis gelten viele Punkte nur eingeschränkt.

## Was man anwenden kann
1. **Agent recherchiert, Vorlage positioniert.** Vercel gab dem Prospecting-Agenten anfangs volle Schreibrechte, auch für die Value Proposition, und nahm das zurück (01:51). Heute recherchiert der Agent, die Botschaft kommt aus von Menschen gestalteten Vorlagen je Käufertyp (02:15). Der Agent qualifiziert Inbound, recherchiert Outbound und versucht, ein Meeting mit einem Rep zu buchen (02:30).

2. **Kanalmix nach Firmengröße.** Bei kleineren Zielkunden kommen die meisten Meetings per E-Mail zustande. Je größer das Unternehmen, desto mehr braucht es E-Mail, Anruf und Social Outreach zusammen (02:40).

3. **Produktnutzung als Intent-Signal.** Legt ein CTO eines Fortune-500-Unternehmens am Wochenende ein Konto an, erkennt der Agent das und stößt Outreach an (03:21). Die Mail kombiniert Agenten-Recherche mit Vorlagen zu „Why now“ und „Why Vercel“ (03:40). Gilt dort, wo Entscheider das Produkt selbst ausprobieren.

4. **Mensch prüft C-Level-Mails.** CTO-Outreach geht im Namen von Jean Grotz raus. Grotz liest jede dieser Mails vor dem Versand (04:15). Ziel insgesamt: BDRs schreiben weniger Mails und telefonieren mehr (04:56).

5. **Eine Kennzahl für KI-Wirkung im Vertrieb.** Gemessen wird der durchschnittliche Dollarwert eines menschlichen Touchpoints bei gewonnenen Deals. Er soll steigen, während die Zahl der Touches sinkt (05:25). Zusätzlich zählt Vercel wöchentlich produktive Kundengespräche je AE, Solution Architect und BDR (17:21).

6. **Für Agenten auffindbar sein.** Vercel investiert dauerhaft in Dokumentation, Vorlagen und Guides, die Agenten bei der Websuche verarbeiten (07:35). Dazu kommen Community-Signale von Millionen Open-Source-Entwicklern, die über die Software sprechen (07:50). Das Marketing hat dafür eine deutlich größere Content-Engineering-Funktion als ein typisches B2B-Team vor 24 Monaten, plus ein Developer-Experience-Team (08:15).

7. **Empfehlungsrate messen und Ursachen beheben.** Mit AEO-Evals misst Vercel, wie oft es in Claude, Cursor, OpenAI und anderen Systemen je Anwendungsfall empfohlen wird (09:55). Wird bei gleicher Leistung ein Mitbewerber gewählt, prüft das Team Landing- und Preisseiten und schreibt Erklärungen um, bis der Agent den Wert erfasst (10:15).

8. **Jeder Inhalt doppelt.** Zu jedem veröffentlichten Inhalt gibt es eine Markdown-Version für LLMs (llms.txt) und eine Version für Menschen (12:00). Inhalte für Agenten schreiben Agenten. Thought Leadership für Menschen schreiben Menschen selbst (22:00).

9. **Kein Release ohne CLI und MCP.** Eine Funktion gilt erst als fertig, wenn sie im Dashboard, in der CLI und über MCP verfügbar ist (12:15). So können Menschen und Agenten sie gleichermaßen nutzen.

10. **PLG nach oben verkaufen.** Bauen Entwickler in Konzernen eigenständig Apps mit Cursor oder Claude auf Vercel, nutzt der Vertrieb das als Anlass für ein Gespräch mit CTO oder CIO über Security und Governance (14:00). Bei Startups geht es um den Ausbau von einzelnen Funktionen zu allen Workloads („wall to wall“) (13:28).

11. **Erst die menschliche Hypothese, dann der Agent.** In einem Experiment legte ein Sales-Team vor dem KI-Outreach eine eigene Hypothese pro Account fest. Die Konversion stieg laut Grotz deutlich (21:20), Zahlen nannte Grotz nicht.

12. **Agenten-Stack im Vertrieb.** Ein Agent baut Account-Pläne zu etwa 90 Prozent, der Rep ergänzt die Hypothese (18:00). Ein Agent fasst Gespräche zusammen, zieht drei Aufgaben heraus und entwirft die Follow-up-Mail (18:25). Ein Agent bereitet Termine mit Historie, offenen Punkten und Agenda vor (18:40). „Index“ schiebt proaktiv Aufgaben, etwa wenn in Phase 3 noch kein Economic Buyer gesprochen wurde (27:28).

13. **Wissensbasis für den Sales-Agenten.** Product Marketing hat hunderte Seiten interne Dokumentation geschrieben: Tonalität und Value Proposition je Produkt in Ein-Satz-, Drei-Satz-, Absatz- und Essay-Länge (23:45).

14. **Ops-Agenten auf sauberen Daten.** Der Marketing-Ops-Agent erstellt aus strukturiertem Input binnen 24 Stunden eine Kampagne mit Mails, Empfängerliste und Landingpage (25:45). Der RevOps-Agent (im Transkript „Ravoah“) erledigt Routineänderungen wie Account-Übertragungen, prüft, ob die Änderung sicher ist, und eskaliert sonst (27:00). Voraussetzung war viel Vorarbeit in Snowflake und einen Semantic Layer (26:45).

15. **Organisation anpassen.** Vercel will die Zahl der Reps pro Manager erhöhen, weil weniger Zeit für das Abhören von Gong-Calls nötig sei (28:55). Bei sieben- bis achtstelligen Deals müssen Manager trotzdem selbst auf mehreren Ebenen beim Kunden präsent sein (29:25). Quoten hob Grotz seit Amtsantritt etwa alle sechs Monate an (32:40).

16. **Interne Tools per Pull-Strategie.** Ein fünfköpfiges GTM-Engineering-Team arbeitet eng mit einem Team an einer Lösung und skaliert dann (34:00). Ergebnis unter anderem: ein eigenes Headless-Front-End für das CRM mit laut Grotz 100 Prozent täglicher Nutzung (36:00). Ohne Steuerung bauen sonst zehn Leute denselben Agenten, und API-Schlüssel werden breit verteilt (36:40).

17. **Prozess dokumentieren, bevor Agenten starten.** Agenten sind „garbage in, garbage out“ (39:05). Beispiel: genau zehn festgelegte Discovery-Fragen für BDRs (39:25).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 3 % auf über 60 % | Anteil der Vercel-Deployments, die ein Agent auslöst, von Januar bis Aufnahme (Jahr im Video nicht genannt) | eigene Daten, ohne Methodik (06:40) |
| 1 % auf 10 % | vermutlich Anteil der Sign-ups über ChatGPT; Transkript unklar („chat TBC sign offs“) | eigene Daten (08:40) |
| 70 % | Anteil des Geschäfts über Agenten-Empfehlungen; im Transkript unklar, ob Moderator fragt oder Grotz bestätigt | unklar (08:40) |
| 90 % | Anteil eines Account-Plans, den der Agent erstellt | eigene Einschätzung (18:00) |
| 10 bis 15 | Kundentermine pro Woche von Grotz, 2 bis 3 CTOs pro Tag | eigene Angabe (19:00) |
| 3 Personen | gesamtes Marketing-Ops-Team | eigene Angabe (26:35) |
| 24 Stunden | Zeit vom Input zur fertigen Kampagne beim MOPs-Agenten | eigene Angabe (25:45) |
| 5 Personen | GTM-Engineering-Team | eigene Angabe (34:00) |
| 100 % | tägliche aktive Nutzung des CRM-Front-Ends | eigene Angabe (36:00) |
| alle 6 Monate | Anhebung der Vertriebsquoten über 18+ Monate | eigene Angabe (32:40) |
| 10 | Discovery-Fragen für BDRs | eigene Angabe (39:25) |

## Wortlaute
- „I don't really want Claude deciding my value prop“ (01:51). Warum die Botschaft beim Menschen bleibt.
- „anytime we're shipping content, we ship a markdown version in LLM.txt as well as a human readable version“ (12:00). Die Regel für doppelte Veröffentlichung.
- „you're not ready to ship until you're available both“ (12:15). Release-Kriterium für Mensch und Agent.
- „you're in stage three, but you still haven't ever talked to an economic buyer“ (27:28). Beispiel für einen proaktiven Hinweis des Sales-Agenten.

## Grenzen und Widerspruch
- Alle Zahlen sind Selbstauskünfte von Vercel. Es gibt keine Methodik zu den AEO-Evals, keine Prompts, keine Messbasis für die Deployment-Quote.
- Die Übertragbarkeit ist begrenzt: Vercel verkauft an Entwickler, die über Agenten wie Cursor und Claude direkt Infrastruktur auswählen und deployen. Für Branchen, in denen Agenten nicht kaufen oder deployen, sind 60 Prozent oder 70 Prozent kein Maßstab.
- Agenten lösen Deployments auch dann aus, wenn ein Mensch den Agenten steuert. Die 60 Prozent sagen also etwas über den Weg, nicht über die Kaufentscheidung.
- Das Hypothesen-Experiment nennt keine Konversionswerte und betrifft nur ein Team.
- Governance gegen Schatten-CRMs und verstreute API-Schlüssel wird benannt, aber nicht technisch erklärt.
- Der Begriff „Experimental Run Rate Revenue“ (16:40) beschreibt hohe Enterprise-Ausgaben ohne mehrjährige Verträge. Das ist eine Branchenbeobachtung ohne Beleg und zugleich ein Hinweis, dass ein Teil des Wachstums bei Plattformen wie Vercel weniger stabil sein könnte.
- Dass Ops-Agenten funktionieren, setzt laut Grotz eine saubere Datenbasis voraus. Wer die nicht hat, sollte die Ergebnisse nicht erwarten.
