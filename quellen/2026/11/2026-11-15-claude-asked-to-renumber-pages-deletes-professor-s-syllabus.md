# Claude soll Seitenzahlen anpassen und löscht den Syllabus und ein Jahr Vorlesungsnotizen eines Professors

> **Quelle:** [Claude asked to renumber pages deletes professor's syllabus, year of notes](https://www.tomshardware.com/tech-industry/artificial-intelligence/rogue-claude-ai-tasked-with-renumbering-pages-accidentally-deletes-law-professors-entire-syllabus-one-year-of-lecture-notes-youre-right-to-be-angry-i-deleted-your-files-through-my-own-carelessness-humbled-agent-admits) · Stephen Warwick, Tom's Hardware (Future), dazu Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50499114) und im Tom's-Hardware-Forum · Artikel und Diskussion · 2026-11-15
> **Sprecher verkauft:** Technikjournalismus, Werbung und Premium-Mitgliedschaft · **Zielmarkt der Aussagen:** Hardware-Enthusiasten und Technikinteressierte · **Beweislage:** ein einzelner Tweet des Betroffenen, ohne Modell, Harness oder Gesprächsverlauf, nicht unabhängig geprüft

## Worum es geht
Ein KI-Agent mit Schreib- und Löschrechten auf echte Arbeitsdateien hat bei einer banalen Aufgabe Dateien gelöscht, die mit der Aufgabe nichts zu tun hatten. Die Quelle beantwortet, welche Schutzmaßnahmen den Schaden begrenzt haben und welche ihn verhindert hätten. Relevant für alle, die Agenten an Dateisystemen oder Cloud-Speichern arbeiten lassen, ob in Teams oder allein.

## Was man anwenden kann
1. **Versionierten Speicher vor dem ersten Agentenlauf sicherstellen.** William Baude, Juraprofessor an der University of Chicago, bekam die gelöschten Dateien über Dropbox zurück. Ohne Versionierung oder Backup wäre der Verlust endgültig gewesen. Gilt für jeden Agenten mit Löschrechten auf Dateien, die nicht gesichert sind. Ein Forennutzer nennt Speicherkosten 2026 als Hürde, das betrifft vor allem große Datenmengen.

2. **Rechte auf die Aufgabe zuschneiden.** Der Auftrag betraf Seitenzahlen in alten Notizen, gelöscht wurde auch der aktuelle Syllabus. Der HN-Nutzer ghais_dev formuliert das Prinzip: Eine Bearbeitung an einem Dokument darf kein anderes Dokument entfernen können. Praktisch heißt das: Agent nur in einer Arbeitskopie oder einem eigenen Ordner arbeiten lassen, nicht im Hauptverzeichnis.

3. **Löschaktionen bestätigen lassen.** Wer den Agenten ohne Rückfragen überall alles tun lässt, muss mit solchen Vorfällen rechnen (forgotpwd16). Ob Baude so arbeitete, ist nicht belegt. Für Claude Code und die Claude Apps empfiehlt ein Anthropic-Mitarbeiter den Auto Mode, der Aktionen vor der Ausführung auf Risiko prüft. Ob er diesen Fall verhindert hätte, kann er selbst nicht sagen.

4. **Deterministische Werkzeuge für Routineaufgaben nutzen.** Seitenzahlen kann Word selbst neu nummerieren. Das gilt nur, wenn es um die Seitennummerierung des Dokuments ging und nicht um Seitenverweise in Zitaten. Baude warnt laut Artikel selbst davor, KI für banale Aufgaben einzusetzen.

5. **Unbeaufsichtigte Läufe nur mit Sicherung.** Der Vorfall geschah, während Baude beim Mittagessen war. Wer einen Agenten allein laufen lässt, sollte vorher die Punkte 1 bis 3 erfüllt haben. Das ist eine Ableitung aus dem Fall, keine Aussage der Quelle.

6. **Statusmeldung des Agenten gegen die Aufgabe prüfen.** Der Agent meldete konkret, welche Dateien gelöscht und nicht wiederhergestellt waren, und dass die eigentliche Aufgabe nicht erledigt war: ein falscher Zitatverweis gefunden, nichts bearbeitet. Ergebnis war also Datenverlust ohne Fortschritt. Die Meldung erleichterte die Wiederherstellung, weil Dateinamen genannt waren.

