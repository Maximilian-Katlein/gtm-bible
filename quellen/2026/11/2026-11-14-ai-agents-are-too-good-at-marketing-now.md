# KI-Agenten sind inzwischen zu gut im Marketing

> **Quelle:** [AI Agents are too good at marketing now](https://www.youtube.com/watch?v=uJuxenfe-NU) · Cody Schneider, Graft (Host: Greg Isenberg) · Video · 2026-11-14
> **Sprecher verkauft:** Graft (graft.com), eine Plattform für agentengestütztes Marketing („Marketing Engineering Cloud“); im Video wird zudem die laufende Seed-Finanzierung der Gründer erwähnt · **Zielmarkt der Aussagen:** Startups, KMU und Mid-Market-Marketingteams in B2B SaaS, E-Commerce und Finanzdienstleistung · **Beweislage:** Live-Demos und Erfahrungswerte des Sprechers, keine Messreihen und keine A/B-Daten.

## Worum es geht
Das Video zeigt, wie ein kleines Marketingteam eine Umgebung baut, in der KI-Agenten Anzeigen recherchieren, erzeugen, hochladen und auswerten. Im Zentrum stehen Datenarchitektur, Kostenkontrolle bei KI-Video und die Frage, wie man Werbekonten dabei nicht gefährdet. Relevant ist das für Startups und Growth-Teams, die Paid Social oder Google Ads betreiben und das Creative-Volumen deutlich erhöhen wollen.

## Was man anwenden kann
1. **Drei Voraussetzungen vor dem ersten Agenten.** Ein Marketing-Agent braucht laut Schneider erstens Zugriff auf Unternehmensdaten, zweitens Werkzeuge über APIs und drittens Schreibrechte auf den Werbeplattformen (07:30). Fehlt eine der drei Komponenten, arbeitet der Agent nur halb.

2. **Daten zentral sammeln, nicht live abfragen.** Airbyte als Open-Source-Pipeline zieht Daten aus Facebook Ads, Google Analytics, HubSpot und PostHog in ein Data Warehouse, im Beispiel ClickHouse (10:05, 11:40). Der Agent liest nur aus dem Warehouse und läuft so nicht in Ratenbegrenzungen der Plattformen.

3. **Lesen und Schreiben trennen.** Die Facebook- und Google-APIs nutzt der Agent ausschließlich zum Schreiben: Creatives hochladen, Anzeigen abschalten, Anzeigen verschieben (14:00). Als Gegenbeispiel nennt Schneider einen Fall, in dem ein Agent Tausende Anfragen pro Sekunde schickte und das Konto wegen Verstoßes gegen die API-Nutzungsbedingungen gesperrt wurde (15:20).

4. **Anzeigen bis zum Kundenwert verfolgen.** Werden Werbedaten im Warehouse mit dem Zahlungsanbieter verknüpft, lässt sich je Anzeigenmotiv ablesen, ob daraus Kunden mit höherem Lifetime Value entstehen (12:20). Bedingung ist eine durchgehende Datenkette von der Anzeige bis zur Zahlung.

5. **Suchbegriffe maschinell prüfen.** Ein Google-Ads-Agent lässt ein LLM 5.000 Suchbegriffe in rund 20 Sekunden auf Kaufabsicht bewerten, bevor Budget auf unpassende Landingpages fließt (18:40). Gilt für Suchkampagnen mit großem Suchbegriffsvolumen.

6. **Static Ads in einer festen Reihenfolge erzeugen.** Der gezeigte Skill `/static-ads` liest den Markenstil der Ziel-URL aus, durchsucht die Facebook-Werbebibliothek, recherchiert Schmerzpunkte auf Reddit, schlägt fünf Konzepte vor und generiert danach die Grafiken (23:50). Anschließend lädt der Agent sie per Befehl in ein neues Anzeigen-Set hoch (29:40).

7. **KI-Video nie nur mit Skript beauftragen.** Wer Seedance nur ein Skript schickt, bekommt erfundene Bild- und Tondetails und zahlt für unbrauchbare Renderings (32:00). Stattdessen gehen drei Eingaben gleichzeitig an das Modell: das exakte Skript, eine MP3 aus einem Voice-Clone bei fal und ein hochauflösendes Referenzbild (32:20).

8. **In niedriger Auflösung rendern, dann hochskalieren.** Ein 1080p-Render bei Seedance kostet nach Erinnerung des Sprechers etwa 14 US-Dollar. Er rendert in 480p und skaliert anschließend mit FFmpeg hoch, inklusive leichtem Weichzeichner (34:00).

9. **Aussprachefehler automatisch reparieren.** Ein Wort-für-Wort-Transkript der synthetischen Stimme deckt falsch gesprochene Markennamen auf, im Beispiel „Calendly“. Der Agent isoliert die Zeitstempel und ersetzt nur diese Audiosequenz (34:50).

10. **Plastik-Look bei Avataren vermeiden.** Als Vorlage dient das Foto eines echten Creators, das in Hintergrund, Alter oder Ethnie variiert wird (36:50). Untertitel und Motion Graphics fügt danach Mirage Tesseract auf Basis des Transkripts ein (37:40).

11. **Menschliche Creator per API einbinden.** Über Tribe oder SideShift verschickt der Agent Skripte an echte UGC-Creator, die pauschal etwa 40 US-Dollar pro Video erhalten (40:00). Ein Creator-Manager bleibt als menschliche Freigabestufe vor der Veröffentlichung (02:40).

12. **Compliance-Schleife für regulierte Branchen.** Bei einem Kunden aus dem Finanzbereich prüft ein Agent mit Bildmodell jede Grafik gegen Compliance-Regeln und korrigiert sie in zwei bis drei rekursiven Durchläufen (43:50). Für gezielte Bildänderungen bevorzugt Schneider ChatGPT Image 2.5, weil es das Ausgangsbild weitgehend erhält (46:00).

13. **Creative-Volumen für Meta stark erhöhen.** Für Metas Auslieferungsalgorithmus Andromeda steigerte ein Team von 10 auf 300 Anzeigen pro Monat, hochgeladen in Kohorten von 30 (47:30). In einem B2B-SaaS-Fall brachte eine Kohorte zwei Demo-Buchungen zu je etwa 50 US-Dollar bei sonst rund 150 US-Dollar (48:00).

14. **Prompts als Daten speichern.** Jeder Generierungs-Prompt wird als JSON-Blob in der Datenbank abgelegt und mit den Performancedaten der Anzeige verknüpft (48:30). So lässt sich auswerten, welche Prompt-Parameter zu welchen Ergebnissen führen.

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 90 Minuten | Podcast-Länge, die Mirage Tesseract in einem Durchgang schneidet (06:10) | Erfahrung des Sprechers |
| 5.000 Suchbegriffe in 20 s | LLM-Prüfung auf Kaufabsicht in Google Ads (18:40) | Erfahrung des Sprechers |
| ca. 14 USD | Kosten eines 1080p-Renders bei Seedance, vom Sprecher selbst als ungefähr markiert (34:00) | Erfahrung des Sprechers |
| ca. 4,75 USD, künftig ca. 3 USD | Kosten einer KI-UGC-Videoanzeige im eigenen Setup (39:00) | Erfahrung des Sprechers, ohne Setup- und Abokosten |
| 500 USD und mehr | Vergleichskosten mit Creator, Cutter und Designer (39:00) | Schätzung ohne Beleg |
| ca. 40 USD | Pauschale je Video für menschliche Creator über SideShift (40:00) | Erfahrung des Sprechers |
| 2 bis 3 Schleifen | Compliance-Korrekturen bei einem Finanzkunden (43:50) | Kundenfall |
| 10 auf 300 Anzeigen/Monat, Kohorten zu 30 | Volumensteigerung für Meta (47:30) | Kundenfall |
| 2 Demos zu ca. 50 USD statt ca. 150 USD | Ergebnis einer Kohorte bei B2B SaaS (48:00) | Kundenfall, Einzelbeispiel |

## Wortlaute
- „stop guessing which idea to build. Every idea is scored on demand, pain, and timing.“ (26:50) Vom Agenten erzeugter Hook für ein Ideen-Tool: Schmerz benennen, dann Mechanismus.
- „your chat GPT ideas are generic.“ (27:05) Hook, der eine bekannte Alternative direkt abwertet.
- „Your product is getting a second user.“ (41:45) Hook für eine Strategieagentur, die KI-Agenten als neue Nutzergruppe rahmt.
- „finally understand the code nobody wrote down.“ (42:00) Hook für einen Code-Editor, der ein konkretes Alltagsproblem von Entwicklern trifft.

## Grenzen und Widerspruch
- Das Video ist an mehreren Stellen Produktwerbung für Graft. Die Teamfunktionen (19:50, 50:30) sind Herstellerangaben.
- Die Kostenrechnung von etwa 5 gegenüber 500 US-Dollar enthält keine Abos, keinen Engineering-Aufwand für Pipeline und Warehouse und keine Kosten für Fehlversuche.
- Die Aussage, KI-Avatare performten in Meta-Ads teils besser als echte Menschen, ist nicht durch A/B-Ergebnisse belegt.
- Swipe Warehouse (20:50) und Creative-Director-Agent mit Ogilvy-Büchern und 100 Podcasts (49:30) sind Konzepte ohne Wirksamkeitsnachweis.
- Die Demo-Buchungen zu 50 US-Dollar sind ein einzelner Kundenfall. Bezugsbasis, Laufzeit und Budget fehlen.
- Die vollständigen Skill-Dateien und die Einrichtung der Meta- und Google-Ads-APIs liegen in externen Links und einem Notion-Dokument, nicht im Video.
- Mehrere Werkzeugnamen stammen aus einem automatischen Transkript und sind in der Schreibweise unsicher (etwa „Grokbot“, „Kai AI“).
- Kennzeichnungspflichten für KI-Avatare, Datenschutz bei der Übertragung von CRM- und Zahlungsdaten an Drittanbieter und Plattformregeln zu synthetischen Testimonials werden nicht behandelt.
- Ob die Compliance-Schleife eine fachliche Prüfung in regulierten Branchen ersetzt, sagt die Quelle nicht.
