# United Airlines verbietet KI-Agenten, Flüge im Namen von Reisenden zu buchen

> **Quelle:** [United Airlines bans AI agents from booking flights on behalf of travelers](https://www.cbsnews.com/news/united-airlines-bans-ai-agents-booking-flights/) · CBS News (Kris Van Cleave, Redaktion Alain Sherter), zitierter Analyst Henry Harteveldt (Atmosphere Research Group), dazu die [Hacker-News-Diskussion](https://news.ycombinator.com/item?id=50458900) · Artikel mit Diskussion · 2026-11-13
> **Sprecher verkauft:** United verkauft Flugtickets und das Vielfliegerprogramm MileagePlus; CBS und der Analyst verkaufen nichts im Artikel · **Zielmarkt der Aussagen:** Fluggäste (B2C) und indirekter Vertrieb über Reisebüros und Aggregatoren · **Beweislage:** Unternehmensaussagen und Analystendeutungen ohne Vorfall, ohne Vorschrift, ohne Kostenzahlen.

## Worum es geht
Ein Anbieter mit eigenem Direktvertrieb sperrt persönliche KI-Agenten von Drittanbietern aus Buchung und Kontoverwaltung aus. Die Quelle zeigt, welche Begründungen ein Unternehmen dafür nennt, welche Motive Außenstehende vermuten und warum die Durchsetzung umstritten ist. Relevant ist das für alle, die Agenten bauen, die in fremden Shops handeln, und für Anbieter, die entscheiden müssen, ob sie Agenten als Kanal öffnen oder sperren.

## Was man anwenden kann
1. **Agenten-Politik nach Handlung trennen, nicht pauschal.** United unterscheidet faktisch drei Ebenen: Suche, Buchung mit Zahlungsdaten und Check-in. Für den Check-in führt United ein rechtliches Argument an (persönliche Bestätigung zum Gepäckinhalt), für die Buchung ein Sicherheitsargument. Wer eine eigene Richtlinie schreibt, sollte je Handlung festlegen, was erlaubt ist, statt nur „Agenten verboten“ zu formulieren.

2. **Geteilte Zugangsdaten als eigentliches Risiko benennen.** Uniteds Kernargument: Kunden geben einem Drittanbieter-Assistenten ihre Login- und Zahlungsdaten, und der Agent kann ungewollt kaufen, das Konto ändern oder Meilen ausgeben. Für Agenten-Entwickler folgt daraus: Lösungen mit delegiertem, eingeschränktem Zugriff statt Passwortweitergabe sind das Argument, das solche Sperren entkräften könnte. Belegt ist das in der Quelle nicht, es ist die logische Gegenposition.

3. **„Autorisiert“ definieren, bevor man sperrt.** United sperrt nur „unauthorized, third-party personal AI agents“, sagt aber nicht, was autorisiert wäre. Wer eine solche Regel einführt, lässt ohne Definition offen, ob Partnerintegrationen oder eigene Agenten erlaubt sind. Das erzeugt Unsicherheit bei Partnern und Kunden.

4. **Sperren oder Öffnen als strategische Kanalentscheidung behandeln.** Der Artikel stellt United und Southwest gegenüber: Southwest macht sein Flugangebot für ChatGPT-Nutzer sichtbar. Laut Analyst will United keinen weiteren, womöglich mächtigeren Intermediär neben Google, Metasuchen und Online-Reisebüros. Für B2C-Anbieter mit starkem Direktvertrieb ist das die Kernabwägung: Kontrolle über Kundenkontakt und Preis gegen Reichweite in einem neuen Kanal.

5. **Bei Agentenprodukten mit Sperren rechnen.** In der Diskussion berichtet siliconc0w, nach einer Amazon-Sperre einen eigenen Browser-Proxy für Agenten gebaut zu haben. Wer Agenten für Käufe in fremden Shops baut, sollte davon ausgehen, dass große Händler aussperren, und die Abhängigkeit vom Wohlwollen des Händlers in die Produktplanung aufnehmen. Ob Umgehung rechtlich oder vertraglich zulässig ist, behandelt die Quelle nicht.

6. **Durchsetzbarkeit realistisch einschätzen.** Mehrere Kommentatoren halten die Sperre technisch für schwer durchsetzbar: Agenten mit Computer Use bedienen den Browser wie ein Mensch, lokale Modelle entziehen sich Plattformvorgaben. Durchsetzbar sei vor allem, dass große Anbieter ihre eigenen Agenten selbst begrenzen. Eine Sperre wirkt also eher über Haftung und Nutzungsbedingungen als über Technik.

7. **Preisdifferenzierung als mögliches Motiv prüfen.** Der meistdiskutierte Kommentar (ProblemExplorer) erklärt die Sperre mit fester Kapazität pro Flug: Agenten, die systematisch die günstigsten Tarife abgreifen, drücken den Durchschnittserlös. United gebe günstige Tarife lieber Kunden mit hohem Langfristwert. Für jedes Geschäft mit fixer Kapazität und dynamischen Preisen ist das die Frage, die man sich vor einer Öffnung für Agenten stellen sollte.

8. **Asymmetrie im eigenen KI-Einsatz vermeiden.** Kommentatoren werfen der Airline vor, Kunden-Agenten zu verbieten, im Störungsfall aber selbst Kunden an ein LLM statt an einen Menschen zu verweisen. Wer Kunden-KI sperrt und gleichzeitig eigene KI im Service einsetzt, muss mit genau diesem Vorwurf rechnen.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 661 Punkte, 688 Kommentare | Resonanz der Hacker-News-Diskussion | Plattformangabe |
| 5 Dollar | Preisunterschied, ab dem ein Economy-Kunde laut Kommentar von United zu Delta wechselt | Behauptung ohne Beleg |
| 50 Dollar | Hypothetischer Agenten-Fund für SFO nach DEN | Rechenbeispiel, kein gemessener Fall |
| 250 Dollar | Geschätzte nominale Kosten eines Economy-Sitzes („likely“) | Behauptung ohne Beleg |

Kosten pro Flugsuche, Anteil von Bot-Traffic oder Schadensfälle nennt weder der Artikel noch die Diskussion.

## Wortlaute
- „unauthorized, third-party personal AI agents or assistants“: Uniteds Abgrenzung, wen die Regel trifft. Zeigt, dass die Sperre auf persönliche Agenten von Dritten zielt, nicht auf alle Automatisierung.
- „actions taken by these tools may result in unintended purchases, account changes, or use of MileagePlus miles“: Uniteds Risikoformulierung. Typische Begründung, die sich in Nutzungsbedingungen anderer Anbieter wiederfinden dürfte.
- „directly within our digital platforms and indirectly via travel agencies and aggregators“: die zwei Ebenen der Durchsetzung, ohne Angabe der Mittel.

## Grenzen und Widerspruch
- **Keine Belege für die Gründe.** United nennt Sicherheit und Bundesrecht, aber keine konkrete Vorschrift und keinen Vorfall. Die Rechtsaussage zum Check-in steht im Konjunktiv.
- **Drei Erklärungen nebeneinander.** United nennt Sicherheit und Recht, der Analyst Kontrolle über den Kundenkontakt und Suchkosten, die Diskussion Preisdifferenzierung. Keine davon ist belegt.
- **Kostenargument fraglich.** pavel_lishin wendet ein: Wenn Suchen teuer wären, wären cachende Intermediäre für die Airline billiger als direkte Agentenanfragen. Prüfen lässt sich das ohne Kostenzahl nicht.
- **Widerspruch bei Aggregatoren.** United will auch indirekt über Aggregatoren beschränken, der Analyst sagt, Tarife blieben über Kayak, Hopper und Google Flights buchbar. ProblemExplorer prognostiziert dagegen, günstige Tarife würden bei Agenten-Umgehung ganz verschwinden.
- **Southwest nur „viewable“.** Ob über ChatGPT bei Southwest auch gebucht werden kann, bleibt offen.
- **Fehlende Eckdaten.** Kein Datum des Inkrafttretens, keine technischen Mittel, keine Definition von „autorisiert“.
- **Genannte Agenten unverifiziert.** „Meta's Muse“ und „OpenAI's dots“ stehen im Artikel ohne weitere Angaben.
- **Diskussion unvollständig.** Nur die ersten Kommentare liegen vor, verlinkte Threads und ein msn.com-Artikel sind nicht im Material. Alle Kommentare sind Meinung oder Einzelerfahrung.
- **Geltungsbereich.** Alles betrifft B2C-Reise mit fixer Kapazität und dynamischen Preisen. Übertragbarkeit auf B2B-Beschaffung oder Händler ohne Kapazitätsgrenze ist nicht gezeigt.
