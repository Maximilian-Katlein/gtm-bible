# Projects neu gestaltet: vom Ordner zur Unterhaltung

> **Quelle:** [Projects redesigned: from folder to conversation](https://claude.com/resources/articles/projects-redesigned) · Anthropic (Artikel), Boris (bcherny, Anthropic Team) und HN-Kommentatoren · Artikel mit Diskussion ([Hacker News](https://news.ycombinator.com/item?id=50492141)) · 2026-11-14
> **Sprecher verkauft:** Claude Code Projects in den Abos Claude Pro und Max · **Zielmarkt der Aussagen:** Entwickler und Teams mit Claude Code Cloud Sessions, später alle Claude Oberflächen sowie Team und Enterprise · **Beweislage:** reine Herstellerangaben ohne Messwerte, ergänzt um Anekdoten aus der Diskussion

## Worum es geht
Anthropic baut Projects in Claude Code von einem Ablageordner zu einem Coordinator um, der parallele Arbeits-Threads mit gemeinsamem Memory steuert. Die Quelle beantwortet, wie dieses Muster aufgebaut ist und für wen es heute nutzbar ist. Die Diskussion zeigt, dass Power-User dasselbe Muster bereits selbst bauen und wo es hakt.

## Was man anwenden kann
1. **Coordinator plus Threads als Arbeitsmuster.** Ein Project besteht aus einem Coordinator und mehreren Threads. Der Coordinator grenzt die Anfrage ein, delegiert, koordiniert parallele Threads, prüft die Ergebnisse und setzt das Endergebnis zusammen. Gebrieft wird wie ein Chief of Staff, Claude verteilt die Arbeit auf neue oder bestehende Threads und meldet sich mit Rückfragen. Eingreifen ist auch vom Smartphone möglich.
2. **Projekt sauber aufsetzen.** Beim Start wählt man ein Ziel und das Repo oder den Kontext. Konfigurierbar sind Cloud-Umgebung, Connectors, Plugins, Instructions und Modell. Claude schlägt zuerst Arbeit vor, die es sofort übernehmen kann.
3. **Branch pro Thread als Kollisionsschutz.** Jeder Thread ist eine eigene Claude Code Cloud Session mit eigenem Branch und eigener Repo-Kopie. Überschneidungen werden nicht verhindert, sondern als normaler Merge Conflict im PR gelöst. Threads können ihre Aufgabe weiter mit Subagents, Loops und Workflows aufteilen.
4. **Multi-Repo-Migration als Einsatzfall.** API-, Web- und Mobile-Repo verbinden, Ziel setzen: veralteten v1 Endpoint abschalten. Claude legt pro Repo einen Thread an, migriert die Caller, lässt Tests laufen, öffnet PRs und nennt die Merge-Reihenfolge. Bedingung: Alle betroffenen Repos sind mit dem Project verbunden. Ergebnisse werden nicht berichtet.
5. **Zielbasierte Performance-Arbeit.** Beispielziel: p75 Latenz des Checkouts senken. Claude profilt jeden Endpoint, testet Optimierungen und öffnet PRs in parallelen Threads. Das Beispiel ist illustrativ, Messergebnisse fehlen.
6. **Gemeinsames Memory für Projektwissen nutzen.** Alle Threads lesen und schreiben in einen gemeinsamen Speicher. Anthropic nennt als Inhalte etwa einen verschobenen Release-Termin, den Grund für einen gestrichenen Export und wen man vor Änderungen am Billing Service fragen muss. Laut Hersteller sinkt dadurch der Aufwand für Prompt Engineering, belegt ist das nicht.
7. **Kommunikationsstil des Coordinators einstellen.** Häufigkeit der Check-ins, Tempo beim Starten neuer Threads und Detailtiefe der Updates lassen sich per Anweisung anpassen. Das ist der einzige Hebel, den der Artikel gegen ein überladenes Coordinator-Fenster anbietet.
8. **Kosten über getrennte Modellwahl steuern.** Weil jeder Thread eine volle Claude Code Session ist, erreichen Projects Nutzungslimits schneller. Modell und Effort Level lassen sich für Coordinator und Worker getrennt wählen, die projektspezifische Nutzung ist einsehbar. Wer viele Threads parallel laufen lässt, sollte das vorab prüfen.
9. **Parallelisierung nicht erzwingen.** bcherny betont, dass fokussierte Einzelaufgaben mit engem Hin und Her wichtig bleiben. Dafür springt man in einen einzelnen Thread und arbeitet dort, statt die Aufmerksamkeit zu verteilen.
10. **Eigenbau-Muster aus der Diskussion.** Mehrere Kommentatoren betreiben eigene Orchestrierung mit Todo- oder Issue-Liste als Eingang, Coordinator mit Unter-Agents und Worktrees plus PRs gegen Kollisionen. nickalaso nutzt GitHub Issues für Tracking und Zuweisung. myaccountonhn lässt Todos aus CalDAV von einem LLM abarbeiten und schickt Screenshots aus einem Simulator zur Freigabe zurück.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1 Woche | Ausweitung der Beta auf mehr Claude Code Nutzer in Pro und Max | Herstellerangabe |
| 17 Skills, 4 Connectors | Verwandte Ankündigung Claude for Manufacturing (Angebote, Qualitätsberichte, Lieferantenanfragen) | Herstellerangabe |
| 12.11.2026 | Datum der verlinkten Ankündigung Self-hosted Claude Managed Agents | Herstellerangabe |
| 10+ Suborchs mit je bis zu 20 Workern | Eigenes Multi-Vendor-Setup von nickalaso | Anekdote |
| fast 12 Monate | Laufzeit des eigenen Multi-Agent-Frameworks Intent von matthewsinclair | Anekdote |
| 85 Punkte, 81 Kommentare | Resonanz auf Hacker News, nur ein Teil der Kommentare lag vor | eigene Erfassung |

## Wortlaute
- „Brief Claude in the project the way you'd brief a chief of staff and it routes work to new or pre-existing threads.“ Steht für das Bedienmodell: delegieren statt einzelne Sessions verwalten.
- „Because of this, projects can reach usage limits faster.“ Das einzige Eingeständnis zu Kosten, ohne Zahlen.
- „it is hard to manage the complexity and context switch. It feels bad to fragment your attention like that.“ bcherny über das Problem, das der Coordinator lösen soll.
- „the coordinator comes back to me with a question about an idea or feature that I had thought of an hour ago“ kami23 über das Kernproblem asynchroner Coordinator-Muster.
- „github issues for work tracking/assignment + worktrees and prs to prevent collision.“ nickalaso fasst das Eigenbau-Rezept in einer Zeile.

## Grenzen und Widerspruch
- **Keine Belege.** Weder Benchmarks noch Kundenfälle. Beide Beispiele sind ohne Ergebnis beschrieben. bcherny sagt, fast der gesamte eigene Code entstehe so, das ist die Aussage eines Mitarbeiters.
- **Nur Cloud.** Threads laufen ausschließlich in der Anthropic Cloud. Lokale Ausführung hinter dem eigenen Netzwerk ist „very soon“ angekündigt, ohne Datum. Für Organisationen, die Code oder Daten nicht in eine Anbieter-Cloud geben dürfen, ist Projects derzeit nicht nutzbar. Das separate Produkt Self-hosted Managed Agents läuft in der eigenen Cloud oder on premise, ist aber kein Ersatz für Projects.
- **Memory ungeklärt.** Offen bleibt, wo das gemeinsame Memory liegt, ob es einsehbar oder löschbar ist und wie es sich zu Datenschutz und EU-Anforderungen verhält.
- **Kosten unklar.** Keine Preise, keine Limits, kein Verbrauch pro Thread. augment_me und gib444 unterstellen, das Produkt solle den Token-Verbrauch treiben. Das ist unbelegt, aber bei vielen parallelen Threads plausibel.
- **Lock-in.** throwaway13337 und ddxv sehen in der Verlagerung des Dev-Setups in die Cloud einen wachsenden Moat für den Anbieter: Je mehr Prozess und Memory dort liegen, desto schwerer der Ausstieg. Die Aussagen zu Nvidia-GPU-Zugang sind unbelegt.
- **Defaults ungeprüft.** soared behauptet, Standard sei Opus low als Coordinator und Opus high in den Threads. Der Artikel nennt keine Defaults.
- **Mehrwert gegenüber Eigenbau offen.** nickalaso fragt, was Projects besser macht als ein eigenes Setup. In den vorliegenden Kommentaren gibt es keine Antwort. myaccountonhn hält ein ähnliches System für leicht selbst baubar.
- **Coordinator-Chaos.** kami23 berichtet, dass die Coordinator-Session bei vielen langlebigen Agents unübersichtlich wird und veraltete Rückfragen den Nutzer zwingen, eigene Gedanken neu zu rekonstruieren. Der Artikel adressiert das nur über einstellbare Check-ins.
- **Zugang begrenzt.** Beta nur für ausgewählte Pro- und Max-Nutzer mit Cloud Sessions und ohne bestehende Projects. Team und Enterprise folgen ohne Termin.
