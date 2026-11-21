# Oleg Melnikov

Oleg Melnikov zeigt, wie man mit Claude Cowork, Browser-Agenten und Apify-Scrapern B2B-Kaltakquise über LinkedIn baut, vom Lead-Scraping bis zur personalisierten Vernetzungsnotiz.

Stand: 2026-11-21 · 1 Quelle

Verkauft: in den bisherigen Quellen nicht genannt.

## Kernideen

*Bisher stützt sich die Seite auf eine einzige Quelle. Die folgenden Ideen sind dort zentral, ob Melnikov sie wiederholt vertritt, ist noch offen.*

### Bewusst unpolierte Nachrichten, damit sie auffallen

Glatte KI-Texte gehen laut Melnikov in der Masse unter. Deshalb verlangt der Prompt einen einzigen Satz mit einem sehr spezifischen Kompliment, das ruhig etwas unbeholfen wirken darf.

> It all looks too much polished, too much generic, and for that reason, we want to stand out here.

*Behauptung ohne Beleg: Eine Messung, dass holprige Notizen besser angenommen werden, legt Melnikov nicht vor.*

Belege: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (03:39, 01:11)

### Der Agent recherchiert und schreibt, der Mensch gibt frei

Die personalisierte Nachricht landet zuerst in der Lead-Tabelle und wird erst nach menschlicher Freigabe gesendet. Das senkt das Risiko von Fehltreffern im Namen des Absenders.

> You might want to make it write the personalized message first in the table and send only after your approval.

Belege: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (06:39)

### Günstige Werkzeugkette statt teurer Sales-Datenbanken

Statt Apollo nutzt Melnikov Apify-Scraper, die Claude Cowork über den Apify-MCP-Server selbst aufruft. Das Argument ist durchgehend der Preis: wenige Dollar für Tausende Leads, ein Claude-Pro-Abo für die Automatisierung.

Belege: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (05:02, 05:43, 07:22, 08:29)

## Methoden und Abläufe

### Kampagnenablauf in Claude Cowork

1. **Kontext geben:** Angebot, Geschäft und Zielgruppe im Startprompt erklären.
2. **Leads scrapen:** Cowork ruft über den Apify-MCP-Server einen Scraper auf (z. B. Apollo-Ersatz oder Social-Media-Scraper) und legt die Ergebnisse als Excel-Datei im Arbeitsordner ab.
3. **Lead-Liste ausgeben lassen** und prüfen.
4. **Outreach starten:** Je Profil recherchiert der Agent und schreibt eine Vernetzungsnotiz.
5. **Freigabe:** Nachrichten zuerst in die Tabelle schreiben lassen, erst nach Zustimmung senden.

Quelle: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (09:36, 06:39)

### Recherche für eine personalisierte Vernetzungsnotiz

*Bedingung: B2B-Erstkontakt über LinkedIn, ein Profil je Agentenaufgabe.*

- Recherchebasis ist das Profil plus die letzten 10 Posts. Der Agent liest erst den Profilkopf, dann den Aktivitäts-Feed Post für Post.
- Als Aufhänger dient der Post mit der stärksten Resonanz. In der Demo begründet der Agent die Wahl mit Likes, Kommentaren und der Nische der Person. Das setzt voraus, dass die Zielperson regelmäßig postet.

> study her profile and last 10 posts

Quelle: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (01:22, 03:17), Anekdote

### Klickpfade für Browser-Agenten ausschreiben

Bei UI-Automatisierung schreibt Melnikov den Klickpfad explizit in den Prompt, etwa welche Schaltfläche im LinkedIn-Popup zu klicken ist („Add a note“), statt das dem Agenten zu überlassen.

Quelle: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (01:11), Anekdote

### Werkzeugeinrichtung

- **Claude for Chrome:** Claude Cowork steuert über diese Erweiterung den Browser und klickt sich durch LinkedIn. Laut Melnikov langsam, vermutlich per Screenshot und anschließender Klickentscheidung. Voraussetzung: bezahlter Claude-Pro- oder Max-Plan und Google Chrome.
  > I tried to use it with other browsers, it doesn't work.
