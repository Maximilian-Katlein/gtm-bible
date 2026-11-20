# Foolscap: eine Schreibapp, die dein Buch liest und nie für dich schreibt

> **Quelle:** [Show HN: Foolscap – a writing app that reads your book and never writes for you](https://foolscap.works/) · Foolscap (Show-HN-Einreichung, Autorenname nicht genannt), Foolscap (foolscap.works) · Diskussion (Landingpage plus [Hacker-News-Thread](https://news.ycombinator.com/item?id=50559749)) · 2026-11-20
> **Sprecher verkauft:** Schreibapp für Bücher, die das ganze Manuskript kennt, Zusammenhänge und offene Handlungsfäden anzeigt und selbst keinen Text erzeugt · **Zielmarkt der Aussagen:** Buchautorinnen und Buchautoren, in der Diskussion auch Sachbuch und Blogposts · **Beweislage:** reine Herstellerangaben von der Landingpage, dazu 14 von 84 Kommentaren ohne Antwort des Anbieters.

## Worum es geht
Wie positioniert man ein KI-Werkzeug, dessen Kernversprechen ist, dass die KI nicht schreibt? Die Quelle ist für Gründer und Produktteams nützlich, die KI-Produkte als Verstärkung menschlicher Arbeit statt als Ersatz vermarkten wollen. Sie zeigt außerdem, welche Fragen eine Datenschutzbotschaft offen lässt und welche Landingpage-Fehler ein Launch auf Hacker News sichtbar macht.

## Was man anwenden kann
1. **Positionierung über eine Verweigerung.** Foolscap definiert sich über das, was die App nicht tut: Sie erzeugt kein Wort. Sie zeigt nur Stellen im vorhandenen Text, an denen etwas zusammenhängt oder offen bleibt. Das grenzt das Produkt klar von generativen Schreibtools ab. Ob das kommerziell trägt, ist nicht belegt; die Resonanz im Thread spricht aber dafür, dass die Botschaft bei einem technikaffinen Publikum ankommt.

2. **Augmentieren statt Ersetzen als Nische prüfen.** Mehrere Kommentatoren begrüßen Werkzeuge, die den Arbeitsprozess ergänzen. FinnLobsien beschreibt, dass viele KI-Tools Schreiben oder Programmieren als lästige Pflicht behandeln, obwohl der Prozess vielen Freude macht. dgrcode erwartet eine Marktspaltung: Die Mehrheit der Tools automatisiert den Menschen weg, eine Minderheit stärkt ihn. Wer ein KI-Produkt baut, kann prüfen, ob die eigene Zielgruppe zur zweiten Gruppe gehört. Belege dafür gibt es keine, es sind Einschätzungen einzelner Nutzer.

3. **Datenschutz in zwei getrennten Zusagen formulieren.** Die Landingpage trennt zwei Versprechen: Texte werden nie zum KI-Training genutzt, und ein als privat markiertes Buch geht an gar keine KI. Diese Aufteilung ist klar lesbar. Sie verrät aber auch, dass nicht private Bücher offenbar an eine KI übermittelt werden. Wer so formuliert, sollte gleich mitliefern, welcher Anbieter, welches Modell und welcher Speicherort betroffen sind. Für DSGVO-Fragen und souveräne KI fehlen genau diese Angaben.

4. **Privat-Modus als Opt-in kennzeichnen.** Aus dem Wortlaut folgt, dass „privat“ eine Einstellung pro Buch ist und nicht der Standard. Vermutlich fallen dann die Kernfunktionen weg, weil sie eine KI brauchen. Das ist eine Schlussfolgerung, keine Anbieterangabe. Wer einen ähnlichen Modus anbietet, sollte offen sagen, was im privaten Modus noch funktioniert.

5. **Demo pausierbar machen.** djeastm konnte die Animation auf der Landingpage nicht anhalten. Mausbewegungen und sich öffnende Elemente liefen zu schnell, um den Funktionsumfang zu verstehen. Wenn eine Seite ihr Produkt fast nur über eine Animation erklärt, braucht diese Steuerelemente oder eine Textalternative.

6. **Mobile Ansicht vor dem Launch testen.** HaloZero sah auf dem Smartphone nur ein großes, nicht zu öffnendes Bild, einen kurzen Verkaufstext und dann den Link zu den Plänen. Die Funktion wurde mobil nicht erklärt. Bei einem Show-HN-Launch klicken viele Leser vom Telefon, die Aufmerksamkeit geht so verloren.

7. **Eigene Copy auf KI-Klang prüfen.** chmod7000 hält die Hero-Zeile für einen typischen LLM-Satz. Für ein Produkt, das sich gegen KI-generierten Text positioniert, ist KI-haftig klingende Werbung ein Glaubwürdigkeitsrisiko. Die Zeile selbst geschrieben zu haben, reicht nicht; sie muss auch so klingen.

8. **Abgrenzung zum naheliegenden Vergleich vorwegnehmen.** iknownthing fragt, was Foolscap von Cursor im Ask-Modus unterscheidet. Die mögliche Antwort, proaktive Hinweise beim Schreiben statt Chat auf Anfrage, steht nicht auf der Seite. Eine Landingpage sollte den ersten Vergleich, den Nutzer ziehen, selbst beantworten.

9. **Einsatzfälle benennen.** janandonly schreibt ein Lehrbuch und fragt nach der Eignung, iamben fragt nach Blogposts. Beide Fragen bleiben im Material unbeantwortet. Die Formulierung „Verbindungen und offene Fäden“ klingt nach Erzählstruktur; für Sachtexte ist die Eignung unbelegt.

10. **Review-Workflow für die eigene Arbeit (Entwicklung).** noir_lord schreibt Code selbst, lässt ihn von der KI prüfen und liest das Ergebnis genau. Bei Zustimmung wird der Code angepasst, bei Ablehnung bleibt er. Bei starkem Widerspruch kommt eine Begründung in eine Datei errata.md. Das gilt als Einzelpraxis aus der Softwareentwicklung, nicht als belegte Methode.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 103 | Punkte des Show-HN-Beitrags zum Zeitpunkt der Erfassung | eigene Daten |
| 84 | Kommentare im Thread | eigene Daten |
| 14 | davon im Material ausgewertete Kommentare | eigene Daten |

## Wortlaute
- „It never writes a word for you.“ (Landingpage, kein Zeitstempel). Die Kernpositionierung in einem Satz.
- „Your writing is never used to train AI. Mark a book private, and nothing of it goes to any AI at all.“ (Landingpage). Datenschutzbotschaft mit zwei getrennten Zusagen.
- „Your book, alive as you write it.“ (Landingpage, Hero-Titel). Die Zeile, die chmod7000 als LLM-typisch kritisiert.
- „AI tools that work with you and augment your process, but don't replace it.“ (FinnLobsien). Wie Nutzer die Positionierung in eigenen Worten wiedergeben.

## Grenzen und Widerspruch
- Die Seite nennt keine Preise, kein Modell, keine Architektur, keine Plattformen, Dateiformate, Sprachen oder Buchlängen. Ein Link zu Plänen existiert, der Inhalt liegt nicht vor.
- Ob die Analyse lokal oder in der Cloud läuft und welche Anbieter Daten erhalten, bleibt offen. Für souveräne KI ist das die entscheidende Lücke.
- Die Datenschutzzusagen sind ungeprüfte Herstellerangaben ohne Zertifizierung oder technische Beschreibung.
- Das Demo-Video liegt nicht vor, der Funktionsumfang ist nicht überprüfbar.
- Der Anbieter antwortet in den erfassten Kommentaren nicht. Nur 14 von 84 Kommentaren wurden ausgewertet, die Stimmung ist daher nicht repräsentativ.
- Konkurrenz: dleeftink nennt Fleshnote, eine Pre-Release-App mit ähnlichem Ansatz und einer Funktion „Pentimento“ (Versionierung für Prosa). Foolscap zeigt laut Material keine vergleichbare Funktion. Der Reifegrad von Fleshnote ist nicht verifiziert.
- chiasabah schlägt formale Verifikation der Handlung vor, etwa mit dem Beweisassistenten Lean. Ob das für literarische Texte praktikabel ist, bleibt offen.
- guy4261 wirft scherzhaft ein, an KI-Anbieter übermittelte Texte könnten rechtlich relevant werden. Der verlinkte Fall ist im Material nicht überprüfbar.
- Für B2B Go-to-Market ist die Quelle nur am Rand relevant. Verwertbar sind vor allem Positionierung, Datenschutzbotschaft und Landingpage-Kritik.
