# Show HN: Mastra Factory, die Open-Source-Software-Factory, mit der wir Mastra bauen

> **Quelle:** [Show HN: Mastra Factory, the open-source software factory we use to build Mastra](https://news.ycombinator.com/item?id=50548660) · Shane, Sam und Abhi (Gründerteam Mastra) · Diskussion (Hacker News, 82 Punkte) · 2026-11-19
> **Sprecher verkauft:** das Open-Source TypeScript Agent Framework Mastra und Mastra Factory (Open Source, zusätzlich als gehostete Version) · **Zielmarkt der Aussagen:** Entwicklungsteams und Maintainer, die Coding-Agenten in ihren PR- und Issue-Workflow einbinden wollen · **Beweislage:** eigene Nutzungszahlen des Herstellers aus einer einzelnen Woche, ohne Methodik und ohne Qualitätsdaten.

## Worum es geht
Das Mastra-Team zeigt, wie es Coding-Agenten in den eigenen Entwicklungsprozess einbaut: als Kanban-Board, das sich aus Slack per @-Tag ansprechen lässt. Die Quelle beantwortet, welche Bausteine dafür nötig sind und wie sich die Arbeitsweise nach drei Monaten verändert hat. Sie richtet sich an Entwicklungsteams mit hohem PR-Aufkommen. Der Hersteller beschreibt dabei sein eigenes Produkt.

## Was man anwenden kann
1. **Agenten-Workflow am bestehenden Prozess ausrichten.** Das Team hat Factory zuerst an seine vorhandenen Stufen angelehnt: Triage, Plan, Build, Review, Shipped. Diese Stufen sind die Spalten des Boards. Wer Agenten einführt, beginnt also mit dem Prozess, den das Team schon lebt, statt einen neuen zu erfinden.

2. **Steuerung dorthin legen, wo das Team ohnehin arbeitet.** Nach drei Monaten steuert das Team Factory überwiegend über Slack, nicht über die Web-Oberfläche. Das Board wird zur Zustandsanzeige, die Interaktion läuft im Chat. Eine Nutzungsstatistik dazu gibt es nicht, es ist eine Beobachtung des Teams.

3. **Review-Feedback in dieselbe Session zurückführen.** Sogenannte Signals abonnieren PR-Kommentare und speisen sie in die laufende Agenten-Session ein. Der Agent reagiert auf Kommentare im bestehenden Kontext, statt dass jemand eine neue Session starten muss. Wie das technisch umgesetzt ist, steht nicht im Beitrag.

4. **Sammelaufträge für den Rückstau.** Erfahrenere Engineers starten mehrere Sessions parallel und geben Aufträge wie die 20 ältesten Issues zu triagieren und zu bewerten. Der Agent bereitet vor, Menschen entscheiden danach. Das Team beobachtet das vor allem bei Senior Engineers.

5. **Bausteine einer Software Factory.** Factory setzt sich aus Mastra-Komponenten zusammen: durable Agents für lang laufende Sessions, ein konversationelles Memory-System, ein Markdown-Wiki mit Quellenangaben für Unternehmenswissen, Signals für PR-Kommentare und eine anpassbare Cloud-Sandbox mit eigenem Coding-Harness. Die Liste taugt als Prüfraster für eigene Agenten-Setups, auch ohne Mastra.

6. **Externe Beiträge als Issue-Repro statt PR.** Mastra hat das Repo für externe Contributor geschlossen und bittet stattdessen um detaillierte Issue-Reproduktionen, die intern bearbeitet werden, auch durch Factory. Eine Begründung oder Daten zur Qualität externer PRs nennt das Team nicht. Ein Kommentator beobachtet dasselbe Muster bei anderen Open-Source-Projekten.

7. **Automatische Scanner ergänzen.** Das Team nutzt inzwischen Bug- und Schwachstellenscanner. Welche, und wie deren Funde in Sessions landen, bleibt offen.

8. **Einstieg und Self-Hosting.** Start mit `npm create factory`, Repo `mastra-ai/template-factory`. Laut Beitrag vollständig Open Source und komplett auf eigener Infrastruktur betreibbar, zusätzlich gehostet. Die Lizenz wird nicht genannt. Aktuell läuft nur der eigene Coding-Harness, Claude Code und Codex sind erst in Arbeit.

9. **Alternative mit Workflow-Sprache (Kommentar).** Der Kommentator siscia beschreibt ein eigenes System mit der Sprache dotFactory. Bausteine: Trigger (Webhook, GitHub-PR, GitHub-Issue, Cron, manueller Klick), eigene Secrets und Konfiguration, manuelle Gates, an denen ein Mensch freigibt, und Container als Schritt, damit man nicht auf offizielle Integrationen warten muss.

10. **Dokumentation per Prüfschleife pflegen (Kommentar).** Beispiel von siscia: täglich um 3 Uhr prüfen, ob die Website-Doku aktuell ist. Falls nicht, aktualisieren und das Ergebnis einem adversarialen LLM vorlegen. Besteht es die Prüfung, wird gemergt, sonst geht das Feedback zurück in die Schleife.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| knapp 4 Mio. | Downloads von Mastra pro Woche im Schnitt | eigene Daten, Zählquelle nicht genannt |
| Verdopplung | Downloads etwa zwei Wochen nach dem ersten Show HN vor fast zwei Jahren | eigene Daten, nur zeitlicher Zusammenhang, Ausgangswert fehlt |
| 238 | von Factory geöffnete und gemergte PRs in der Vorwoche | eigene Daten, eine Woche, mastra-ai Org |
| 630 | von Menschen gemergte PRs in derselben Woche | eigene Daten |
| ca. 27 % | Agentenanteil an 868 gemergten PRs | eigene Rechnung aus den Angaben oben |
| 3 Monate | Nutzungsdauer bis zur Beobachtung, dass Slack die Hauptschnittstelle ist | Anekdote |

## Wortlaute
- „a configurable agentic kanban board that's @-taggable in Slack“: die Selbstdefinition von Factory, bewusst ohne allgemeine Definition von Software Factory.
- „triage the 20 oldest issues and let's evaluate…“: Beispiel für einen Sammelauftrag an parallele Agenten-Sessions.
- „we've closed our repo to outside contributors, asking folks to write detailed issue repros instead“: die Umstellung von externen PRs auf Issue-Reproduktionen.
- „There is also the concept of manual gate, so you can wait for an human to actually click a button.“: menschliche Freigabe als fester Schritt im Agenten-Workflow (Kommentar siscia).

## Grenzen und Widerspruch
- **Dünnes Material.** Ein kurzer Show-HN-Text ohne Methodik plus erste Kommentare. Keine technische Dokumentation.
- **Keine Qualitätsdaten.** Zu den 238 Agenten-PRs fehlen PR-Größe, Review-Aufwand, Ablehnungsquote, Rücknahmen, Kosten, Token-Verbrauch und eingesetzte Modelle. Die Zahl misst Menge, nicht Wert.
- **Dogfooding.** Der Hersteller misst am eigenen Produkt, eine Woche lang. Übertragbarkeit auf andere Teams ist nicht belegt.
- **Agentenidentität offen.** moltar fragt, ob Agenten mit eigener Identität arbeiten oder die GitHub-Identität des Engineers übernehmen. Für Audit, Zurechenbarkeit und Branch-Protection ist das zentral. Keine Antwort in den gezeigten Kommentaren.
- **Verifikation offen.** slopinthebag fragt, wie autonom der Ablauf ist und wie Ergebnisse, besonders im UX-Bereich, geprüft werden. Der Beitrag beschreibt keine Verifikationsschritte für Oberflächen.
- **Onboarding und Darstellung.** SillyUsername vermisst Visuals, da Nutzer nicht nur Entwickler seien, und der Einstieg wirke wie ein reines CLI-Werkzeug. jobryan fragt nach Demovideo und Best Practices. Ein Video scheint zu existieren, ist aber offenbar schlecht auffindbar.
- **Souveräner Betrieb nur teilweise geklärt.** Self-Hosting ist laut Beitrag möglich, aber Lizenz, nötige Modelle, Sandbox-Anbieter, EU-Hosting und Preise der gehosteten Version fehlen.
- **Plattformrisiko.** tireguess prophezeit ohne Beleg, Mastra werde von Anthropic verdrängt. Der Kern des Einwands bleibt prüfenswert: Anbieter von Coding-Agenten können die Orchestrierung selbst anbieten. Die geplante Unterstützung von Claude Code und Codex zielt auf Anbieterneutralität, ist aber noch nicht verfügbar.
- **Keine Antworten der Autoren** in den gezeigten Kommentaren.
