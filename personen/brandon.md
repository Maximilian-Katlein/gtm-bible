# Brandon

Brandon zeigt, wie man B2B-Kaltakquise mit KI-Agenten wie Claude Code baut, und lohnt sich vor allem für die konkrete Verbindung von Signal-Recherche, Textregeln und sicherem Versand über Instantly.

Stand: 2026-11-20 · 1 Quelle

Verkauft: In den bisherigen Quellen wird kein eigenes Produkt beworben. Brandon hat an der Instantly CLI mitgewirkt und deren Standardwerte selbst festgelegt; erwähnt wird außerdem ein eigenes SaaS-Produkt ohne Namen.

## Kernideen

### Personalisierung heißt Signal, nicht Platzhalter

Ein Serienbrief mit Vorname und Firmenname gilt nicht als Personalisierung. Echte Personalisierung knüpft an ein konkretes, aktuelles Ereignis an: Post, Neueinstellung, Produktlaunch, Finanzierungsrunde, Stellenanzeige, Pressenennung oder Podcast-Auftritt. Fehlt dieses Signal in der Leadliste, wird es je Lead von einem Recherche-Agenten beschafft.

> „Hey first name, I noticed you work at company. That is not personalization. That is a mail merge.“

Belege:
- Serienbrief ist keine Personalisierung, gilt für B2B-Kaltakquise per Mail ([Cold Emails mit Claude Code, 00:28](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Fehlende Signal-Spalte per Recherche-Agent füllen ([Cold Emails mit Claude Code, 15:23](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Erste Mail der Sequenz führt mit dem Signal ([Cold Emails mit Claude Code, 20:34](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Stellenanzeige als Signal, aus dem sich ein Schmerzpunkt ableiten lässt ([Cold Emails mit Claude Code, 20:38](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

### Der Agent arbeitet, der Mensch gibt frei

Wer Agenten auf Versandsysteme loslässt, baut an mehreren Stellen Haltepunkte ein: Der Agent bestätigt erst sein Verständnis und legt einen Plan vor, ein kleiner Pilot läuft vor der großen Liste, unsichere Signale werden markiert, Kampagnen werden pausiert angelegt und erst nach Sichtprüfung gestartet. Fehler sollen an 20 Mails auffallen, nicht an 1.000.

> „I need you to confirm with me that you understand before you actually go and do something.“

Belege:
- Prompt endet mit Bitte um Bestätigung und Plan; deckte zwei Lücken auf ([Cold Emails mit Claude Code, 12:24](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Pilot mit 10 bis 25 Leads vor 1.000 Leads ([Cold Emails mit Claude Code, 13:39](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Feld signal_confidence gegen unbelegte Behauptungen ([Cold Emails mit Claude Code, 20:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Gedankenstriche von Hand entfernen, weil die Sperrliste sie übersah ([Cold Emails mit Claude Code, 21:03](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Kampagne pausiert und ohne Absenderkonten anlegen, Start erst nach Vorschau je Lead ([Cold Emails mit Claude Code, 23:28](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

### Kaltmail führt mit Wert und will nur Neugier

Eine Kaltmail soll nicht abschließen, sondern aus kaltem Kontakt warmes Interesse machen. Der Wert wird über einen von drei B2B-Kaufgründen gerahmt: Zeit sparen, Geld sparen, mehr Geld verdienen. Damit der Agent das kann, muss er das eigene Angebot kennen.

> „We're trying to go from cold outreach to warm intent and peak curiosity.“

Belege:
- Ziel kalt zu warmem Interesse, drei Kaufgründe ([Cold Emails mit Claude Code, 12:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- Ohne Angebotsbeschreibung kann Claude nicht mit Wert führen; Angebot gehört in die CLAUDE.md ([Cold Emails mit Claude Code, 14:06](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

## Methoden und Abläufe

### Ablauf: 1.000 personalisierte Kaltmails mit Claude Code und Instantly

1. **Angebot hinterlegen.** Das eigene Angebot in eine CLAUDE.md im Projektordner schreiben. Ohne sie fragte Claude nach; ersatzweise wurde die eigene Website gescrapt. ([14:06](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
2. **Prompt mit Freigabeschritt.** Den Auftrag damit abschließen, dass Claude sein Verständnis bestätigt und einen Plan zur Freigabe vorlegt. ([12:24](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
3. **Pilot ziehen.** 10 bis 25 Leads, geschichtet nach Rollen, je Bucket die besten Entscheider. Im Video: 20 Leads mit je 3 Mails in etwa 20 Minuten. ([13:39](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
4. **Signale recherchieren.** Je Lead ein Recherche-Agent mit Websuche, Rückgabe als festes JSON mit den Feldern `company_one_liner`, `role_context`, `signal`, `signal_source`, `pain_hypothesis`. In Batches von etwa 10 parallel, nicht alle auf einmal, damit das Kontextfenster des Hauptagenten sauber bleibt. ([15:23](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md), [16:01](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
5. **Signalqualität markieren.** Ein Feld `signal_confidence` kennzeichnet Leads, deren Signal nur abgeleitet ist. ([20:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
6. **Texte schreiben.** Dreistufige Sequenz nach den Textregeln unten, danach Prüfung gegen eine Sperrliste inklusive Gedankenstrichen. ([20:34](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md), [21:03](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
7. **In Instantly laden.** Über die Instantly CLI Kampagne anlegen, Leads laden, Sequenz setzen. Texte über Merge-Tags, siehe unten. ([05:06](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md), [23:51](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
8. **Sicher anlegen, dann prüfen.** Kampagne pausiert, ohne verbundene Absenderkonten, nur Text, ohne Open- und Link-Tracking, Stopp bei Antwort und Auto-Antwort. Start erst nach Sichtprüfung der Vorschau je Lead. ([23:28](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

*Einordnung: Die Standardwerte in Schritt 8 hat Brandon nach eigener Aussage selbst in die Instantly CLI eingebaut. Sie sind eine plausible Vorsichtseinstellung, aber keine unabhängig geprüfte Empfehlung.*

### Dreistufige Sequenz mit wechselndem Winkel

| Schritt | Tag | Winkel |
|---|---|---|
| 1 | 0 | Führt mit dem recherchierten Signal |
| 2 | +3 | Führt mit einem konkreten Schmerzmechanismus |
| 3 | +7 | Weicher Abschied mit einer Rechnung oder einem „ignorier mich, wenn X“ |

Quelle: [Cold Emails mit Claude Code, 20:34](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md)

### Individuelle KI-Texte über Merge-Tags in Instantly

Jeder Sequenzschritt enthält nur `{{emailN_subject}}` und `{{emailN_body}}`. Jeder Lead trägt seine sechs vorgenerierten Textfelder (drei Betreffe, drei Texte) als `custom_variables`. So steckt die gesamte Personalisierung im Lead, nicht in der Vorlage. ([Cold Emails mit Claude Code, 23:51](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

### Stellenanzeigen als Fenster in die Vertriebsorganisation

Aus einer Ausschreibung für eine Director-Stelle las der Agent, dass die AEs Full Cycle arbeiten, also Inbound und Outbound. Daraus wurde der Schmerzpunkt „teure Closer-Zeit geht für Prospecting drauf“.

> „from the Director job spec, your AEs are running full cycle, both inbound and outbound.“

Quelle: [Cold Emails mit Claude Code, 20:38](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md)

### Werkzeug: Instantly CLI statt MCP

Die per npm installierte Instantly CLI lässt Claude Code Kampagnen anlegen, Leads laden und Sequenzen setzen. Brandon sagt, sie decke die ganze API ab, aus der Erinnerung 156 Endpunkte, und hält eine CLI für Agenten natürlicher als einen MCP-Server. ([Cold Emails mit Claude Code, 05:06](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

## Formulierungen und Formate

- **„That is a mail merge.“** Kurzformel gegen Scheinpersonalisierung. ([00:28](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **„From cold outreach to warm intent.“** Ziel einer Kaltmail als Übergang, nicht als Abschluss. ([12:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Zeit sparen, Geld sparen, mehr Geld verdienen.** Die drei B2B-Kaufgründe als Rahmen für jedes Wertversprechen. ([12:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **„Ignorier mich, wenn X“.** Format für die Abschiedsmail im dritten Schritt. ([20:34](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Festes JSON-Schema für Recherche-Agenten.** `company_one_liner`, `role_context`, `signal`, `signal_source`, `pain_hypothesis`, ergänzt um `signal_confidence`. ([16:01](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md), [20:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Sperrliste für KI-Texte.** Floskeln, LinkedIn-Schmeichelei, harte CTAs, Konzernsprache und zusätzlich Gedankenstriche. ([21:03](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))

## Zahlen, die sie nennt

| Zahl | Kontext | Beleg | Quelle |
|---|---|---|---|
| höchstens etwa 100 Wörter, gemessen 80 bis 100 | Länge je Kaltmail im Pilot | Behauptung ohne Beleg | [10:04](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| Betreff unter 60 Zeichen, besser unter 33 | ab etwa 34 Zeichen laut Brandon auf dem Handy abgeschnitten | Behauptung ohne Beleg | [10:04](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| 1 bis 3 % Antwortrate | realistisch bei Kaltmails; unter 1 % stimmt etwas nicht | Behauptung ohne Beleg | [21:29](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| 20,8 % Antwortrate | eigener SaaS-Lauf, vom Agenten in eine Mail geschrieben; Brandon selbst: „too good to be true“ | ohne genannte Basis | [21:29](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| 10 bis 25 Leads | empfohlene Pilotgröße | eigene Daten | [13:39](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| 20 Leads, je 3 Mails, etwa 20 Minuten | Dauer des Piloten im Video | eigene Daten | [13:39](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| 8 von 20 Leads | nur abgeleitete Signale, weil Agenten keine Websuche hatten | eigene Daten | [20:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| etwa 10 parallel | Batchgröße für Recherche-Agenten | Anekdote | [16:01](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| Tag 0, +3, +7 | Abstände der dreistufigen Sequenz | Anekdote | [20:34](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |
| 156 Endpunkte | Abdeckung der Instantly CLI, aus der Erinnerung | Behauptung ohne Beleg | [05:06](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md) |

> „let's be real, it's usually like 1 to 3%.“

## Wo Vorsicht geboten ist

- **Interessenkonflikt bei Instantly.** Brandon hat an der Instantly CLI mitgewirkt und deren Standardwerte selbst gesetzt. Lob für die CLI und die Einschätzung „CLI ist für Agenten natürlicher als MCP“ sind daher nicht neutral. ([05:06](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md), [23:28](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Halluzinierte Personalisierung.** Im eigenen Pilot hatten 8 von 20 Leads nur abgeleitete Signale. Ohne Markierung gehen plausibel klingende, aber unbelegte Behauptungen an echte Empfänger. ([20:16](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Agenten übernehmen ungeprüfte Zahlen.** Der Agent schrieb die 20,8 % Antwortrate in eine Mail, obwohl Brandon die Zahl selbst für unrealistisch hält. Zahlen in KI-Texten vor dem Versand einzeln prüfen. ([21:29](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **API-Keys nicht in den Chat.** Keys über Terminal oder `.env` hinterlegen, einen im Chat gelandeten Key rotieren. Im Test funktionierte bei der Instantly CLI nur die Umgebungsvariable `INSTANTLY_API_KEY`, nicht das Flag `--api-key`. ([05:55](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Sperrlisten sind lückenhaft.** Die automatische Prüfung übersah Gedankenstriche, die als typisches KI-Merkmal gelten. ([21:03](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md))
- **Dünne Beweislage.** Textlängen, Betreffgrenzen und Antwortraten sind Erfahrungswerte ohne Beleg; die Methode stammt aus einem einzigen Demo-Piloten mit 20 Leads, nicht aus einem ausgewerteten Versand.

## Alle Quellen

- 2026-11-20 · [How To Send 1000 Deep-Personalized Cold Emails Per Day with Claude Code](../quellen/2026/11/2026-11-20-how-to-send-1000-deep-personalized-cold-emails-per-day-with.md)
