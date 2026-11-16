# Richterin lehnt Abweisung der DRAM-Absprageklage gegen Samsung, SK Hynix und Micron ab

> **Quelle:** [Judge Refuses to Dismiss DRAM Supply Conspiracy Suit Against Samsung, SK Hynix, Micron](https://litnews.ai/articles/garciaguirre-samsung-sk-hynix-micron-dram-conspiracy-suit-survives-dismissal) · LitNews.ai (Bericht über einen Beschluss von Richterin Noël Wise, N.D. Cal.), dazu [HN-Diskussion](https://news.ycombinator.com/item?id=50502988) · Artikel und Diskussion · 2026-11-16
> **Sprecher verkauft:** nichts erkennbar, juristische Nachrichtenseite · **Zielmarkt der Aussagen:** Käufer von DRAM (Verbraucher, kleine Unternehmen, PC- und Serverbetreiber) und Leser von Branchennachrichten · **Beweislage:** Gerichtsbeschluss in der Pleading-Phase, alle Marktzahlen stammen aus der Klageschrift und sind unbewiesen.

## Worum es geht
Ein US-Bundesgericht hat entschieden, dass eine Sammelklage gegen die drei großen DRAM-Hersteller weiterlaufen darf. Der Vorwurf: Sie hätten sich abgesprochen, das Angebot an konventionellem DRAM zu verknappen und Kapazität zu HBM für KI-Beschleuniger zu verlagern. Relevant ist das für alle, die Server, Workstations oder lokale Inferenz-Hardware einkaufen, und für alle, die verstehen wollen, woran ein Gericht abgestimmtes Marktverhalten von bloßem Parallelverhalten unterscheidet.

## Was man anwenden kann
1. **Stand richtig einordnen.** Am 14. November wies Richterin Wise den gemeinsamen Abweisungsantrag vollständig zurück. Das heißt nur: Die Klage beschreibt eine Absprache nach Section 1 Sherman Act plausibel. Die Vorwürfe gelten in dieser Phase als wahr unterstellt, bewiesen ist nichts. Wer den Fall zitiert, sollte nicht von einer Verurteilung sprechen.

2. **Angebotsbeschränkung, nicht Preisabsprache.** Die Klage wirft eine Verschwörung zur Verknappung von konventionellem DRAM vor. Preissteigerungen sind die behauptete Folge. Der HN-Titel und viele Kommentare sprechen von „price fixing“. Für korrekte Kommunikation über den Fall ist der Unterschied wichtig.

3. **Fristen für die Beschaffungsplanung.** Die Unternehmen müssen bis 7. Dezember 2026 auf die Klage antworten. Die erste Case Management Conference ist auf den 12. Januar 2027, 9 Uhr, angesetzt. Vor 2027 ist also keine Beweisaufnahme zu erwarten. Wer Hardwarekäufe von einem Ausgang des Verfahrens abhängig macht, plant mit Jahren, nicht Monaten.

4. **Der behauptete Mechanismus hinter knappem DDR5.** HBM soll pro Gigabyte etwa drei- bis viermal so viel Waferfläche brauchen wie DDR5. Wer Kapazität zu HBM verschiebt, nimmt damit überproportional DDR5-Menge vom Markt. Laut Klage begannen Produktionskürzungen Ende 2022, die HBM-Verlagerung ab 2023. Der Faktor ist Klagevortrag ohne technische Quelle im Artikel.

5. **Woran das Gericht Absprache von Parallelverhalten trennt.** Ohne direkte Beweise braucht es Plus-Faktoren. Akzeptiert wurden: Handeln gegen das eigene Interesse (langfristige HBM-Verträge, verweigerte Langfristverträge für konventionelles DRAM, Schließung der Marke Crucial, kein Ausbau trotz Rekordpreisen), verzögerte oder gestoppte Fabriken bei Samsung und Micron, gleichzeitiger DDR4-Auslauf, nahezu identische Kundenprüfung ab Januar 2026, Kartellvorgeschichte.

6. **Was vor Gericht wenig zählt.** Ohne Gewicht blieben Investorenaussagen zu „supply discipline“, Treffen auf Branchenkonferenzen ohne benannten Inhalt und die Dreier-Marktstruktur. Grundlage ist das Ninth-Circuit-Urteil DRAM II von 2022. Für Beobachter heißt das: Konzentration und öffentliche Rhetorik allein tragen keinen Kartellvorwurf, konkrete und schwer umkehrbare Handlungen schon.

7. **Zeitversatz widerlegt Parallelität nicht automatisch.** SK Hynix und Micron kündigten Kürzungen Ende 2022 im Abstand von drei Wochen an, Samsung folgte am 7. April 2023, rund viereinhalb Monate später. Das Gericht hielt das auf dieser Stufe nicht für zu lang.

8. **Irreversibilität als Prüfkriterium.** Nach Ninth-Circuit-Maßstab muss eine Handlung ohne Absprache so riskant sein, dass keine vernünftige Firma sie ginge. Der HBM-Schwenk allein reiche womöglich nicht. Erst zusammen mit schwer rückholbaren Schritten (Lieferbindungen, Crucial-Schließung am 3. Dezember 2025, Fabrikentscheidungen, analog zum Raffinerie-Fall Petroleum Products von 1990) kippe der Faktor zugunsten der Kläger.

9. **Kundenprüfung als stärkstes Indiz.** Die angeblich im Januar 2026 bei allen drei eingeführte, nahezu identische Kundenprüfung werte das Gericht als starkes Indiz. Die Erklärung „KI-Nachfrage“ ließ es nicht gelten, weil die Prüfung erst nach Beginn von KI-Boom und HBM-Schwenk einsetzte. Worin die Prüfung bestand, beschreibt der Artikel nicht.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| über 91 % | Anteil der drei am weltweiten DRAM-Umsatz, Q3 2025 | Klageschrift, keine Quelle genannt |
| +171,8 % | Preis für konventionelles DRAM binnen eines Jahres bis Q3 2025 | Klageschrift, ohne Preisreihe oder Referenzprodukt |
| +697 % | Preis über 18 Monate bis Q3 2025 | Klageschrift, ebenso |
| 3 bis 4fach | Waferfläche pro GB, HBM gegenüber DDR5 | Klageschrift, ohne technische Quelle |
| 17 Kläger, 5 Bundesstaaten | Verbraucher und kleine Unternehmen, Klage eingereicht 25. Juni 2026 | Artikel |
| 300 Mio. USD / 185 Mio. USD | Strafen Samsung und Hynix im Kartell 1998 bis 2002, Micron erhielt Immunität | Klageschrift laut Artikel |
| ca. 3fach | Preis gegenüber vor zwei bis drei Jahren | HN-Kommentar, Anekdote |
| 4 bis 5 Tsd. USD | jeweils für 256 GB RAM und eine GPU mit 32 GB VRAM | HN-Kommentar, Anekdote eines Forschers |

Zum Abgleich: +171,8 % entspricht rund dem 2,7fachen Preis, +697 % rund dem 8fachen (eigene Umrechnung, gerundet).

## Wortlaute
- „hawks flying in formation“: Antwort der Richterin auf das Posner-Zitat der Verteidigung, Wettbewerber beobachteten sich wie Falken. Gemeint ist: Gegenseitige Beobachtung erklärt koordiniertes Handeln nicht.
- „difficult if not impossible to unwind“: Begründung, warum Lieferbindungen und Markenschließung als Handeln gegen das eigene Interesse zählen.
- „The court gave no weight to three other arguments.“: Einleitung zur Liste der verworfenen Indizien (Investorenaussagen, Konferenzen, Marktstruktur).

## Grenzen und Widerspruch
- Alle Markt- und Preiszahlen sind Klagevortrag. Der Artikel nennt weder Datenquelle noch Referenzprodukt noch Aktenzeichen. Der Beschluss selbst liegt nur als eingebettetes PDF vor.
- Das Jahr der Entscheidung steht nicht im Text, es ergibt sich aus den Fristen (2026).
- Stellungnahmen der Unternehmen außerhalb der Anhörung fehlen.
- In der HN-Diskussion argumentiert bob1029, die echte HBM-Nachfrage sei eine vernünftige Verteidigung, HBM sei schwer herzustellen und die Branche risikoscheu. Belege zu HBM-Ausbeuten fehlen. ketzu hält fast alles für nicht kollusiv erklärbar, etwa Zurückhaltung beim Fabrikbau aus Angst vor einer KI-Blase, räumt aber ein, dass gerade das die Ablehnung des Antrags bedeute.
- sysguest sieht DDR4 zu DDR5 als echtes Upgrade und verweist auf günstige chinesische DDR4-Hersteller. Chinesische Hersteller kommen im Artikel nicht vor, die Aussage ist unbelegt.
- PeterStuer beschreibt ein Dreier-Gefangenendilemma, in dem nach früherer Kollusion keine expliziten Absprachen mehr nötig seien. Genau diese Lücke soll der Plus-Faktor-Test schließen. Das Gericht wertete die Marktstruktur bewusst als neutral.
- Woodi behauptet, DDR5 komme im Artikel nicht vor. Das stimmt für die vorliegende Fassung nicht.
- Weitere Kommentare (Reservequote von 40 % für Consumer-Elektronik, Platzen der KI-Blase, angeblich gescheiterte Börsengänge, chinesische Marktübernahme) sind Meinungen ohne Beleg und teils nicht durch das Material gedeckt.
- Für KI-Bau ist der Fall nur mittelbar relevant: Auswirkungen auf GPU-, Server- oder lokale Inferenzkosten werden nicht beziffert. Es lagen nur die ersten Kommentare vor.
- Die Belegkategorie „eigene Daten“ in den Learnings bezeichnet hier Inhalte des Gerichtsbeschlusses laut Artikel, nicht eigene Messungen.
