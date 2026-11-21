# Harvard-Forscher: KI-Coding-Agents verlagern den Engpass ins Code Review

> **Quelle:** [Harvard researchers find AI coding agents shifted the bottleneck to code review](https://complexdiscovery.com/harvard-researchers-find-ai-coding-agents-shifted-the-bottleneck-to-code-review/) · ComplexDiscovery OÜ Staff, berichtet über ein Working Paper von Fiona Chen und James Stratton (Harvard) · Artikel mit [Hacker-News-Diskussion](https://news.ycombinator.com/item?id=50538303) · 2026-11-18
> **Sprecher verkauft:** Nachrichten und Analysen zu eDiscovery, Datenschutz, Compliance und Legal AI · **Zielmarkt der Aussagen:** Softwareteams (Studie), eDiscovery-, Compliance-Profis und Legal-AI-Käufer (Artikel-Ableitungen) · **Beweislage:** große Paneldaten aus einem Working Paper ohne abgeschlossenen Peer Review, nur über den Sekundärbericht vorliegend; die Legal-Schlüsse sind unbelegte Übertragungen.

## Worum es geht
Bringen KI-Coding-Agents mehr fertige Arbeit oder nur mehr Code? Eine Studie mit 718 Firmen findet rund 30 Prozent mehr Code, aber keinen messbaren Zuwachs an erledigten Aufgaben, weil das Review 49 Prozent länger dauert. Relevant für Engineering-Leiter, die Agents einführen, und für Käufer von KI-Werkzeugen, die Produktivitätsversprechen prüfen müssen.

## Was man anwenden kann
1. **Downstream messen, nicht Entwurfsleistung.** Die Studie zählt Output als gelöste Jira-Issues, deren Code in Produktion ist. Mehr Codezeilen, Commits (plus 20 Prozent) und Pull Requests (plus 23 Prozent) blieben ohne Effekt auf diese Größe. Wer Agents bewertet, braucht eine Kennzahl am Ende der Kette, etwa Zeit von Einreichung bis Merge und Anzahl ausgerollter Issues.
2. **Review-Kapazität vor dem Entwurfsvolumen planen.** Die Merge-Dauer stieg von 7,03 auf rund 10,5 Tage. Der Anteil der Beschäftigten, die überhaupt reviewen, stieg um 14 Prozent (Basis etwa 29 Prozent), ohne den Stau aufzulösen. Mehr Generierung ohne Prüfkapazität verschiebt nur die Warteschlange.
3. **Herausfinden, welcher Engpass dominiert.** Das Modell der Autoren trennt zwei Kanäle. Volumen: mehr Code trifft auf einen festen Reviewer-Pool, lösbar durch Umschichtung ins Review. Qualität: Änderungsanforderungen haben sich fast verdoppelt (von 13 Prozent der PRs um etwa 12 Prozentpunkte), Kommentare pro PR stiegen um 35 Prozent; das spricht für schlechtere Entwürfe und verlangt bessere Technologie. Beide Fälle brauchen unterschiedliche Budgets. Die Gewichtung der Kanäle beziffert der Bericht nicht.
4. **Protokollieren, was Reviewer ändern.** Der Artikel empfiehlt ein Log der Reviewer-Änderungen. Es zeigt, ob Menge oder Qualität das Problem ist, und liefert die Grundlage für Punkt 3.
5. **KI-Anteil über Metadaten erfassen.** Die Forscher erkannten Agent-Nutzung an Bot-Accounts, die KI-Tools zugeordnet sind, und an „Co-authored-by“-Zeilen in Commits und PR-Beschreibungen. Dieselben Marker lassen sich in der eigenen Codebasis auswerten, sofern die Tools sie setzen.
6. **Keine Wunder von KI-Review-Tools erwarten.** Fast 80 Prozent der Firmen hatten bis März 2026 ein KI-Review-Tool genutzt. Trotzdem kamen nur 23,3 Prozent der Kommentare von KI, und nur 10,8 Prozent der PRs erhielten überhaupt einen KI-Kommentar. Der Engpass blieb laut Autoren bestehen.
7. **Schutzregeln auf Engpasswirkung prüfen.** Ein Junior-Engineer berichtet: Nach Ausfällen durch KI-Commits verlangte man Senior-Freigabe für KI-Code, bei einem einzigen Senior, der einmal pro Woche prüfte. Die Qualitätsregel verstärkte den Stau. Wer solche Regeln einführt, sollte die Freigabekapazität gleich mitplanen.
8. **Kauftest für Legal-AI (Artikel-Empfehlung).** Erst klären, ob der Agent Populationsoutput (z. B. Relevanzprüfung in der ersten Review-Runde, per Sampling validierbar) oder Einzeldokumente (Einreichungen mit Zitaten und sensiblen Daten, direkt zu prüfen) erzeugt. Dann vom Anbieter verlangen: Stunden von Upload bis freigegebenem Arbeitsprodukt, Anteil zurückgeschickter Entwürfe, Reviewer-Zeit pro Fall. Gilt als Ableitung aus Softwaredaten, nicht als geprüfte Legal-Regel.
9. **Herstellerzahlen auf die Prüfphase abklopfen.** Harvey nennt für eine Motion to Dismiss 40 bis 50+ Stunden manuell und wenige Stunden für Recherche und ersten Entwurf, ohne Angabe zur Anwaltszeit an den „Human Checkpoints“. Bei US-Bundesgerichten bleibt nach Rule 11(b) eine angemessene Prüfung Pflicht des Anwalts. Cooleys Schwärzungsagent mit Google Cloud ist in Entwicklung, ohne veröffentlichte Fehlerquote.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 725.938 Beschäftigte, 718 Firmen | Stichprobe, Januar 2021 bis März 2026, nur zustimmende Jellyfish-Kunden | Studie, laut Bericht |
| 68,3 Mio. / 200,9 Mio. / 49,1 Mio. / 21,3 Mio. | Jira-Issues / Commits / Pull Requests / Kalenderereignisse; Kalender nur von 213 Firmen | Studie, laut Bericht |
| plus 1.494 Zeilen auf Basis 5.017 (rund 30 %) | hinzugefügter Code pro Beschäftigtem und Monat | Studie |
| plus 20 % / plus 23 % | Commits / Pull Requests | Studie |
| plus 0,12 Issues auf Basis 3,67, SE 0,17 | erledigte Jira-Issues pro Beschäftigtem und Monat, nicht signifikant; Anstieg über rund 12 % ausgeschlossen | Studie |
| plus 3,45 Tage auf Basis 7,03 (49 %) | Zeit von PR-Einreichung bis Merge | Studie |
| etwa plus 12 Prozentpunkte auf Basis 13 % | PRs mit formaler Änderungsanforderung | Studie |
| plus 35 % | Review-Kommentare pro PR | Studie |
| plus 14 % auf Basis etwa 29 % | Anteil der Beschäftigten, die reviewen | Studie |
| fast 80 % / 23,3 % / 10,8 % | Firmen mit KI-Review-Tool / KI-Anteil an Kommentaren / PRs mit mindestens einem KI-Kommentar | Studie |
| Rückgang über 2,9 % bzw. 13,8 % ausgeschlossen | Gesamt- bzw. Engineering-Beschäftigung, kurzfristig | Studie, mit Vorbehalt der Autoren |
| plus 240 % zu plus 30 % | Commits autonomer Agents zu tatsächlichen Releases, über 500.000 GitHub-Entwickler | NBER-Paper (Demirer, Musolff, Yang), Autoren beraten Microsoft bezahlt |
| 40 bis 50+ Stunden | manueller Aufwand für Motion to Dismiss | Herstellerangabe Harvey |
| ein Tag bis sechs bis zwölf Monate | Freigabedauer für KI-Tools in Firmen | zwei Interviewaussagen |

## Grenzen und Widerspruch
- **Nur Sekundärquelle.** Das Paper (fion.ac/jellyfish.pdf) lag nicht vor. Es ist ein Job-Market-Paper, aktuelle Version vom 4. August 2026, ohne Hinweis auf abgeschlossenen Peer Review.
- **Gemessen wird der Schritt von Assistenten zu Agents**, in Firmen, die schon KI-Assistenten nutzten. Für Firmen ohne jede KI-Nutzung sagt die Studie nichts.
- **Design mit Annahmen.** Gestaffeltes Difference-in-Differences, gestützt auf das Argument, dass Einführungszeitpunkte vor allem von Beschaffung, Legal- und Security-Freigaben abhingen. Größere Firmen führten früher ein; die Autoren meinen, ein verbleibender Bias würde KI eher besser aussehen lassen. Das ist ein Argument, keine Prüfung.
- **Output über Jira-Issues**, nicht über Umsatz oder Kundenwert. Die Kontrolle der Aufgabengröße beruht auf GPT-4o-Labels einer 0,5-Prozent-Stichprobe, per Embedding hochgerechnet.
- **Unbekannte Tools und Modelle.** Welche Agents, Versionen und wie die Einführung datiert wurde, nennt der Bericht nicht. In der Diskussion wendet lz400 ein, Forschungszyklen hinkten der Modellentwicklung hinterher.
- **Datenpartner mit Eigeninteresse.** Jellyfish verkauft Engineering-Analytics. Der Artikel sagt, die Beziehung gehe über eine Datenlizenz hinaus; der Text bricht an dieser Stelle ab.
- **Keine Legal-Daten.** Der Artikel räumt selbst ein, dass Document Review nicht Code Review ist. Die 49 Prozent auf Kanzleien hochzurechnen, überdehnt die Evidenz. Die Information-Governance-These (KI-Autorenschaft als Record für Legal Holds) ist Interpretation, keine Rechtsklärung.
- **Diskussion (Meinungen und Einzelfälle):** gzell sieht den Engpass in schlechter Spezifikation, nicht im Review. dangoodmanUT macht ihn von SDLC und Bürokratie abhängig. dominotw berichtet, in der eigenen Firma lese niemand mehr PRs, mit offenem Qualitätsrisiko. jacobgorm erwartet, dass ohne Ownership niemand mehr reviewen will. JonoW schlägt vor, die Prompts statt des Codes zu reviewen und Outputs per Test zu prüfen, ohne Erfahrungswerte. TexanFeller: „Code ist billig“ gilt nur, wenn niemand ihn verstehen und warten muss. ttctciyf erinnert an Buchhaltungssoftware der 1970er, die länger brauchte, weil Menschen alles nachrechneten.
