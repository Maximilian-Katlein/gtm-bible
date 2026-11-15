# Kaum zu glauben: Wir haben in 67 Minuten mit KI eine App gebaut (V0, Cursor AI, Replit, Claude AI)

> **Quelle:** [I can't believe we coded an app with AI in 67 mins (V0, Cursor AI, Replit, Claude AI)](https://www.youtube.com/watch?v=kDcM_xwmP3Q) · Greg Isenberg (Late Checkout), Riley (Software Composers) · Video · 2026-11-14
> **Sprecher verkauft:** Software Composers Community und Kurse; im Video läuft zudem eine Sponsorenwerbung · **Zielmarkt der Aussagen:** Creator und Einzelpersonen ohne Programmiererfahrung (65:10) · **Beweislage:** Live-Demo eines einzelnen Prototyps plus Erfahrungswerte des Sprechers, keine Messungen.

## Worum es geht
Das Video zeigt, wie eine Person ohne klassische Programmierausbildung mit V0, Cursor, Replit, Firebase und einer LLM-API einen funktionierenden Web-Prototyp baut. Die gebaute App lädt YouTube-Transkripte, lässt eine KI darin Geschäftsideen finden und speichert bewertete Ideen im Nutzerprofil. Relevant ist das für Gründer, Marketer und Creator, die interne Tools oder Prototypen selbst bauen wollen, nicht für produktive Software mit Sicherheitsanforderungen.

## Was man anwenden kann
1. **Arbeitsteilung der Werkzeuge.** V0 erzeugt das Frontend als Next.js-Komponenten aus Sprachbefehlen (03:50). Cursor übernimmt Backend und Gesamtlogik, Replit führt die App aus, verwaltet Umgebungsvariablen und veröffentlicht sie unter eigener Domain (24:45, 25:50). Firebase liefert Datenbank und Login (26:35).
2. **Mit Vorlage starten, nicht bei null.** Riley nutzt ein vorbereitetes Template, in dem das „Plumbing“ bereits erledigt ist: Bibliotheken, Ordnerstruktur, Abhängigkeiten. Ohne Vorlage koste das Anfänger laut Sprecher bis zu 3 Stunden (08:35). Die 67 Minuten im Titel gelten also nur mit dieser Vorarbeit.
3. **UI-Elemente als Datenstruktur denken.** Die Ideenkarte in V0 hat vier feste Felder: Hauptidee, Marktbeschreibung, Marktgröße, relevante Internet-Zielgruppen (05:05). Erst die Felder, dann die Optik prompten.
4. **Optik präzise und in Schritten prompten.** Zuerst Grundstil („slick“, flach, dezente Animationen) (06:35), dann Details wie Rahmen und ein leichtes, transparentes Punktraster im Hintergrund nach Art von Millimeterpapier (09:30). Interaktion wird ebenso ausgeschrieben: Slider nach rechts ist positiv und grün, nach links negativ und rot (10:45).
5. **Den Zweck einer Funktion mitprompten.** Riley nennt im Prompt, wofür ein Element gedacht ist. Begründung des Sprechers: Das Modell greift dann auf passende UI-Muster zurück und wird kreativer (13:30). Erfahrungswert, nicht gemessen.
6. **Screenshot statt Textbeschreibung bei UI-Fehlern.** Wenn Textprompts nicht greifen: Screenshot machen, Korrekturen farbig einzeichnen, Bild in den Chat einfügen (21:15).
7. **Cursor mit Replit per SSH verbinden.** Im Cursor-Terminal mit Command K einen SSH-Schlüssel erzeugen lassen und den Public Key in Replit hinterlegen (28:10). Danach mit dem Composer mehrere Dateien gleichzeitig bearbeiten (30:15).
8. **Bewährte Prompts im Projekt ablegen.** Erfolgreiche Prompts und App-Muster landen in einer chat.md im Projektordner, damit die KI und andere Nutzer darauf zurückgreifen (31:15).
9. **Installationsbefehle selbst ausführen.** Schlägt die KI einen npm-Befehl vor (etwa openai-edge, framer-motion, lucide-react), muss er manuell in der Replit-Shell laufen (33:35, 43:10).
10. **Änderungen reversibel halten.** In Cursor rät Riley zu „Save all“ statt „Accept all“, weil Letzteres laut Sprecher nicht rückgängig zu machen ist (34:40). Gilt für die damals gezeigte Version.
11. **Fehler sichtbar machen.** Bleibt eine Eingabe ohne Reaktion, die KI ausdrücklich um Error Logs bitten (39:35). Die Fehlermeldung aus den Dev-Logs dann wörtlich in den Chat kopieren und um Behebung bitten (52:50). Leitsatz: Fehlermeldungen sind gut, leere Bildschirme schlecht (44:20).
12. **Aktuelle Doku statt Modellwissen.** Weil Modelle veraltete API-Syntax kennen, sucht Riley die aktuelle Dokumentation (hier OpenAI Chat Completions mit Structured Output) über Perplexity und gibt den Code an Cursor weiter (47:20).
13. **Anbieter wechseln, wenn eine API hängt.** Bei anhaltenden Fehlern mit der OpenAI-API lässt Riley den Code auf das Anthropic SDK umstellen (51:10). Ein pragmatischer Ausweg, keine Fehleranalyse.
14. **Hartnäckigkeit als Erfolgsfaktor.** Laut Riley scheitern die meisten in den ersten Schritten. Wer weiterfragt, komme meist im zweiten oder dritten Anlauf zu einer laufenden App (37:35).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 67 Minuten | Bau der gezeigten App im Video, mit vorbereitetem Template | Live-Demo, eigene Daten |
| 6 bis 7 Stunden | Notion-ähnliche App mit Datenbank und Speicher ohne eigene Codezeile (01:25) | Erfahrungswert des Sprechers |
| 10 bis 15 Stunden | Übung, um typische Fehler mit Claude zu beheben (02:25) | Erfahrungswert des Sprechers |
| 50 Tage | Rileys Programmiererfahrung zum Zeitpunkt der Aufnahme (03:15) | Anekdote |
| bis 3 Stunden | Plumbing ohne Vorlage bei Anfängern (08:35) | Erfahrungswert, laut Riley eine Aussage von Ange |
| ca. 20 USD/Monat | Replit-Hosting (26:35) | Aussage des Sprechers |
| 0 USD | Firebase bis zu einer gewissen Nutzerzahl (26:35) | Aussage des Sprechers, Schwelle nicht genannt |
| 15 bis 20 USD/Monat | V0-Abo (26:55) | Aussage des Sprechers, Riley ist unsicher |
| über 1.000 USD/Monat | Rileys gesamtes KI-Tool-Budget (26:55) | Eigene Angabe |
| „hunderte USD pro Stunde“ | Stundensatz eines guten Designers als Vergleich (26:55) | Schätzung ohne Beleg |

## Wortlaute
- „make it a really slick uh design uh with cool uh subtle animations.“ (06:35) Grundstil-Prompt für V0.
- „add light dots in the background as if it's graph paper... very light and transparent.“ (09:30) Detailprompt für Hintergrundtextur.
- „Sip is positive, spit is negative, sip should be green, spit should be red.“ (10:45) Interaktionslogik als Klartext.
- „generate an SSH key for Replit. Name it Replit and copy the public key to my clipboard.“ (28:10) Terminalbefehl in Cursor per Command K.
- „can you please add error logs to the AI input field. I have no way of knowing what the problem is.“ (39:35) Diagnose erzwingen.
- „Can you change this to Anthropic, please?“ (51:10) Anbieterwechsel bei hartnäckigen API-Fehlern.

## Grenzen und Widerspruch
- Die 67 Minuten setzen ein fertiges Template voraus. Rileys eigene Schätzung für eine vollständige App liegt bei 6 bis 7 Stunden.
- Gezeigt wird ein Prototyp. Datenbankstruktur, Sicherheitsregeln in Firebase und Betrieb unter Last bleiben offen.
- Die KI berechnet im Demo Marktgrößen und Prognosen bis 2028 aus einem Transkript. Ob diese Zahlen stimmen, wird nicht geprüft. Für Entscheidungen taugen sie ohne Gegenrecherche nicht.
- Das Beispiel eines Verlags, der 80 Prozent von Nischenbüchern (LitRPG) per KI erzeugt (57:55), ist eine von der KI extrahierte Idee, kein Fall mit Ergebnissen.
- Rechtliche und technische Fragen beim Abgreifen von YouTube-Transkripten werden nicht behandelt.
- Die Tool-Ratschläge (etwa „Accept all“ nicht reversibel) beziehen sich auf die damaligen Versionen und können veraltet sein.
- Die Sprecher verkaufen eine Community für genau diese Arbeitsweise. Die Erwähnung von boringmarketing.com mit 30-Tage-Sprint und Geld-zurück-Garantie (23:50) ist Sponsorenwerbung, keine Fallstudie.
- Keine Aussage dazu, wie gut der Ansatz in Firmen mit IT-Governance, Datenschutzanforderungen oder größeren Codebasen funktioniert.
