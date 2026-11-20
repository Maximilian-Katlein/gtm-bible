# Ich habe in 43 Minuten einen KI-Agenten gebaut, der meine Workflows automatisiert (ohne Code)

> **Quelle:** [I built an AI Agent in 43 min to automate my workflows (Zero Coding)](https://www.youtube.com/watch?v=QFc7jXZ2pdE) · Max (Co-Founder und CEO, Gumloop), interviewt von Greg Isenberg · Video · 2026-11-20
> **Sprecher verkauft:** No-Code-Plattform Gumloop für KI-Workflows (Canvas mit Nodes, LLM-Schritte, Integrationen, Webhooks, Interfaces, Chrome-Extension, Custom Nodes), Abrechnung über Credits · **Zielmarkt der Aussagen:** Enterprise, daneben Solo-Gründer und kleine Teams · **Beweislage:** vorbereitete Produktdemo des Gründers mit Anekdoten, keine Ergebniszahlen.

## Worum es geht
Welche wiederkehrenden Abläufe in Vertrieb, Marketing und Recruiting lassen sich mit verketteten KI-Schritten automatisieren, ohne zu programmieren? Max zeigt fünf fertige Workflows: Lead-Recherche nach dem Signup, YouTube-zu-Blog, Wettbewerber-Ad-Analyse, Morgen-Briefing und LinkedIn-Recruiting. Die Bauprinzipien (Aufgaben zerlegen, Entwurf statt Versand, Subflows, Schleifen) sind werkzeugunabhängig übertragbar, die Bedienung ist Gumloop-spezifisch.

## Was man anwenden kann
1. **Signup sofort recherchieren lassen.** Ein Webhook aus dem eigenen Produkt übergibt bei jeder Registrierung die E-Mail-Adresse an einen Workflow (06:44). Der Ablauf: Domain extrahieren, Website scrapen, mit einem günstigen Modell (Claude 3 Haiku, laut Untertitel unsicher) einen Einzeiler über die Firma schreiben, Firmennamen per KI extrahieren, Enrichment abfragen, für Slack formatieren, Outbound-Entwurf in Gmail anlegen (07:26). Laut Max kommt der Slack-Ping etwa 5 Sekunden nach dem Signup (08:13). Bedingung: B2B-Produkt mit Enterprise-Zielgruppe und eigenem Signup-Event.

2. **Entwurf statt Auto-Versand.** Die personalisierte Mail landet als Entwurf im Postfach, nicht beim Lead (08:35). Max sichtete bei etwa 20 Signups pro Tag am Abend alle Entwürfe, schickte die besten 10 und löschte den Rest (08:47). Das gilt nur bei niedrigem Volumen, bei dem manuelle Triage machbar ist. Konversionszahlen fehlen.

3. **Firmennamen per KI statt aus dem Enrichment-Anbieter.** Anbieter wie ZoomInfo liefern oft unsaubere Namen wie „Gumloop YC W24“, die in einer Anrede peinlich wirken (07:44). Ein eigener KI-Extraktionsschritt bereinigt das vor der Mail.

4. **Waterfall-Enrichment.** Ein Node fragt mehrere Datendienste nacheinander ab, bis Felder gefüllt sind: Branche, Umsatz, Land, optional LinkedIn-URL, Web-Traffic, Finanzierung, Mitarbeiterzahl (08:00). Welche Anbieter im Waterfall liegen, bleibt offen.

5. **Große Aufgaben in kleine KI-Schritte zerlegen.** Statt „schreibe einen Blogpost“ in einem Prompt baut Max eine Kette: Digest, Artikel, HTML-Formatierung, Titel (16:24). Max hält die Ergebnisse so für deutlich besser, belegt das aber nicht. Ein sauber gebauter Prompt lohnt sich vor allem, wenn der Flow sehr oft läuft.

6. **Das stärkste Modell an den Anfang.** Qualität kaskadiert: Ein schwacher erster Schritt begrenzt alle folgenden (17:13). Max nutzt OpenAI o1 für den Digest eines 55-Minuten-Podcasts, weil lange Eingaben kritisches Verdichten brauchen, und nimmt höhere Kosten in Kauf (16:41).

7. **YouTube-Link zu Blogartikel.** Transkript per YouTube-Node holen (alternativ Gemini für Speech-to-Text oder Videoanalyse), Füllgespräch per o1 entfernen, Artikel aus Gastgeber-Perspektive mit TL;DR und „avoid jargon“, per KI in HTML formatieren, Quellenlink manuell anhängen, in Ghost veröffentlichen (15:59 bis 17:48). Den Titel extrahiert ein Extract-Data-Node aus nur den ersten rund 1000 Wörtern, weil Podcasts die Kerninformation vorn bringen (18:18). Eignet sich laut Max für Ratgeberformate, schlecht für Demo-Videos (14:22).

8. **Strukturierte Ausgabe statt Bitten im Prompt.** Ein schemabasierter Extraktionsschritt gibt nur den Wert zurück, ohne „Hier ist dein Titel“ (18:38). Gleiches Prinzip für Beträge und Daten aus Belegen (04:25).

9. **Einzel-Workflow per Subflow und Schleife skalieren.** Den fertigen Flow als Node in einen zweiten Flow einbetten, mit einem Google Sheet verbinden und im Loop Mode für jede Zeile ausführen, etwa 1000 YouTube-Links (15:22). Credits steigen linear mit den Läufen.

10. **Wettbewerber-Ads wöchentlich auswerten.** Aktive Meta-Anzeigen eines Wettbewerbers scrapen, jede Anzeige im Loop von Gemini analysieren lassen, alle Einzelanalysen in einen o1-Prompt geben, Gesamtstrategie als HTML-Mail an das Management schicken (22:01). Fehlerhafte Einzelanzeigen werden übersprungen, statt den Lauf abzubrechen (22:22). Zeitplan etwa freitags 9 Uhr (23:06). Als Subflow laut Max für rund 40 Wettbewerber in einem Bericht nutzbar (28:26).

11. **Morgen-Briefing aus dem Kalender.** Täglich 9 Uhr: Termine lesen, Teilnehmer und Firmen recherchieren (Umsatz, Web-Traffic als Größensignal), daraus eine SMS mit drei bis vier Stichpunkten und eine ausführliche Mail erzeugen (26:28). Funktioniert bei externen Teilnehmern, deren Firma über die Mail-Domain auffindbar ist.

12. **Recruiting aus dem Browser.** Per Chrome-Extension auf einem LinkedIn-Profil starten: Name, Titel, Firma, Uni, Ort extrahieren, Hintergrund nach eigenen Kriterien (etwa früher Founding Engineer) zusammenfassen, Twitter und GitHub per Google-Suche plus KI-Auswahl finden, in ein Sheet schreiben, Slack-Ping senden, Mail via Apollo finden, Entwurf ins Gründerpostfach legen (35:36). Auch wenn ein Praktikant den Kandidaten findet, schreibt der Gründer persönlich (36:33).

13. **Eigene API-Keys hinterlegen.** Mit eigenen Schlüsseln (genannt Apollo, Gemini) sinkt der Gumloop-Verbrauch der Ad-Analyse laut Max von etwa 500 auf etwa 50 Credits (29:19). Die Drittanbieterkosten laufen dann über die eigenen Konten.

14. **Kostenpflichtige Workflows nicht öffentlich anbieten.** Wer Workflows per API als eigenes Produkt nutzt, stellt sie hinter Login oder Bezahlschranke, sonst kann jemand tausende Läufe auslösen (25:50). Das gilt für jeden öffentlich erreichbaren KI-Endpunkt.

15. **API-Keys aus Screenshares heraushalten.** Beim Zeigen der Webhook-Definition war ein Schlüssel im Bild (25:05). Webhook-Beispiele vor dem Teilen prüfen oder Schlüssel danach rotieren.

16. **Sticky-Note-Test für Automatisierung.** Lässt sich eine Aufgabe als Schrittliste für einen Praktikanten auf einen Klebezettel schreiben, ist sie laut Max vollständig automatisierbar (39:25). Das gilt für regelbasierte, klar beschreibbare Abläufe.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 9 Mio. USD | Finanzierungsrunde Gumloop, laut Host | Behauptung ohne Beleg |
| ca. 20 pro Tag, 10 verschickt | Signups und abgeschickte Entwürfe in der Frühphase | Anekdote |
| ca. 5 Sekunden | Zeit vom Signup bis zum Slack-Ping | Anekdote |
| ca. 5 Sekunden | YouTube-Link bis veröffentlichter Blogpost | Anekdote |
| unter 20 Minuten | Bauzeit des Blog-Workflows durch Max | Anekdote, Produktexperte |
| 45 bis 60 Minuten | Bauzeit eines komplett eigenen Flows | Anekdote, Produktexperte |
| 389 | Klone des Ad-Workflows nach Twitter-Post | eigene Daten, nur Popularität |
| ca. 500 Credits | Kosten einer Ad-Analyse-Mail („might be“) | Behauptung ohne Beleg |
| ca. 50 Credits | dieselbe Analyse mit eigenen API-Keys | Behauptung ohne Beleg |
| 30.000 Credits für 97 USD | günstigster Plan, Abrechnungszeitraum unklar | Behauptung ohne Beleg |
| ca. 1,62 USD | Rechnung pro Ad-Mail (97 × 500 / 30.000) | rechnerisch korrekt, Eingaben unsicher |
| mindestens 80.000 USD/Jahr | Junior-Ad-Mitarbeiter in San Francisco | Behauptung ohne Beleg |
| ca. 5 | KI-Enthusiasten pro Firma, die Workflows bauen | Anekdote aus Kundengesprächen |
| 2 + 2 | Gumloop-Team: zwei Personen, zwei Praktikanten bis vor Kurzem | Anekdote |
| 1000 Credits | Gratis-Credits nach dem Tutorial | Herstellerangabe |

## Wortlaute
- „you're an expert in ad analysis I want you to come up with a overall analysis of this competitor's ad strategy“ (22:01). Kern des Prompts, der alle Einzelanalysen zu einer Strategieeinschätzung verdichtet.
- „hey I'm Max from gum Loop this is my calendar this is all the research uh explain who I'm going to meet why they might be important to me“ (26:54). Einstieg des Briefing-Prompts: Rolle, Kontext, Daten, Ziel.
- „you're writing in Greg's perspective um I wanted a tldr because I think that's useful“ (17:30). Perspektive und Struktur im Blog-Prompt, ergänzt um „avoid jargon“.
- „make things spacious use a bit of color put Emojis focus on the content type and structure“ (27:57). Formatierungsanweisung für die HTML-Mail der Ad-Analyse.
- „make this integration please“ (31:34). Einzige Anweisung an den Custom-Node-Builder, nachdem die API-Doku von BuiltWith hineinkopiert wurde.

## Grenzen und Widerspruch
- **Keine Ergebnisse.** Antwortraten, Demo-Buchungen oder Umsatz aus dem Signup-Workflow fehlen. Die Aussage, damit den frühen Umsatz erzeugt zu haben, bleibt Anekdote.
- **Verkaufsdemo.** Der Gast zeigt das eigene Produkt in vorbereiteten Flows. Der Host sagt, nicht beteiligt zu sein, ist aber selbst auf Max zugegangen. Ein Vergleich mit Zapier, Make oder n8n findet nicht statt.
- **Prompts unvollständig.** Kein Prompt und keine generierte Outbound-Mail wird vollständig gezeigt. Im Produktivbetrieb braucht es laut Max deutlich mehr Kontext und Beispiel-Mails als in der Demo (36:24).
- **Kosten unsicher.** Max kennt die Umrechnung von Credits in Dollar nicht, die 500 Credits sind geschätzt. Drittanbieterkosten bei eigenen Keys fehlen. Der Vergleich mit 80.000 USD für einen Junior ignoriert Bau, Wartung und Prüfaufwand.
- **Bauzeiten nicht übertragbar.** Unter 20 Minuten und 45 bis 60 Minuten sind Werte des Produktentwicklers, nicht von Einsteigern.
- **Zuverlässigkeit offen.** Keine Fehlerraten, kein Umgang mit Halluzinationen bei Enrichment und Zusammenfassung, keine Prüfung, ob die KI das richtige Twitter- oder GitHub-Profil wählt.
- **Blog-Automatisierung.** Greg verspricht SEO-Traffic und Leads auf Autopilot durch einen Lead-Magnet am Artikelende (19:53), ohne Rankings oder Besucherzahlen. Rechte an Gesprächsinhalten von Gästen und Duplicate Content werden nicht angesprochen.
- **Recht und Datenschutz fehlen.** Scraping von LinkedIn und Meta-Anzeigen, Personenrecherche und Kaltakquise per Mail werden ohne DSGVO, UWG oder Nutzungsbedingungen besprochen. Für den europäischen Markt ist das vor jeder Übernahme zu klären, ebenso Datenhaltung und Hosting. Zur Modellwahl gibt es nur den Hinweis auf eigene Azure-Modelle, nichts zu Open-Weight oder souveräner KI.
- **Sicherheit.** Berechtigungen der Chrome-Extension, der Gmail- und Slack-Anbindung und öffentlicher Webhooks werden nicht behandelt.
- **Roadmap.** Marktplatz für Templates und Cmd+K-Builder für Integrationen sind angekündigt, ohne Termin.
- **Host relativiert.** Greg will Vertrieb nicht vollständig automatisieren und setzt im ersten Call auf den Menschen (41:25). Das passt zu Max' Entwurfsprinzip.
