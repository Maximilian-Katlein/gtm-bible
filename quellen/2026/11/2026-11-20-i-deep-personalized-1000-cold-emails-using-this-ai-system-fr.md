# Ich habe über 1.000 Kaltmails mit diesem KI-System tief personalisiert (kostenlose Vorlage)

> **Quelle:** [I Deep-Personalized 1000+ Cold Emails Using THIS AI System (FREE TEMPLATE)](https://www.youtube.com/watch?v=oAWe5wFwHlo) · Nick Saraev, LeftClick und Maker School · Video · 2026-11-20
> **Sprecher verkauft:** Maker School (kostenpflichtige Community für den Aufbau einer AI-Automation-Agentur, Geld zurück ohne Kunden in 90 Tagen); im Kampagnenbeispiel ein Outreach-System für Webdesign-Agenturen · **Zielmarkt der Aussagen:** SMB, vor allem lokale Dienstleister und Agenturen · **Beweislage:** Workflow vollständig gezeigt, Ergebniszahlen sind Eigenangaben ohne Versandvolumen.

## Worum es geht
Wie man in n8n aus einer Apollo-Suche automatisch mehrzeilige, stark personalisierte Einstiege für Kaltmails erzeugt, indem man nicht nur die Startseite, sondern viele Unterseiten jeder Firmenwebsite scrapt und per KI verdichtet. Gedacht für Agenturen und Freelancer, die Kaltmails an kleine Firmen mit eigener Website senden.

## Was man anwenden kann
1. **Leads über Apify statt Apollo-Export holen.** Apollo-Such-URLs stehen in einem Google-Sheet-Tab „Search URLs“. n8n liest alle Zeilen und schickt jede per HTTP-POST an den Apify-Endpunkt `run-sync-get-dataset-items` (Header: Bearer-Token). Saraev begründet das damit, dass Leads direkt bei Apollo teuer seien (00:13, 05:00). Ein Lauf lieferte 96 Leads (06:08).
2. **Hart filtern, Verluste einplanen.** Nur Leads mit E-Mail UND Website-URL laufen weiter: 96 wurden zu 28. Von 28 Websites ließen sich 21 scrapen. Faustregel des Sprechers: etwa 20 personalisierbare Leads je 100 Apollo-Leads. Daher Zielgruppen um 10.000 wählen, um rund 2.000 nutzbare Kontakte zu bekommen (07:22, 08:33, 08:49). Gilt nur, wenn der Adressmarkt groß und Leads billig sind.
3. **HTTP-Request robust einstellen.** Follow Redirects mit Max Redirects 21 aktivieren, sonst brechen viele Seiten ab. On Error auf „Continue (using error output)“ stellen und den Fehlerzweig ignorieren, weil manche Seiten Scraping blockieren (07:50, 08:10).
4. **Unterseiten statt nur Startseite.** HTML-Node extrahiert alle `a`-Tags (Attribut `href`, als Array). Pro Lead in einer Loop-Over-Items-Schleife: Split Out der Links, Filter auf Links, die mit „/“ beginnen, Duplikate entfernen, Basis-URL voranstellen, Seite abrufen (13:09 bis 16:34). Im Test blieben von 270 Links 121; gescrapt wurden 39 Seiten. Der Relativ-Filter ist ein grober Näherungswert: absolute interne Links fallen weg.
5. **Tokens sparen.** HTML in Markdown umwandeln und den Text auf 5.000 Zeichen kürzen. Auslöser war eine Seite mit 18.898 Zeichen, die den Lauf hängen ließ (17:18, 21:26, 21:41). Faustregel: ein Token sind etwa vier Zeichen.
6. **Zweistufige KI.** Stufe 1: GPT-4.1 fasst jede Unterseite als zweiabsätziges Abstract im JSON-Format zusammen, nüchterner Ton, leere Seiten als „no content“ (18:49). Ein Aggregate-Node bündelt alle Abstracts eines Leads. Stufe 2 erzeugt daraus den Icebreaker (23:16). Neue OpenAI-Konten mit niedriger Stufe laufen dabei leicht ins Rate Limit.
7. **Few-Shot-Prompt in fünf Nachrichten.** System, Anweisung, Beispiel-Input (Profil plus Abstracts aus einem Testlauf), Assistant mit perfektem Beispiel-Output, dann der echte Input (25:58). Der Beispiel-Output leitet einen Wert der Zielfirma aus der Website ab und knüpft den Pitch an die Priorität einer genannten Person.
8. **Flexible Platzhalter statt Merge-Felder.** Die Vorlage enthält Platzhalter wie `{thing}` oder `{someImpliedBeliefTheyHave}`, die die KI frei füllt und umformuliert. Saraev hält das für glaubwürdiger als feste Variablen (24:03). Dazu Regeln: Firmennamen und Orte kürzen („San Fran“, „BC“), kleine, nicht offensichtliche Details wählen, kein Floskel-Lob (24:34).
9. **Kurze, informelle Mail.** In der gezeigten Instantly-Sequenz lautet der Betreff nur „Vorname, q“. Auf den Icebreaker folgt eine Demutsgeste („bin neu darin“), dann ein kurzer Pitch mit Kostenhinweis, eigenem Social Proof und einer Interessensfrage (02:44).
10. **Mehrere Personen pro Firma.** Duplikate nach Firma werden bewusst nicht entfernt. In der Mail kann man auf den bereits angeschriebenen Kollegen verweisen, was menschlicher wirke (27:33, 27:42).
11. **Arbeitsweise in n8n.** Manueller Trigger für Tests, Daten pinnen, um Google-Sheets-Rate-Limits zu schonen, aber vor dem Abschluss End-to-End mit frischen Daten testen, weil gepinnte Daten falsche Datensatzmengen vortäuschen können (04:18, 20:36). Ergebnis per „Append Row“ mit manuellem Spalten-Mapping ins Sheet, von dort Import in Instantly.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 5 bis 10 % | Antwortrate „regelmäßig“ in eigenen Kaltmail-Kampagnen | Behauptung ohne Beleg, keine Basis genannt |
| 72.000 USD/Monat | Umsatz der eigenen Agentur, unter anderem mit dieser Methode | Behauptung ohne Beleg |
| 4 %, über 30 qualifizierte Leads | Kampagne an Webdesign-Agenturen | Eigene Daten, Versandvolumen fehlt |
| 96 → 28 | Apollo-Leads vor und nach Filter E-Mail plus Website | Eigene Daten, ein Testlauf |
| 28 → 21 | Websites, die sich scrapen ließen | Eigene Daten, ein Testlauf |
| 20 von 100 | Faustregel nutzbare Leads | Hochrechnung des Sprechers |
| 270 → 121 | Links vor und nach Relativ-Filter | Eigene Daten |
| 39 | gescrapte Unterseiten im Test | Eigene Daten |
| 18.898 Zeichen | längste Seite, die den Lauf blockierte | Eigene Daten |
| 5.000 Zeichen | gewählte Kürzung je Seite | Bauchentscheidung |

## Wortlaute
- „Hey {name}. Love {thing}—also doing/like/a fan of {otherThing}. Wanted to run something by you.“ (23:38) Erster Absatz der Icebreaker-Vorlage.
- „I hope you'll forgive me, but I creeped you/your site quite a bit, and know that {anotherThing} is important to you guys“ (23:38) Zweiter Absatz: offenes Eingeständnis der Recherche plus vermutete Priorität.
- „Your task is to provide a two-paragraph abstract of what this page is about.“ (18:49) Kern des Prompts für die Seitenzusammenfassung.
- „Do not say cookie-cutter stuff like "Love your website!" or "Love your take on marketing!"“ (24:34) Regel gegen generisches Lob.
- „hey Cali, love how L2 makes it easy to filter by acreage. also a fan of your property update email option.“ (02:07) Fertiger Icebreaker an eine Maklerin.
- „Am new to this, so please bear with me.“ (02:44) Demutsgeste direkt nach dem Icebreaker.
- „Subject: Katie, q“ (02:44) Betreff aus Vorname plus Kürzel für „question“.

## Grenzen und Widerspruch
- Die Antwortraten nennen weder Versandmenge, Zeitraum noch ob alle oder nur positive Antworten zählen. Ein Vergleich mit einer Kampagne ohne Personalisierung fehlt.
- Belegt ist das Vorgehen nur für kleine lokale Firmen (Makler, Agenturen) in den USA. Für Konzerne mit großen, CMS-lastigen Websites oder für den DACH-Raum gibt es keine Daten.
- Die Methode setzt auf massenhafte Verluste („quick and scrappy“). Das funktioniert nur, wenn der Adressmarkt groß ist. In engen B2B-Nischen verschwendet man so knappe Kontakte.
- Rechtlich nicht angesprochen: Scraping von Apollo über Dritte und Websites mit Schutzmechanismen sowie unaufgeforderte Werbemails. In der EU sind Kaltmails an Unternehmen nach UWG und DSGVO deutlich enger begrenzt als in den USA.
- Das Prinzip „wie ein Mensch wirken, der manuell recherchiert hat“ ist bewusst auf Täuschung über die Automatisierung angelegt. Ob Empfänger das als Vertrauensbruch werten, wird nicht diskutiert.
- Der gezeigte Pitch verkauft ein Outreach-System an Agenturen; das Video selbst endet mit Werbung für Maker School. Beides ist eigenes Geschäftsmodell des Sprechers.
- Der Relativ-Link-Filter und die Kürzung auf 5.000 Zeichen sind Näherungen ohne Prüfung, welche Inhalte dabei verloren gehen.
