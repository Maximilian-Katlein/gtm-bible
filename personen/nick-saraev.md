# Nick Saraev

Nick Saraev zeigt, wie man mit No-Code-Automatisierung (n8n, Apify, LLMs) Kaltakquise im großen Stil baut. Man hört Saraev zu wegen der konkreten, nachbaubaren Workflows für tief personalisierte Kaltmails.

Stand: 2026-11-20 · 1 Quelle

Verkauft: laut Quelle ein Outreach-System an Webdesign-Agenturen (die gezeigte Kaltmail-Kampagne bewirbt es); das Video selbst dient als Lead-Magnet mit kostenloser Vorlage („FREE TEMPLATE“).

## Kernideen

### Personalisierung heißt: die ganze Website lesen, nicht nur die Startseite

Für jede Zielfirma werden alle erreichbaren Unterseiten gescrapt, jede einzeln von der KI zusammengefasst, und erst aus allen Zusammenfassungen entsteht der Einstieg der Mail. Saraev grenzt das ausdrücklich von der üblichen Praxis ab, nur eine Seite zu lesen.

> „you wouldn't just scrape one page like most other people are doing, you'd actually scrape all the pages on the website“

*Bedingung: Zielfirmen mit inhaltsreicher eigener Website, SMB. Beleg: Behauptung ohne Beleg.* [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (10:26)

### Die Mail soll aussehen, als hätte ein Mensch recherchiert

Der rote Faden fast aller Taktiken im Video: Jedes Signal von Massenversand wird entfernt, damit der Empfänger an manuelle Recherche glaubt. Saraev begründet das so:

> „when you can imply that you're a real human being and you can convince someone of that, they're a lot more likely to take the rest of your pitch seriously.“

Belege aus derselben Quelle, die alle dieser Idee dienen:
- Kleine, nicht offensichtliche Details von Unterseiten loben statt generischem Lob (24:54)
- Firmennamen und Orte kürzen, weil volle Namen nach Scraping aussehen (25:03)
- Flexible Platzhalter, die die KI paraphrasiert, statt starrer Merge-Felder (24:03)
- Demutsgeste „Am new to this“ in der Mail (02:44)
- Auf bereits angeschriebene Kollegen derselben Firma verweisen (27:42)

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (29:36)

*Einordnung: Das Ziel ist ausdrücklich, manuelle Arbeit vorzutäuschen. Siehe „Wo Vorsicht geboten ist“.*

### Leads sind nie der Engpass, also 80/20 bauen

Weil Leads über Apollo und Apify billig nachzuladen sind, nimmt Saraev hohe Verluste im Trichter bewusst in Kauf und optimiert nicht auf jeden einzelnen Datensatz.

> „To me, the leads are never the bottleneck here, just because we have platforms like Apollo and Apify“

*Gilt nicht für enge Nischenmärkte mit wenigen Zielkunden. Bedingung: großer Adressmarkt, SMB. Beleg: Behauptung ohne Beleg.* [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (28:31)

## Methoden und Abläufe

### Pipeline für tief personalisierte Kaltmails (n8n)

1. **Leads holen:** Apollo-Suchergebnisse per HTTP-POST aus n8n an den Apify-Endpunkt `run-sync-get-dataset-items` schicken; der gibt die Lead-Daten direkt zurück. Ein Lauf lieferte 96 Leads. *Voraussetzung: Apify-Konto mit API-Token. Ob das mit den Nutzungsbedingungen von Apollo vereinbar ist, wird nicht geprüft.* (05:00)
2. **Filtern:** Nur Leads mit E-Mail und Website behalten (Trichterzahlen siehe unten).
3. **Websites scrapen:** In n8n „Follow Redirects“ mit bis zu 21 Weiterleitungen aktivieren und Fehler über den Error-Output weiterlaufen lassen, sonst bricht der Lauf ab. *Beleg: Anekdote.* (07:50)
   > „If you don't do this, I find that in practice, a lot of the websites are going to error out because most of them redirect.“
4. **Unterseiten vorbereiten:** HTML in Markdown umwandeln und auf etwa 5.000 Zeichen kürzen. Eine einzelne Seite mit knapp 19.000 Zeichen ließ den Lauf im Test hängen. *Gilt für Zusammenfassungen pro Unterseite, nicht für Detailanalysen.* (21:41)
   > „Let's just go like 5,000. You don't need much more than that realistically.“
5. **Pro Unterseite zusammenfassen**, dann aus allen Zusammenfassungen den Icebreaker generieren. (10:26)
6. **Icebreaker per Few-Shot erzeugen** (siehe unten).

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md)

### Few-Shot-Aufbau in fünf Nachrichten

1. Systemprompt
2. Anweisung
3. User-Nachricht mit Beispiel-Input aus einem echten Testlauf
4. Assistant-Nachricht mit einem perfekten Beispiel-Output
5. Der echte Input

> „then a user prompt where I give it an example of an input, then an assistant prompt where I give it an example of an output“

*Beleg: eigene Daten.* [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (25:58)

### Prompt-Regeln für den Icebreaker

- **Keine Standardfloskeln:** Kleine, nicht offensichtliche Details von Unterseiten wählen, etwa eine Filterfunktion oder eine Fax-Option. (24:54)
  > „Do not say cookie cutter stuff like love your website or love your take on marketing.“
- **Namen kürzen:** „Love Mayo“ statt „Mayo Inc.“, „San Fran“ statt „San Francisco“. *Bedingung: englischsprachige Kaltmails.* (25:03)
  > „If you write the whole company name, if you say hello, I love Mayo Incorporated. Odds are you scraped Mayo Incorporated“
- **Flexible Platzhalter statt Merge-Felder:** Variablen wie `{thing}` oder `{someImpliedBeliefTheyHave}` vorgeben, die die KI frei füllt und paraphrasiert. *Beleg: Anekdote.* (24:03)
  > „If you tell AI like, "Hey, I want you to write this casually in short form." What it can do is it can paraphrase those things“

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md)

### Mehrere Kontakte pro Firma verknüpfen

Mehrere Personen derselben Firma anschreiben und im Text auf den bereits kontaktierten Kollegen verweisen. Das soll glaubhafter machen, dass ein Mensch schreibt. *Bedingung: mehrere Kontakte pro Firma im Datensatz. Beleg: Behauptung ohne Beleg.*

> „"Hey, David, I just reached out to Zayn and I wanted to follow up with you as well."“

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (27:42)

### Testen in n8n

Gepinnte Daten beschleunigen Tests und schonen Rate Limits, täuschen aber falsche Datensatzmengen vor. Vor dem Einsatz deshalb End-to-End mit frischen Daten testen. *Beleg: Anekdote.*

> „if you pin all the nodes and only test off of pin nodes, sometimes it bugs out“

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (20:36)

## Formulierungen und Formate

### Icebreaker-Vorlage in zwei Absätzen

1. Lob eines konkreten Details plus Überleitung.
2. Eingeständnis der Recherche, eine aus der Website abgeleitete Priorität und der Pitch, verknüpft mit einer vermuteten Überzeugung des Empfängers.

> „Hey {name}. Love {thing}—also doing/like/a fan of {otherThing}. Wanted to run something by you.“

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (23:38)

### Gezeigte Kaltmail an Webdesign-Agenturen

- **Betreff:** nur Vorname plus „q“
- Icebreaker
- Demutsgeste („bin neu darin“)
- Pitch mit Kostenhinweis
- Eigener Social Proof
- Interessensfrage zum Schluss

> „Am new to this, so please bear with me. But I put something interesting together a few months ago that works well.“

[Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (02:44)

## Zahlen, die sie nennt

| Zahl | Kontext | Beleg | Quelle |
|---|---|---|---|
| 100 → 28 → 21 | Aus etwa 100 Apollo-Leads blieben 28 mit E-Mail und Website, davon 21 scrapbar | eigene Daten | [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (07:22) |
| ca. 20 je 100 | Faustregel für nutzbare Leads; deshalb Zielgruppen um 10.000 für etwa 2.000 Kontakte | eigene Daten | ebd. (07:22) |
| 96 Leads | Ein Lauf über den Apify-Endpunkt | eigene Daten | ebd. (05:00) |
| ca. 5.000 Zeichen | Empfohlene Kürzung je Unterseite; 19.000 Zeichen ließen den Lauf hängen | eigene Daten | ebd. (21:41) |
| bis zu 21 | Weiterleitungen bei „Follow Redirects“ | Anekdote | ebd. (07:50) |
| 4 % Antwortrate, über 30 qualifizierte Leads | Kampagne an Webdesign-Agenturen; Versandvolumen nicht genannt | eigene Daten | ebd. (02:51) |
| 5 bis 10 % Antwortrate | „routinemäßig“ mit dieser Personalisierung; ohne Volumen, Zeitraum oder Definition | Behauptung ohne Beleg | ebd. (01:57) |

> „So, you're going to feed in, you know, about 100 or so and you're going to get about 30.“

> „this specific pitch has already got me a 4% reply rate and something like over 30 qualified leads“

## Wo Vorsicht geboten ist

*Antwortraten ohne Basis:* Die 5 bis 10 % sind eine pauschale Behauptung ohne Volumen, Zeitraum oder Definition, was als Antwort zählt. Bei den 4 % fehlt die Zahl der versendeten Mails. Die Kampagne bewirbt zudem das System, das Saraev verkauft. [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (01:57, 02:51)

*Täuschung als Designziel:* Das System soll manuelle Recherche vortäuschen (gekürzte Namen, „bin neu darin“, Verweis auf Kollegen). Das kann Vertrauen beschädigen, sobald der Empfänger es durchschaut. [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (29:36)

*Rechtslage in DACH und EU:* Kaltmails an Unternehmen sind nach UWG und DSGVO enger begrenzt als in den USA. Die Quelle spricht das nicht an. Auch ob das Scrapen von Apollo-Suchergebnissen über Apify mit den Nutzungsbedingungen von Apollo vereinbar ist, bleibt offen. [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (05:00, 29:36)

*Verschwendung von Leads:* Die 80/20-Haltung setzt einen großen Adressmarkt voraus. In engen Nischen mit wenigen Zielkunden verbrennt man so den Markt. [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (28:31)

*Sprachgebundene Taktiken:* Kürzungen wie „San Fran“ oder der Betreff „{Vorname} q“ sind auf englischsprachige Mails zugeschnitten und lassen sich nicht direkt auf deutsche Kaltmails übertragen. [Deep-Personalized Cold Emails](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) (25:03, 02:44)

## Alle Quellen

- 2026-11-20 · [I Deep-Personalized 1000+ Cold Emails Using THIS AI System (FREE TEMPLATE)](../quellen/2026/11/2026-11-20-i-deep-personalized-1000-cold-emails-using-this-ai-system-fr.md) · Learnings L-20261120-088 bis L-20261120-104
