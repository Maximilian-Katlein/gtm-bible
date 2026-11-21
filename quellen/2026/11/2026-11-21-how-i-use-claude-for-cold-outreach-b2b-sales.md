# Wie ich Claude für Cold Outreach nutze (B2B-Vertrieb)

> **Quelle:** [How I Use Claude For Cold Outreach (B2B Sales)](https://www.youtube.com/watch?v=QoiFASDh8J8) · Oleg Melnikov, Firma nicht genannt · Video · 2026-11-21
> **Sprecher verkauft:** nichts direkt; verweist auf eine kostenlose Setup-Anleitung in der Videobeschreibung und ein eigenes Video zu Content mit Claude Code · **Zielmarkt der Aussagen:** SMB, B2B-Vertrieb über LinkedIn · **Beweislage:** Live-Demo an einem einzigen Kontakt, keine Annahme- oder Antwortquoten, keine Abschlüsse gezeigt.

## Worum es geht
Das Video zeigt, wie Claude Cowork mit der Chrome-Erweiterung und dem Apify-MCP-Server eine LinkedIn-Outreach-Kette ausführt: Leads per Scraper holen, Profil und letzte Posts lesen, eine Ein-Satz-Notiz schreiben, Vernetzungsanfrage senden. Es richtet sich an Gründer und kleine Vertriebsteams, die ohne Vertriebswerkzeug-Budget personalisierte Erstkontakte aufsetzen wollen.

## Was man anwenden kann
1. **Recherche auf Profil plus 10 Posts begrenzen.** Der Prompt übergibt eine LinkedIn-URL und weist an, Profil und die letzten 10 Posts zu studieren (01:22). Cowork liest erst den oberen Profilteil, öffnet dann den Aktivitäts-Feed und geht jeden Post einzeln durch (02:20). Ein Profil je Aufgabe; die Lead-Liste wird nacheinander abgearbeitet (01:11).

2. **Aufhänger nach Resonanz wählen.** In der Demo nimmt Cowork den Post mit der stärksten Reaktion (206 Likes, 14 Kommentare) als Bezugspunkt und begründet das mit Nische und Tonfall der Person (03:17). Das lässt sich als feste Regel in den Prompt schreiben: den meistdiskutierten Post der letzten Wochen referenzieren.

3. **Bewusst unpolierter Text.** Vorgabe: ein Satz, ein spezifisches Kompliment, nicht kitschig, nicht generisch, gern etwas unbeholfen (01:11). Begründung des Sprechers: Empfänger erhalten massenhaft KI-Nachrichten, die zu glatt klingen; etwas Holpriges falle auf (03:24). Die gesendete Notiz hatte 169 von 300 möglichen Zeichen (06:18).

4. **Klickpfad im Prompt mitgeben.** Der Prompt enthält explizite UI-Anweisungen für das LinkedIn-Popup („Add a note“ klicken). Ablauf: Connect im Dropdown, „Add a note“, Text einfügen, Send, Status „Pending“ (03:50). Cowork arbeitet laut Sprecher langsam, vermutlich über Screenshots und anschließende Klickentscheidung (02:10).

5. **Leads über Apify statt Apollo-Abo.** Genutzt wird der Actor „Leads Finder | Similar to Apollo“ von Brave Leads (04:57). Eingabe als JSON: 100 Ergebnisse, Seniorität CEO und Founder, Branchen-Keywords aus dem Marketing-Umfeld, nur verifizierte Mails (05:43). Cowork setzt die Parameter laut Sprecher selbst und legt die Liste als Excel-Datei im Arbeitsordner ab (06:15). Wichtigstes Feld ist die LinkedIn-URL; Mails fehlen bei einem Teil der Datensätze (05:53).

6. **Freigabeschleife einbauen.** Statt sofort zu senden, schreibt Cowork die Nachricht zuerst in die Tabelle; versendet wird erst nach Freigabe (06:39). Für alle, die Fehltreffer und Tonalität kontrollieren wollen, ist das die vernünftigere Standardeinstellung.

7. **Setup in drei Schritten.** Claude-Desktop-App laden und mit bezahltem Pro- oder Max-Plan anmelden (06:58, 07:22). Erweiterung „Claude for Chrome“ installieren und Berechtigungen erteilen; andere Browser funktionierten beim Sprecher nicht (07:46). Apify-Konto anlegen, API-Token kopieren, in Cowork unter Settings, Connectors den „Apify MCP server“ installieren, aktivieren und Token eintragen (08:29).

8. **Startprompt mit Kontext.** Für eine Kampagne: Angebot, Geschäft und Zielgruppe erklären, Scraping über Apify anfordern, Lead-Liste ausgeben lassen, dann Outreach starten (09:36). Mit „Show me the whole list of leads.“ lässt sich die Liste vor dem Versand prüfen (06:34).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 10 Posts | Recherchetiefe je Kontakt | im Prompt gezeigt |
| 169 / 300 Zeichen | Länge der gesendeten Notiz / LinkedIn-Limit | im Cowork-Log gezeigt |
| 1,50 USD je 1.000 Leads | Actor-Preis laut Sprecher; die Actor-Seite im Bild nennt 1 USD je 1.000 | Sprecher, widersprüchlich |
| 0,226 USD, 25 s | Gezeigter Lauf mit 100 Leads | im Apify-Log gezeigt |
| 5 USD/Monat | Gratis-Credits bei Apify | Sprecher |
| 3.000 Leads gratis | Rechnung des Sprechers, korrigiert von zuvor 5.000 (05:02) | eigene Rechnung, nicht nachgeprüft |
| bis 25.000 Leads je Lauf | Werbeangabe des Actors | Herstellerangabe |
| 5,0 Sterne | Actor-Bewertung bei 3 Bewertungen | Plattformangabe, sehr kleine Basis |
| unter 10 Minuten | Setup ohne Vorerfahrung | Behauptung ohne Beleg |
| 19 USD/Monat | Claude Pro laut Sprecher | Sprecher |
| 1 Abschluss = 1 Jahr Cowork | Amortisation | Behauptung ohne Beleg |

## Wortlaute
- „study her profile and last 10 posts craft a personalized message that we will send along with connection request“ (01:11). Kern des Recherche-Prompts.
- „this message should be just one sentence, making a non-cheesy and non generic complement, something super specific and maybe even a bit awkward“ (01:11). Stilvorgabe gegen glatten KI-Ton.
- „You might want to make it write the personalized message first in the table and send only after your approval.“ (06:39). Freigabe vor Versand.
- „Do the web scraping using Apollo or using Apify for some other social media. Give me the whole list of leads, and then let's do the cold outreach.“ (09:36). Startprompt für eine Kampagne.

## Grenzen und Widerspruch
- **Kein Ergebnisnachweis.** Gezeigt wird eine einzige versendete Anfrage im Status „Pending“. Annahmequote, Antworten, gebuchte Calls und Abschlüsse fehlen. Die Aussage, Gespräche würden bis zum Abschluss geführt (00:19), wird nicht demonstriert.
- **Kostenrechnung geht nicht auf.** Der gezeigte Lauf kostete 0,226 USD für 100 Leads, rechnerisch 2,26 USD je 1.000. Damit reichen 5 USD für rund 2.200 Leads, nicht 3.000. Die Actor-Seite nennt wiederum 1 USD je 1.000. Der Sprecher korrigiert sich zudem selbst von 5.000 auf 3.000.
- **Lead-Qualität.** Die gezeigten Datensätze sind überwiegend Firmen mit 0 bis 1 Mitarbeitenden (06:03). Für Zielkunden im Mittelstand oder Enterprise ist das nicht belegt.
- **Plattformregeln.** Der Sprecher räumt ein, dass LinkedIn das Vernetzungsvolumen begrenzt, nennt aber keine Zahlen (05:15). Ob die Browser-Automatisierung selbst mit den LinkedIn-Nutzungsbedingungen vereinbar ist, klärt das Video nicht. Kontosperren sind ein reales Risiko, das nicht angesprochen wird.
- **Datenschutz.** Der Actor liefert auch private Mailadressen und Telefonnummern. DSGVO und Regeln zur Direktansprache im DACH-Raum kommen nicht vor; für deutsche Anwender ist das vor dem Einsatz zu prüfen.
- **Skalierung unbelegt.** Parallele Sub-Agenten (02:44) werden nur erwähnt, nicht gezeigt. Die Demo zeigt eher, dass ein Kontakt mehrere Minuten dauert.
- **Wortlaut fehlt.** Die tatsächlich gesendete Notiz ist im Video nicht lesbar; die Wirkung des „unbeholfenen Kompliments“ bleibt Annahme.
- **Freigaben.** Die Apify-Tools stehen auf „Always allow“ (09:30). Wer Kosten und Aktionen kontrollieren will, sollte das restriktiver setzen.
