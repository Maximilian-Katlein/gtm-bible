# gtm-bible

**Die wachsende Wissensbasis für B2B Go-to-Market, Marketing, Sales und AI Building.** Jeden Tag kommen neue Learnings dazu: aus Hacker News, aus den besten YouTube-Kanälen und aus neuen Open-Weight-Modellen auf Hugging Face. Keine Zusammenfassungen, sondern das, was man anwenden oder prüfen kann: Abläufe, Zahlen mit Herkunft, Wortlaute, Werkzeuge, Bedingungen und Widersprüche.

## Themen

| Thema | Worum es geht |
|---|---|
| [B2B Go-to-Market](themen/gtm.md) | Positionierung, Kanäle, Founder-led Sales, Wachstum |
| [AI im Vertrieb und B2B Sales](themen/ai-sales.md) | Outbound, AI SDRs, Enterprise-Verkauf, Termine |
| [AI im Marketing](themen/ai-marketing.md) | Content, Distribution, Agenten im Marketing |
| [AI Building](themen/ai-building.md) | Agenten, Claude Code, MCP, Produkte mit AI bauen |
| [Open-Weight-Modelle](themen/open-weight-modelle.md) | neue Modelle, Lizenzen, Hardware, Benchmarks mit Herkunft |
| [Sovereign AI](themen/sovereign-ai.md) | EU AI Act, europäische Modelle und Clouds, Datenhoheit |

Dazu [Personen](personen/): alles, was ausgewählte Praktiker lehren, über alle ihre Inhalte hinweg.

## Wie es funktioniert

1. **Radar:** Täglich werden Hacker News, YouTube (Videos der Woche je Thema und beobachtete Kanäle) und die Trending-Modelle auf Hugging Face durchsucht.
2. **Auswahl:** Substanz vor Reichweite. Geld-schnell-Versprechen, reine Werbung und Clickbait fliegen raus.
3. **Vertiefen:** Jede ausgewählte Quelle wird vollständig ausgewertet (Videos mit Bild und Ton, Artikel samt Diskussion, Model Cards) zu einem Detail-Inventar mit Zeitstempeln.
4. **Schreiben:** Je Quelle eine [Quellseite](quellen/), daraus Learnings in der [Datenbank](daten/learnings.jsonl), eingeordnet in die Themen- und Personenseiten. Was mehrere Quellen unabhängig sagen, wird zu einer Aussage mit mehreren Belegen. Widersprüche stehen unter „Strittig“.
5. **Prüfen und veröffentlichen:** Jede Änderung läuft durch automatische Prüfungen (Quellenpflicht, Zitatlänge, keine personenbezogenen Daten) und wird als Pull Request kuratiert, bevor sie live geht.

Das [Radar-Archiv](radar/) zeigt, was an welchem Tag dazukam.

## Regeln für jeden Eintrag

- **Quelle immer verlinkt**, mit Zeitstempel bei Videos.
- **Beweislage sichtbar:** eigene Daten, Kundenfall, Anekdote, Herstellerangabe oder Behauptung ohne Beleg.
- **Für wen es gilt:** Markt, Firmengröße, B2B oder B2C. Was nur für Creator oder Kleinbetriebe belegt ist, steht so da.
- **Wer etwas verkauft, steht dabei.** Viele Lehrer verkaufen Kurse oder Werkzeuge; das ist kein Ausschluss, aber Kontext.
- **Keine Transkripte.** Kurze Zitate (höchstens 200 Zeichen) mit Quelle, alles andere in eigenen Worten.

## Daten nutzen

- `daten/learnings.jsonl`: ein Learning je Zeile mit Thema, Typ, Aussage, Bedingung, Beleg, Quelle und Link. Gut zum Durchsuchen, Filtern oder als Kontext für eigene AI-Agenten.
- `daten/quellen.jsonl`: alle ausgewerteten Quellen.
- `skills/`: wiederverwendbare Agenten-Skills, die aus den Learnings entstehen, sobald ein Thema genug belegte Substanz hat.

## Mitmachen

Fehler gefunden, Quelle falsch verstanden, wichtige Quelle fehlt? Ein [Issue](../../issues) mit Link genügt. Pull Requests mit Korrekturen sind willkommen; jede Aussage braucht eine Quelle.

## Lizenz

Eigene Texte: [CC BY 4.0](LICENSE.md). Zitate und verlinkte Inhalte gehören ihren Urhebern; sie werden nur kurz und mit Quelle zitiert. Dieses Repo steht in keiner Verbindung zu den zitierten Personen oder Firmen.

Kuratiert von [Maximilian Katlein](https://github.com/Maximilian-Katlein).
