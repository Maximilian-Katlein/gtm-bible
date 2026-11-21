# Wie man mit Claude Code 1.000 tief personalisierte Kaltmails pro Tag versendet

> **Quelle:** [How To Send 1000 Deep-Personalized Cold Emails Per Day with Claude Code](https://www.youtube.com/watch?v=Yl_0pSSiEVs) · Brandon (nur Vorname, aus der Mail-Signatur im Bild), Top of Funnel; erschienen auf dem YouTube-Kanal von Instantly · Video · 2026-11-20
> **Sprecher verkauft:** Outbound-Dienstleistung von Top of Funnel (signalbasiertes Outbound auf Clay und Instantly), indirekt Instantly und die Instantly CLI, an der der Sprecher nach eigener Aussage Standardwerte mitgebaut hat · **Zielmarkt der Aussagen:** B2B, Mid-Market, Beispiele überwiegend SaaS · **Beweislage:** Live-Demo mit 20 Pilot-Leads, ohne Versand, ohne Antwort- oder Termindaten.

## Worum es geht
Die Quelle zeigt, wie ein Outbound-Praktiker mit Claude Code und der Instantly CLI aus einer nackten Leadliste je Person recherchierte, dreistufige Mailsequenzen erzeugt und als pausierte Kampagne in Instantly lädt. Sie richtet sich an B2B-Teams, die Kaltakquise betreiben und Personalisierung nicht mehr von Hand recherchieren wollen. Der Titel verspricht 1.000 Mails pro Tag; im Video laufen tatsächlich 20 Leads, und nichts wird versendet.

## Was man anwenden kann
1. **Projektordner vorbereiten.** Leerer Ordner, gegliedert nach leads, campaigns, copy; die Leadliste kommt nach leads (03:11). Eine CLAUDE.md mit dem eigenen Angebot gehört dazu. Im Video fehlte sie, worauf Claude später nachfragen musste, was das Angebot überhaupt ist (14:06).
2. **Instantly CLI statt Weboberfläche.** Claude Code installiert die CLI per npm global und im Projekt (03:44). Laut Sprecher deckt sie die ganze Instantly-API ab, nach seiner Erinnerung 156 Endpunkte (05:06). Begründung: Agenten arbeiten am natürlichsten über Bash-Befehle im Terminal, ähnlich einem MCP-Server (05:16).
3. **API-Key sauber hinterlegen.** In Instantly unter Workspace, Integrations, API Keys einen Key anlegen (04:45). Nicht in den Chat geben, sondern über Terminal oder .env-Datei; einen Key, der im Chat gelandet ist, rotieren (05:55). Die Demo macht es trotzdem im Chat. Beobachtet: Das Flag --api-key funktionierte nicht, nur die Umgebungsvariable INSTANTLY_API_KEY (06:17).
4. **Hauptprompt in vier Teilen.** Erstens Auftrag und Werkzeug: Liste, Ziel Instantly-Kampagne, Python mit Polars in einer virtuellen Umgebung (07:03). Zweitens Recherche: jede Firma mit parallelen Hintergrund-Agenten untersuchen, dazu die Rolle der Person (07:50). Drittens Wirkung und Textregeln (08:16 bis 12:16). Viertens: erst bestätigen, dann Plan vorlegen, Freigabe abwarten (12:24). Der Sprecher diktiert den Prompt mit dem Werkzeug Spokenly (06:59).
5. **Textregeln, die automatisch geprüft werden.** Höchstens etwa 100 Wörter, Zeilenumbrüche für das Handy (10:04), schlichte Begrüßung, erste Zeile spezifisch und ohne Small Talk (10:29). Wert über einen der drei B2B-Kaufgründe rahmen: Zeit sparen, Geld sparen, mehr Geld verdienen (11:44). Weicher CTA (19:33). Claude schrieb dafür ein eigenes Prüfskript (validate_copy.py) mit Wortzahl und Sperrliste (19:20, 20:34).
6. **Erst Pilot, dann Skalierung.** Claude warnte selbst, dass 1.000 Recherchen Stunden und erhebliche Tokenkosten bedeuten, und empfahl 10 bis 25 Leads (13:39). Der Pilot mit 20 Leads lief etwa 20 Minuten (16:21). Auswahl geschichtet nach Rollen-Buckets (Sales, Marketing, Data, Ops, Executive, Engineering), je Bucket die Leads mit höchstem Decision Maker Score (17:37).
7. **Recherche als festes JSON-Schema.** Je Lead ein eigener Agent, in Batches von etwa 10 gleichzeitig. Rückgabe: company_one_liner, role_context, signal, signal_source, pain_hypothesis (16:01). Signale, wenn die Liste keine hat: Finanzierungsrunde, Neueinstellung, Produktlaunch, Stellenanzeige, Pressenennung, Podcast-Auftritt (15:23).
8. **Signalqualität markieren.** Von 20 Leads hatten 10 verifizierte Signale, 8 nur abgeleitete, weil diese Agenten keine Websuche hatten. Ein Feld signal_confidence in der CSV kennzeichnet das (20:16). Abgeleitete Signale vor dem Versand kritisch lesen.
9. **Ausgabe für Menschen und Maschine.** Ergebnis an die CSV anhängen (sechs Mail-Spalten: Betreff und Text je Schritt), zusätzlich eine Markdown-Datei zum Lesen und eine JSON-Datei für die Übergabe (15:41, 18:02).
10. **Sequenz mit wechselndem Winkel.** Tag 0, +3, +7. Schritt 1 führt mit dem Signal, Schritt 2 setzt an einem konkreten Schmerzmechanismus an, Schritt 3 ist ein weicher Abschied mit einer Rechnung oder einem „ignorier mich, wenn X“ (20:34).
11. **Individuelle Texte über Merge-Tags.** In Instantly enthält jeder Sequenzschritt nur Platzhalter wie {{email1_subject}} und {{email1_body}}; jeder Lead trägt seinen Text als custom_variables (23:51). Im Instantly-Abstand heißt Tag 7 deshalb +4 Tage nach Schritt 2.
12. **Kampagne pausiert anlegen.** Nur Text, kein Open-Tracking, kein Link-Tracking, Stopp bei Antwort und Auto-Antwort, Mo bis Fr 9 bis 17 Uhr (23:28). Absenderkonten bewusst nicht verbunden, Start nur explizit (23:51). Danach die Vorschau je Lead in Instantly prüfen (24:02).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1.000 Mails/Tag | Volumen, ab dem man laut Sprecher erkennt, ob Angebot, Liste, Botschaft oder Zustellbarkeit das Problem ist (01:30) | Behauptung ohne Beleg |
| 156 | Endpunkte der Instantly-API, aus der Erinnerung des Sprechers (05:06) | Behauptung ohne Beleg |
| ≤ 100 Wörter | Zielvorgabe je Mail (10:04); gemessen 80 bis 100 im Pilot (19:20) | Vorgabe; Messung eigene Daten |
| 20 Leads, ca. 20 Min. | Pilot-Laufzeit in Claude Code (16:21) | eigene Daten |
| 60 Mails | 20 Leads mal 3 Schritte (19:16) | eigene Daten |
| 10 / 8 | verifizierte gegen abgeleitete Signale im Pilot; 2 Leads ohne Angabe (20:16) | eigene Daten |
| < 60 bzw. < 33 Zeichen | Betreffzeile; ab etwa 34 Zeichen Abschneiden auf dem Handy (19:38) | Behauptung ohne Beleg |
| 20,8 % | Antwortrate im letzten SaaS-Lauf von Top of Funnel, von der eigenen Website übernommen (21:20) | eigene Daten, Basis nicht genannt |
| 1 bis 3 % | realistische Antwortrate bei Kaltmails; unter 1 % stimmt etwas nicht (21:29) | Behauptung ohne Beleg |
| 1 bis 3 Sek. / 5 Sek. | Aufmerksamkeit der ersten Zeile / Überfliegen der ganzen Mail (09:38, 22:35) | Behauptung ohne Beleg |
| 0 / 0 / 0 | Duplikate, ungültige Adressen, Blocklist-Treffer beim Upload der 20 Leads (23:40) | eigene Daten |

## Wortlaute
- „Hey first name, I noticed you work at company. That is not personalization. That is a mail merge.“ (00:28) Abgrenzung zwischen Serienbrief und echter Personalisierung.
- „I want you to one by one research each company by launching parallel agents in the background“ (07:50) Prompt-Anweisung für die parallele Recherche.
- „It needs to pique their curiosity and it needs to lead with value in such a way that makes them pause“ (08:16) Gewünschte Wirkung, im Prompt formuliert.
- „Never say, "I hope this email finds you well."“ (10:45) Kern der Sperrliste für Einstiege.
- „I need you to confirm with me that you understand before you actually go and do something.“ (12:24) Prompt-Abschluss, der einen Plan mit Freigabe erzwingt.
- „look up Top of Funnel.com and I want you to understand what we do“ (15:05) Angebot über die eigene Website statt Erklärung.
- „from the Director job spec, your AEs are running full cycle, both inbound and outbound. That's expensive closer time spent on prospecting“ (20:38) Stellenanzeige als Quelle für den Schmerzpunkt.
- „Worth a quick chat?“ (20:38) Der weiche CTA, der in den Beispielen wiederkehrt.

## Grenzen und Widerspruch
- **Titel und Inhalt passen nicht zusammen.** Gezeigt werden 20 Leads, nicht 1.000 pro Tag. Laufzeit, Tokenkosten und Zustellbarkeit bei 1.000 bleiben offen; Claude selbst spricht nur von „Stunden“ und „erheblichen Kosten“.
- **Keine Ergebnisse.** Es wird nichts versendet. Ob die Mails Antworten oder Termine bringen, zeigt das Video nicht.
- **Widerspruch bei der Antwortrate.** Der Agent setzt 20,8 % als Beleg in die Mail. Der Sprecher nennt das im selben Atemzug „too good to be true“ und hält 1 bis 3 % für realistisch. Eine Ausreißerzahl ohne Basis in Kaltmails kann Misstrauen erzeugen.
- **Risiko erfundener Personalisierung.** 8 von 20 Signalen stammen von Agenten ohne Websuche. Wer diese Leads ungeprüft anschreibt, behauptet unter Umständen Dinge über den Empfänger, die nicht stimmen. Für 2 Leads fehlt die Einordnung.
- **Sicherheit.** API-Key mit allen Scopes im Chat und Berechtigungsmodus „Bypass permissions“. Der Sprecher rät selbst davon ab und empfiehlt den Standardmodus mit Rückfrage.
- **KI-Merkmale im Text.** Die erzeugten Mails enthalten Gedankenstriche, die der Sprecher als typisches KI-Merkmal bezeichnet und von Hand entfernen würde (21:03). Die Sperrliste deckt das nicht ab.
- **Interessenlage.** Video auf dem Kanal von Instantly, Sprecher verkauft Outbound als Dienstleistung und hat die CLI-Standardwerte nach eigener Aussage selbst gesetzt. Die Aussage über die „erfolgreichsten Instantly-Konten“ (00:22) nennt keine Grundgesamtheit.
- **Geltungsbereich.** Alle Beispiele sind englischsprachige B2B-Tech-Firmen. Für DACH fehlen Hinweise zu Datenschutz und Rechtsgrundlage bei Kaltmails; das muss gesondert geprüft werden.