- **Apify-MCP-Server:** in Cowork unter Settings, Connectors installieren und mit dem Apify-API-Token konfigurieren. Voraussetzung: Apify-Konto und Claude-Desktop-App.
- **Apify-Actor „Leads Finder“ von Brave Leads:** als günstiger Apollo-Ersatz, mit JSON-Filtern für Seniorität (CEO, Founder), Branchen-Keywords und verifizierte Mails. Gedacht für kleine Budgets und SMB-Zielgruppen. *Die Actor-Bewertung beruht auf nur 3 Bewertungen.*

Quelle: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (07:46, 08:29, 05:43)

## Formulierungen und Formate

### Stilvorgabe für die Vernetzungsnotiz

*Format: LinkedIn-Vernetzungsnotiz mit 300-Zeichen-Limit.*

> this message should be just one sentence, making a non-cheesy and non generic complement, something super specific and maybe even a bit awkward

Quelle: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (01:11)

### Startprompt für eine Kampagne

> Do the web scraping using Apollo or using Apify for some other social media. Give me the whole list of leads, and then let's do the cold outreach.

Vorher werden Angebot, Geschäft und Zielgruppe erklärt.

Quelle: [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (09:36)

## Zahlen, die sie nennt

| Zahl | Kontext | Beleg | Quelle |
|---|---|---|---|
| 0,226 USD für 100 Leads in 25 Sekunden | gezeigter Scraper-Lauf, rechnerisch 2,26 USD je 1.000 Leads | eigene Daten | [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (05:02) |
| 3.000 Gratis-Leads aus 5 USD Apify-Credits | Apify Free Tier; im Video zuerst als 5.000 genannt, dann korrigiert | eigene Daten, rechnerisch nicht stimmig | [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (05:02) |
| 19 USD pro Monat für Claude Pro | ein einziger B2B-Abschluss finanziere mindestens ein Jahr Cowork | Behauptung ohne Beleg | [Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md) (07:22) |

> So, you can get 3,000 leads for free. The beginning of the video, I told you 5,000, it was a mistake, it's actually 3,000

*Einordnung: Bei 2,26 USD je 1.000 Leads ergeben 5 USD Credits eher rund 2.200 Leads, nicht 3.000.*

## Wo Vorsicht geboten ist

- **Keine Ergebnisse belegt.** Die Demo zeigt eine einzige versendete Vernetzungsanfrage im Status „Pending“. Annahmequoten, Antworten, gebuchte Calls oder Abschlüsse fehlen, ebenso ein Beleg für die Skalierung über parallele Sub-Agenten. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 04:02)
- **Datenqualität nur für Kleinstfirmen gezeigt.** Die gescrapten Leads sind überwiegend Firmen mit 0 bis 1 Mitarbeitenden. Für Mittelstand oder Enterprise ist die Qualität des Scrapers nicht belegt. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 06:03)
- **LinkedIn-Regeln und Kontosperren.** Melnikov erwähnt Vernetzungslimits, nennt aber keine Zahlen und klärt nicht, ob die Browser-Automatisierung selbst regelkonform ist. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 05:15)
  > but it's still more than you can actually send connections to through LinkedIn because otherwise you will be violating their policies
- **Datenschutz im DACH-Raum.** Der Scraper liefert auch private Mailadressen und Telefonnummern. DSGVO und Regeln zur Direktansprache werden im Video nicht behandelt und sind vor dem Einsatz zu prüfen. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 04:57)
- **Wirkung unpolierter Texte ungemessen.** Die Kernidee der bewusst holprigen Nachricht ist eine Annahme ohne Daten. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 03:39)
- **Widersprüchliche Gratis-Lead-Zahl.** Erst 5.000, dann 3.000, rechnerisch eher 2.200. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 05:02)
- **Dünne Werkzeugbewertung.** Der empfohlene Apify-Actor hat nur 3 Bewertungen. ([Claude für Cold Outreach](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md), 05:43)

## Alle Quellen

- 2026-11-21 · [How I Use Claude For Cold Outreach (B2B Sales)](../quellen/2026/11/2026-11-21-how-i-use-claude-for-cold-outreach-b2b-sales.md)