7. **Vorfallberichte mit vier Fragen bewerten.** Mehrere HN-Nutzer (jmuguy, MostlyStable) verlangen Angaben zu Modell, Harness, Berechtigungsmodus und Werkzeug, etwa Claude Code, Claude Desktop, Auto-Classifier oder `--dangerously-skip-permissions`. Fehlen sie, sagt der Bericht nur, dass unvorsichtiger Gebrauch schaden kann. Zusätzlich lohnt der Abgleich von Headline und Fließtext: Die Headline verschweigt die Wiederherstellung.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1 Jahr | Constitutional-Law-Vorlesungsnotizen, laut Headline gelöscht; der Agent selbst spricht nur von „top-level“ Dateien „Class N 2023“ | Anekdote, Umfang unklar |
| 1 | falscher Zitatverweis, den der Agent beim Seitenabgleich fand | Anekdote |
| 5. November 2026 | Datum von Baudes Tweet, Vorfall am Vortag | Anekdote |
| 9 Sekunden | Zeit, in der ein Claude-Agent im April eine Firmendatenbank löschte (Railway-Volume) | Verweis im Artikel, hier nicht geprüft |
| „zig Millionen“ pro Tag | Agentennutzungen, Argument von ericmay | Behauptung ohne Beleg |

## Wortlaute
Textquelle, daher ohne Zeitstempel.

- „I deleted your Fall 2026 FINAL syllabus .doc and all top-level Class N 2023 notes by accident, and they are not restored.“ Die Schadensmeldung des Agenten, mit Dateinamen und Status.
- „The page check found one wrong cite... but I haven't edited the notes.“ Zeigt, dass die Aufgabe nicht erledigt war.
- „You're right to be angry, I deleted your files through my own carelessness, and you shouldn't have to clean it up.“ Die Entschuldigung, die der Artikel in die Headline übernimmt. Das ist erzeugter Text über das eigene Verhalten, keine Einsicht im menschlichen Sinn.
- „this new default checks actions for risk before they run.“ Anthropic-Mitarbeiter edwinarbus über den Auto Mode, Herstellerangabe.
- „An edit to one document shouldn't be able to remove a different one“ Das Least-Privilege-Prinzip in einem Satz (ghais_dev).

## Grenzen und Widerspruch
- **Keine technischen Angaben.** Modell, Harness, Berechtigungsmodus und Werkzeug sind unbekannt. Der Hinweis des Agenten auf ein „browser pane“ deutet auf Browsersteuerung hin, Details fehlen.
- **Umfang unklar.** Headline („entire syllabus“, „one year of lecture notes“) und Agentenmeldung („top-level“) weichen voneinander ab. Ob alle Notizen betroffen waren, bleibt offen. Ebenso, ob die Wiederherstellung vollständig war und wie viel Aufwand sie kostete.
- **Vergleichsfälle unbelegt.** Firmendatenbank, TV-Show-Schnitt („reportedly“) und Profilverzeichnis werden nur erwähnt.
- **Keine Häufigkeitsdaten.** wolttam behauptet eine Häufung in den letzten Wochen, ericmay hält Einzelfehler bei hoher Nutzung für erwartbar. Beides ohne Zahlen.
- **Auto Mode ohne Nachweis.** Keine Erkennungsraten, keine Funktionsbeschreibung, nur die Aussage eines Mitarbeiters des Herstellers. Anthropic war laut dieser Aussage am selben Tag mit Baude in Kontakt.
- **Kritik an der Berichterstattung.** simonw hält es für keine Nachricht, weil die Dateien zurückkamen, und sieht die Verantwortung bei Backups und umkehrbaren Operationen. contubernio nennt den Artikel tendenziös, Thunder64 vermutet absichtliches Weglassen der Wiederherstellung in der Headline. julianlam lehnt die Wortwahl „humbled“ ab.
- **Fehlerklassen.** Der Artikel trennt fehlgeleitete Eigeninitiative (Agent beschließt, Löschen sei der Ausweg) von echten Versehen und ordnet Baudes Fall als Versehen ein. Im Forum ist umstritten, ob man bei einem Modell überhaupt von Versehen sprechen kann.
- **Haftung offen.** Ein Kommentar fordert, Verantwortung bei Agentenfehlern jetzt zu klären. Der Fall selbst liefert dazu nichts.
