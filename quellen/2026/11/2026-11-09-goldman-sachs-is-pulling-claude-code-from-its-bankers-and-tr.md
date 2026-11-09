# Goldman Sachs entzieht Bankern und Tradern Claude Code

> **Quelle:** [Goldman Sachs is pulling Claude Code from its bankers and traders](https://www.thestateofai.com/news/goldman-sachs-claude-code-traders-bankers) · State of AI (thestateofai.com), Zusammenfassung eines Bloomberg-Berichts · Artikel mit [Hacker-News-Diskussion](https://news.ycombinator.com/item?id=50415628) (874 Punkte) · 2026-11-09
> **Sprecher verkauft:** redaktionelle KI-Nachrichten; die Seite trägt ein Label für gesponserte Inhalte und wirbt am Ende für Outlever, einen Anbieter von Redaktionssystemen · **Zielmarkt der Aussagen:** Führungskräfte und Praktiker, die Coding-Agenten in Unternehmen und regulierten Branchen einführen · **Beweislage:** Nacherzählung eines Bloomberg-Berichts auf Basis anonymer Quellen, die Primärquelle liegt nicht vor.

## Worum es geht
Wer in einem regulierten Unternehmen Coding-Agenten nutzen darf und unter welchen Kontrollen. Laut Bloomberg beschränkt Goldman Sachs Claude Code und GitHub seit einer Richtlinie vom Oktober auf seine Entwickler. Für Teams, die Agenten an Fachbereiche verteilen wollen, zeigt der Fall, an welchen Stellen das Risiko entsteht: Eigentum am Code, Freigabeprozess, Informationsbarrieren und Kosten.

## Was man anwenden kann
1. **Die Grenze nach Rolle ziehen, nicht nach Werkzeug.** Goldman sperrt nicht Claude als Modell. Der hauseigene KI-Assistent mit Modellen mehrerer Anbieter bleibt für alle verfügbar. Eingeschränkt sind Fremdagenten, die selbstständig Code schreiben und ausführen. Strats in Handel, Quant-Forschung und Softwareentwicklung behalten den Zugang. Wer eine Richtlinie entwirft, sollte deshalb Chat-Assistenz und ausführende Agenten getrennt regeln.

2. **Das Risiko liegt im fehlenden Freigabeweg.** Claude Code liest Dateien, schreibt Programme und führt sie aus, meist mit den Rechten des Nutzers. Engineering-Code durchläuft Review, Tests und Deployment-Kontrollen. Das Skript eines Traders zur Überwachung von Kundenflüssen kann ohne diese Schritte im Tagesgeschäft landen, auf Rechnern mit Kundendaten. Prüfen: Gibt es für Code aus Fachbereichen überhaupt einen Freigabeweg?

3. **Informationsbarrieren gelten auch für Agentencode.** Banken müssen etwa Deal-Banker von Tradern trennen. Goldman baute seine interne KI-Plattform um solche Kontrollen herum. Ein mit einem Agenten gebautes Trader-Tool kennt diese Kontrollen nicht, und das Engineering sieht es nur, wenn jemand es schickt. Der Artikel hält dieses Argument allein für ausreichend.

4. **Vor dem Verteilen einen Eigentümer benennen.** Empfehlung der Redaktion: Baut jemand außerhalb des Engineerings ein Tool mit Claude Code oder Copilot, übernimmt ein namentlich benannter Engineer die Verantwortung, bevor das Tool Produktionsdaten berührt.

5. **Nutzungszwecke festhalten, bevor ein Werkzeug entzogen wird.** Trader nutzten die Agenten, um Kundenhandelsflüsse zu überwachen, Marktbewegungen und Positionen zu modellieren und Unterlagen in Text und Grafik zu erstellen. Diese Bedarfe bestehen weiter. Der Artikel rät, die Beschwerden als Anforderungsliste für das Engineering zu sammeln.

6. **Produktive Agenten in Engineering-Hand betreiben.** Anthropic-Engineers arbeiteten laut Goldman sechs Monate in der Bank an Claude-Agenten für Trade Accounting und Client Onboarding. Diese laufen im Back Office und werden von Goldmans Engineering betrieben. Das Muster: Agenten ja, aber mit Betrieb und Verantwortung bei den Entwicklern.

7. **Kosten der Agentennutzung vorab begrenzen.** Agenten werden pro Token abgerechnet. Der Artikel vermutet ohne Beleg, dass Kosten bei Goldman mitspielten. Ein HN-Kommentator berichtet aus seiner Organisation, dass Claude wegen chronischer Überschreitungen zurückgenommen wird und Gemini wegen Pauschalabrechnung mit Drosselung zum Zug kommt. Für Nicht-Engineering-Nutzer sei die Erfahrung zu 90 Prozent gleich.

8. **Standort und Vertrag prüfen.** Im April nahm Goldman Claude in Hongkong von der internen Plattform, laut Financial Times wegen strikter Vertragsauslegung. Anthropic sagt, Claude sei dort nie offiziell unterstützt gewesen. JPMorgan strich Claude im Juni von seiner Hongkong-Liste. ChatGPT und Gemini blieben bei Goldman dort verfügbar. Regionale Verfügbarkeit gehört in jede Modellauswahl.

9. **Alternative zum Verbot: eine sichere Umgebung bauen.** Aus der Diskussion: Das Engineering könne eine Programmierumgebung für Banker entwerfen, in der sie sich nicht schaden können, mit Abstraktionen, die Banker-Agenten nutzen. Setzt Plattform-Kapazität im Engineering voraus.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| rund 47.000 | Beschäftigte von Goldman Sachs | Angabe Goldman (CIO Argenti), über State of AI |
| mehr als 12.000 | Entwickler bei Goldman, die erste Welle der KI-Einführung | Angabe Goldman, über State of AI |
| gut 25 % | Anteil der Entwickler an der Belegschaft | eigene Rechnung aus den beiden Zahlen |
| 6 Monate | Einsatz von Anthropic-Engineers in der Bank | Angabe Goldman, über State of AI |
| 29 US-Dollar | Claude-Budget pro Mitarbeiter und Monat bei Accenture | Behauptung ohne Beleg im Artikel |
| 50 % | Anteil der Barclays-Entwickler, die bis Jahresende Claude Code nutzen sollen | Angabe Barclays, über State of AI |
| 5.000 | Stellenstreichungen bei Barclays, darunter Entwickler | Behauptung ohne Beleg im Artikel; der Zusammenhang mit Agenten ist Interpretation |
| 26. Oktober | Einreichung des S-1 für den Anthropic-Börsengang, Goldman und Morgan Stanley als Lead Underwriter | über State of AI, Primärdokument nicht im Material |
| 1,5 Bio. bzw. 2 Bio. US-Dollar | Bewertungsziel Anthropic | nur Schlagzeile bzw. HN-Kommentar, widersprüchlich, nicht verwenden |
| 90 % | Teil der Nicht-Engineering-Organisation, für den Gemini und Claude gleichwertig seien | Anekdote eines Kommentators |

## Wortlaute
- „the bank makes certain AI tools available to staff "to determine the best use cases"“: offizielle Goldman-Stellungnahme. Sie sagt nichts zur Begründung der Einschränkung.
- „a named engineer should take responsibility for it before it touches production data.“: die Kernregel für agentengebauten Code aus Fachbereichen.
- „Information barriers, data entitlements and software approval rules still apply when the code came from a prompt.“: bestehende Kontrollen werden auf eine neue Herkunft von Code ausgedehnt, nicht neu erfunden.
- „Withdrawing access through a guideline update, with no replacement mentioned in Bloomberg's reporting, tells the traders who found good uses that they were the risk.“: Kritik der Redaktion an der Umsetzung.

## Grenzen und Widerspruch
- **Schwache Quelle.** Alle Kernfakten stammen aus einem Bloomberg-Bericht mit anonymen Quellen, den State of AI nacherzählt. Wortlaut der Richtlinie und Ergebnis der Prüfung zu Produktivität und Risiko fehlen. Ein Kommentator stuft State of AI als KI-geschriebene Seite eines Spam-Unternehmens ein. Die Seite trägt ein Sponsoring-Label. Angaben zu Barclays, Amazon, Accenture, Meta, JPMorgan und Schwab sind im Text nicht belegt.
- **Unklarer Umfang.** Offen bleibt, ob mit „GitHub“ nur Copilot gemeint ist und ob Coding-Funktionen in der Claude-App (Artifacts) weiter nutzbar sind. Ein Kommentator meint, Claude Code passe ohnehin schlecht zu Nicht-Entwicklern, die App decke den Bedarf.
- **Engineer ist nicht gleich Kontrolle.** Ein Kommentator hält dagegen, dass auch Entwickler bei hohem Agenten-Output die Fähigkeit verlieren, Code sorgfältig zu lesen. Der Artikel selbst verweist auf einen Meta-Engineer, der Code ausliefere, den er nicht vollständig erklären kann.
- **Die Übergabe an das Engineering ist geschönt.** Ein Empfänger solcher Trader-Tools schreibt, „verbessert“ heiße realistisch kompletter Umbau oder Backlog. Ein anderer nennt das Muster, dass Fachbereiche Prototypen in Produktion drücken, zeitlos. Der Agent beschleunige es nur. Das eigentliche Problem seien Audit-Pflichten, Datenberechtigungen, Datenlizenzen und Finanzrisiko.
- **Überinterpretation.** Lesarten wie „Goldman vertraut Frontier-Modellen nicht“ oder „Goldman verbietet KI“ widersprechen dem Artikel. Die Grenze verläuft nach Rolle, Goldman baut weiter Claude-Agenten und begleitet den Börsengang. Auch die Frage, warum Goldman das vor dem Börsengang „ankündige“, geht fehl: Es gibt keine Ankündigung, nur einen Bericht über eine interne Richtlinie.
- **Kosten sind Spekulation.** Für Goldman liegt kein Kostenbeleg vor. Bloomberg nennt nur Produktivität als Teil der Prüfung.
- **Geltungsbereich.** Die Argumente zu Informationsbarrieren und Audit gelten für regulierte Finanzhäuser. Für private oder unkritische Nutzung berichtet ein Kommentator den gegenteiligen Fall: Seine Frau, eine Ärztin, nutzt Claude Code für Alltagswerkzeuge, ohne sich für den Code zu interessieren.
- **Interessenlage.** Goldman ist laut S-1 Lead Underwriter des Anthropic-Börsengangs. Stimmen von Goldman-Tradern selbst fehlen, und ausgewertet wurde nur ein Teil der 470 Kommentare.
