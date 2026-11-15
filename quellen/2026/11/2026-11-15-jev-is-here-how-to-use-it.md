# Jev ist da. So setzt man es ein

> **Quelle:** [Jev is HERE. How to use it](https://www.youtube.com/watch?v=4mTLpuQpB80) · Greg Isenberg, Ryan Vogel (Open Code) · Video · 2026-11-15
> **Sprecher verkauft:** KI-Werkzeuge und Entwicklungs-Services von Open Code, dazu Hinweise auf das Vercel AI Gateway und den eigenen Kanal · **Zielmarkt der Aussagen:** SMB, Creator, Developer, Startups (01:58) · **Beweislage:** Live-Demos mit eigenen Zahlen, ein Kundenfall, keine Benchmarks gegen Alternativen.

## Worum es geht
Das Video stellt Jev vor, ein Klassifikator-Modell. Jev erzeugt keinen Text. Es verteilt Wahrscheinlichkeiten auf Antwortoptionen, die man vorher festlegt. Die Frage lautet: Für welche Entscheidungen in Geschäftsprozessen lohnt sich so ein schnelles, billiges Entscheidungsmodell statt eines LLM? Zielgruppe sind Entwickler, kleine Firmen und Gründer, die Eingangsströme wie Mails, Leads oder Tickets automatisch sortieren wollen.

## Was man anwenden kann
1. **Schema statt Prompt denken.** Man übergibt ein Eingabeobjekt und ein festes Ausgabeschema mit erlaubten Optionen (03:15). Jev wählt nur aus diesen Optionen und erfindet keine neuen Kategorien (11:20). Felder können auch Skalen von 0 bis 1 sein, etwa 0,31 oder 0,90 (10:30). Wer Jev einsetzt, muss die Entscheidungslogik also vorher vollständig als Optionen ausformulieren.

2. **Mails ohne Vorverarbeitung sortieren.** In der Demo gehen komplette Mailobjekte mit Betreff, Beschreibung, Text und Absender direkt an Jev (04:30). Das Schema hat vier Felder: Kategorie (Shopping, Work, Marketing, Finance, Security), Priorität (low bis urgent), Spam-Score als Prozentwert und die Wahrscheinlichkeit, dass eine manuelle Antwort nötig ist (04:50). Eine Kickstarter-Werbung bekommt hohen Spam-Score, eine Zahlungsbestätigung von Mercury niedrigen (05:25). Eine Mail mit dem Betreff „90% account violation possibility“ wird als antwortbedürftig erkannt (06:05).

3. **Inbound-Leads mit Schwellenwert priorisieren.** Eine Grafikdesign-Agentur bewertet Kontaktformular-Anfragen mit einem Feld „is good lead“ von 0 bis 1 (17:00). Anfragen ab 0,98 werden sofort bearbeitet. Bedingung: B2B-Dienstleister mit nennenswertem Formular-Eingang. Belegt ist das nur als einzelner Kundenfall ohne Ergebniszahlen.

4. **Alte Mailbestände auf verpasste Leads prüfen.** Dasselbe Schema lässt sich rückwirkend auf das Postfach anwenden, um übersehene Anfragen oder wertvolle Altkunden für eine erneute Ansprache zu finden (18:05). Das ist eine Idee der Sprecher, kein gezeigter Fall.

5. **Support-Tickets an Teams routen.** Jev entscheidet pro Ticket, welches Produktteam zuständig ist (18:45). Die Sprecher nennen etwa 200 Millisekunden pro Abfrage, unabhängig von der Schemagröße (19:15). Für Echtzeit-Routing ist das der eigentliche Vorteil gegenüber LLMs, die laut Sprecher bis zu 30 Sekunden brauchen können.

6. **Dreistufige Weiche bauen („AI Traffic Cop“).** Jev steht vor dem Prozess und entscheidet nach Konfidenz (19:40): hohe Konfidenz geht direkt an einen Menschen, mittlere an ein LLM zur Vorverarbeitung, sehr niedrige wird verworfen. So bezahlt man das langsame, teure LLM nur für die unklaren Fälle. Schwellenwerte für die Stufen nennen die Sprecher nicht.

7. **Geschäftsidee: teure Warteschlange suchen.** Das Muster für Gründer lautet: einen Betrieb mit einer teuren oder langsamen Eingangs-Queue finden und Jev davorsetzen (21:10). Beispiel ist ein Vermittler lokaler Dienstleistungen, der Anfragen wie „Einfahrt reinigen“ sofort einem passenden Anbieter zuordnet statt per Mail nachzufassen (21:30). Beides ist Konzept, nicht gezeigt.

8. **Transkripte nach Clip-Momenten bewerten.** Ein Video wird transkribiert, das Wort-Transkript geht mit Bewertungskriterien an Jev. Ergebnis in der Demo: 17 bewertete Momente in etwa 3 Sekunden, Füllwörter ausgeschlossen (24:10). Verarbeitet wurden 1,1 Millionen Tokens (24:55). Relevant für Content-Teams, die Webinare oder Podcasts zerlegen.

9. **Browser-Agent mit schnellen Einzelentscheidungen.** In einer Browser-Use-Demo wählt Jev einen Flug Zürich nach London in 7,1 Sekunden (25:40). Andere Browser-Agents bräuchten laut Sprecher eine bis drei Minuten. Gemessen wurde nur die eigene Demo.

10. **Zugang und Einstieg.** Direkt gibt es eine Warteliste, sofortiger Zugriff läuft über das Vercel AI Gateway und das Vercel AI Package (26:30). Für die Suche nach Einsatzfällen schlagen die Sprecher vor, einem KI-Agenten die Jev-Dokumentation zu geben und ihn nach täglichen Entscheidungs-Workflows im eigenen Betrieb zu fragen (26:45).

11. **Nicht für Finanzentscheidungen.** Ein Test mit minütlichen Kauf-, Halte- und Verkaufssignalen für Bitcoin lief schlecht (23:00). GPT-6 Astra schnitt besser ab, weil es Nachrichtenquellen einbeziehen konnte (23:30). Jev entscheidet nur auf Basis der übergebenen Eingabe, ohne Recherche und ohne sichtbares Reasoning (13:00).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1.700 Mails, 4,2 Mio. Input- und 0,5 Mio. Output-Tokens, 18 Cent | Klassifikation des Demo-Postfachs in wenigen Sekunden (06:25) | eigene Daten; Wortlaut lässt offen, ob 18 Cent gesamt oder pro Mail gemeint sind |
| ca. 200 ms | Latenz pro Abfrage, unabhängig vom Schema (19:15) | eigene Daten |
| bis 30 s | Antwortzeit herkömmlicher LLMs (19:15) | Behauptung ohne Beleg |
| 0,98 | Schwelle für sofortige Lead-Bearbeitung (17:00) | Kundenfall |
| 17 Momente, ca. 3 s, 1,1 Mio. Tokens | Clip-Scoring eines Videotranskripts (24:10, 24:55) | eigene Daten |
| 7,1 s vs. 1 bis 3 min | Flugauswahl per Browser-Agent (25:40) | eigene Daten gegen Schätzung |
| 5 USD für 2 Tage, 10 USD für ca. 3 Monate | Startguthaben im intensiven bzw. normalen Testbetrieb (16:30) | eigene Daten, Schätzung |
| ca. 1/1.000 Cent | Kosten einer einzelnen Testabfrage (27:50) | eigene Daten, Schätzung |

## Wortlaute
- „How do I find a business with an expensive queue of incoming information and then just put Jev at the front of that queue.“ (21:10) Die Kurzform des vorgeschlagenen Gründermusters.
- „what sort of workflows do I do on the daily basis that could benefit from a decision maker like Jev?“ (26:45) Prompt an einen KI-Agenten, um Einsatzfälle im eigenen Betrieb zu finden.
- „I would not put this model in front of like your stock portfolio“ (23:00) Die Warnung nach dem gescheiterten Bitcoin-Test.

## Grenzen und Widerspruch
- **Keine Vergleichsbasis.** Es gibt keine Benchmarks oder Fehlerraten gegen Open-Weight-Klassifikatoren, kleine feinjustierte Modelle oder strukturierte Ausgaben klassischer LLMs. Ob Jev besser klassifiziert, bleibt offen. Gezeigt ist nur, dass es schnell und billig ist.
- **Kostenangaben passen nicht zusammen.** 18 Cent für 1.700 Mails ergeben rund 0,01 Cent pro Mail, also das Zehnfache der genannten 1/1.000 Cent pro Testabfrage. Ist der Wortlaut „18 cents for each one“ wörtlich gemeint, läge der Preis noch weit höher. Vor Einsatz eigene Kosten messen.
- **Architektur unbekannt.** Wie Jev technisch arbeitet und wo es läuft, wird nicht offengelegt. Für Datenschutz- oder Souveränitätsfragen fehlt damit jede Grundlage; Zugang läuft über einen US-Anbieter (Vercel).
- **Herkunftsbehauptung ungeprüft.** Dass der Entwickler Diogo Almada durch seine Forschung ChatGPT mitgebaut habe (00:03), wird nicht belegt.
- **Vertrauensfrage ohne Reasoning.** Die Sprecher räumen ein, dass Nutzer einem Modell ohne nachvollziehbare Begründung misstrauen (13:00). Für Entscheidungen mit Folgen gegenüber Kunden braucht es daher Stichproben und menschliche Prüfung.
- **Ergebnisoffenes Experiment.** Der Versuch, über A bis Z als Kategorien Text zu erzeugen (14:20), wird gezeigt, ein belastbares Ergebnis aber nicht berichtet.
- **Interessenlage.** Open Code verkauft Entwicklungs-Services, das Video bewirbt stellenweise das Vercel Gateway und den eigenen Kanal. Die Einsatzideen für Lead-Reaktivierung, Ticket-Routing und Dienstleistungs-Matching sind Vorschläge, keine Fälle.
