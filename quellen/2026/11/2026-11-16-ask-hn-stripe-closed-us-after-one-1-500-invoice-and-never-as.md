# Ask HN: Stripe hat uns nach einer einzigen Rechnung über 1.500 $ gesperrt und nie nach Belegen gefragt

> **Quelle:** [Ask HN: Stripe closed us after one $1,500 invoice and never asked for evidence](https://news.ycombinator.com/item?id=50510042) · Anonymer Autor (Gründer eines kleinen Terminvermittlers), dazu Diskussion auf Hacker News · Diskussion · 2026-11-16
> **Sprecher verkauft:** Vorab gebuchte Termine mit Hausbesitzern an lokale Handwerksbetriebe, abgerechnet pro stattgefundenem Termin · **Zielmarkt der Aussagen:** Lokale Handwerker und Bauunternehmer (B2B), Region nicht genannt · **Beweislage:** ein Einzelfall aus Sicht des Betroffenen, alle Erklärungen der Sperre sind Vermutungen von Kommentatoren

## Worum es geht
Wie richtet ein junges B2B-Unternehmen mit nutzungsbasierter Abrechnung (hier: pro Termin) die Zahlungsabwicklung bei Stripe so ein, dass sie nicht wie Kartenbetrug aussieht? Der Fall zeigt, welches Abbuchungsmuster ein neues Konto die Zahlungsfähigkeit kosten kann. Relevant für Gründer, die Pay-per-Lead- oder Pay-per-Appointment-Modelle über einen Payment-Dienstleister abrechnen wollen.

## Was man anwenden kann
1. **Keine 1-Dollar-Zahlung zur Kartenhinterlegung.** Der Autor ließ den ersten Kunden über einen Stripe Payment Link 1 $ zahlen, um die Karte für spätere Abrechnungen zu speichern. Wochen später folgte eine Belastung über 1.500 $. Mehrere Kommentatoren sehen genau darin das Muster, mit dem gestohlene Kartennummern getestet werden. Laut codingdave lehnt seine eigene Bank dieses Muster automatisch ab.
2. **Karten über Setup Intents mit Off-Session-Nutzung speichern.** didgeoridoo empfiehlt Stripes Setup Intents (docs.stripe.com/payments/setup-intents), eingestellt für Abbuchungen ohne Kundenpräsenz. Das ist der vorgesehene Weg für spätere Belastungen gespeicherter Karten. Auch damit ist ein Hold auf die erste Transaktion möglich, bis das Risk-Team die Website geprüft hat.
3. **Eine zahlbare Rechnung je Termin statt Sammelbelastung.** philsquared_ rät, im konkreten Fall drei Stripe Invoices über je 500 $ zu versenden, die der Kunde selbst bezahlt, statt eine gespeicherte Karte manuell mit 1.500 $ zu belasten. A_D_E_P_T berichtet, Stripe-Rechnungen liefen bei ihm problemlos, mit anpassbaren Konditionen, Notizen und Benachrichtigungen an mehrere Empfänger.
4. **Autorisierung schriftlich im Zahlungssystem festhalten.** Der Kunde hatte in einem aufgezeichneten Telefonat zugestimmt. Stripe begründete die Sperre aber mit fehlender Autorisierung. Laut 1123581321 legt Stripe Wert auf schriftliche Autorisierung beim Erfassen der Zahlungsabsicht. Eine Telefonaufzeichnung außerhalb von Stripe hilft im automatisierten Risikoprozess offenbar nicht.
5. **Variable Abbuchungen erst bei etabliertem Geschäft.** TZubiri hält die Rechnung über den exakten Betrag für die sauberste Form. Variable Belastungen am Monatsende seien nur für sehr etablierte Firmen mit solider Buchhaltung sinnvoll, nicht für ein neues Stripe-Konto.
6. **Website-Offenlegungen vor dem ersten großen Zahlungseingang prüfen.** didgeoridoo nennt korrekte Disclosures als möglichen Prüfpunkt des Risk-Teams. Hizonner fragt, ob Hausbesitzer über Provisionen an den Vermittler informiert werden. Ein Vermittlungsmodell sollte offen beschreiben, wer wofür zahlt.
7. **Nach endgültiger Ablehnung den Anbieter wechseln.** Der Autor scheiterte dreimal: Einspruch im Dashboard (am nächsten Tag abgelehnt), Support (Entscheidung endgültig), interne Eskalation durch einen Stripe-Mitarbeiter. lossolo und TZubiri raten, keine weitere Zeit zu investieren. Genannte Alternativen: auf High-Risk spezialisierte Prozessoren (A_D_E_P_T nennt Paykings, vom Hörensagen) oder bei rein lokalem Geschäft eine lokale Bank mit lokalem Anwalt und Versicherungsagenten (brudgers).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1 $ | Zahlung über Payment Link zur Kartenhinterlegung | Anekdote des Autors |
| 1.500 $ | Erste echte Belastung für 3 Termine, rechnerisch 500 $ je Termin | Anekdote des Autors |
| Faktor 1.500 | Sprung zwischen Testzahlung und erster echter Abbuchung | Eigene Rechnung aus den Angaben |
| 2 Tage | Zeit von der geblockten Zahlung bis zur Kontoschließung | Anekdote des Autors |
| 1 Tag | Bis zur Ablehnung des Einspruchs | Anekdote des Autors |
| 3 | Ablehnungen: Einspruch, Support, Eskalation | Anekdote des Autors |
| 4,5k, 70 Kunden, 1,6 Mio. $ | Verlust, onboardete Kunden und Gebührenumsatz laut Kommentator breue | Nicht überprüfbar |

## Wortlaute
- „payments "don't appear to have been authorized by the customer."“ Die Begründung von Stripe für die Kontoschließung: fehlende Autorisierung, nicht das Geschäftsmodell.
- „business model presents a level of risk we're unable to support“ Die spätere Antwort des Supports. Jetzt wird das Geschäftsmodell selbst als Risiko benannt.
- „the exact pattern that criminals use to test stolen credit cards numbers.“ codingdave über die Folge 1 $, dann großer Betrag.
- „imagine a person bought a lemonade from you for $1 then later on you charged them $1500 because you saved their cc. That is all stripe sees.“ philsquared_ erklärt, was das Risikosystem tatsächlich sieht.

## Grenzen und Widerspruch
- **Nur eine Seite.** Es gibt keine Stellungnahme von Stripe. Kartentest-Muster, Hochrisiko-Geschäftsmodell und fehlende Autorisierung sind Vermutungen der Kommentatoren.
- **Autor und Diskussion widersprechen sich.** Der Autor sieht den Fehler darin, dass Stripe nie Anrufaufzeichnung, Nachrichten oder eine Kundenbestätigung angefordert hat. Die Mehrheit der Kommentare verortet die Ursache in der eigenen Abrechnungsstruktur. TZubiri ergänzt: Ein Zahlungsanbieter prüft die Transaktion, nicht den Vertrag. Nur Aeseir, breue und replwoacause kritisieren vor allem Stripes Kommunikation.
- **Entscheidende Details fehlen.** Unbekannt sind Land, Kontoland, Kartentyp, ob der 1 $ verrechnet werden sollte und ob die 1.500-$-Rechnung als automatische Abbuchung oder als zahlbare Rechnung mit Link lief. Davon hängt ab, wie stark die Empfehlung „Invoices statt gespeicherter Karte“ trägt.
- **Alternativen unbelegt.** Keiner der vier genannten Wege ist durch Stripe oder einen dokumentierten Praxisfall bestätigt. Zu Paykings gibt es weder Gebühren noch Konditionen noch Aussagen zur Eignung in der EU.
- **Rechtliche Fragen offen.** brudgers vermutet, die Terminvermittlung könne in manchen Jurisdiktionen gegen Bauvertragsrecht verstoßen, und vergleicht das Transaktionsmuster mit dem von Escort-Services. Beides ist Spekulation ohne Quelle.
- **Unvollständige Diskussion.** Von 71 Kommentaren lagen nur rund 16 vor. Eine Antwort von Stripe ist darin nicht enthalten.
- **Anekdote von breue** (Verlust, angeblich unterdrückter HN-Beitrag) ist nicht überprüfbar und betrifft einen anderen Fall.
