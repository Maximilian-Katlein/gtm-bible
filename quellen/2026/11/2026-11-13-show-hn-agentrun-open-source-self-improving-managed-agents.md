# Show HN: AgentRun, Open-Source-Plattform für selbstverbessernde Managed Agents

> **Quelle:** [Show HN: AgentRun, open-source, Self-improving Managed Agents](https://github.com/Parcha-ai/agentrun/blob/main/README.md) · Parcha (GitHub README), Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50471650) · Artikel und Diskussion · 2026-11-13
> **Sprecher verkauft:** AgentRun, eine Open-Source-Plattform (Apache-2.0) mit Lernschleife, Durable Execution und Control Plane auf bestehenden Agent-Harnesses (pi, Claude Code, Codex, OpenCode) · **Zielmarkt der Aussagen:** Teams, die Agenten produktiv und wiederholt betreiben (Code Review, KYB, Inbound-Lead-Scoring, Marktbeobachtung) · **Beweislage:** zwei eigene Fallstudien mit kleinen Stichproben, Methodik nur in verlinkten Beiträgen, der Rest sind Herstellerangaben.

## Worum es geht
Wie senkt man die Kosten von Agenten, die dieselbe Aufgabe hundertfach ausführen und dabei jedes Mal dieselbe API, Doku und Planung neu erarbeiten? Parcha antwortet mit einer Plattform, die nach jedem Lauf das Gelernte prüft und versioniert, und mit dem Muster „teures Modell erkundet, günstiges Modell wiederholt“. Relevant für Teams, die Agenten nicht experimentell, sondern im Dauerbetrieb einsetzen.

## Was man anwenden kann
1. **Kosten pro Aufgabe überwachen, nicht nur Preis pro Einheit.** Bei Parcha stieg die Code-Review-Rechnung von 180 auf 6.451 Dollar im Monat, obwohl der Preis pro Review gleich blieb. Treiber war das Volumen: Die eigenen Agenten erzeugten deutlich mehr PRs. Wer per Review oder Call abrechnet, sollte die Rechnung an die Zahl agentisch erzeugter Artefakte koppeln und beobachten.

2. **Teures Modell erkundet, günstiges Modell führt aus.** In der Merchant-Code-Fallstudie löste Opus die Klassifikation zuerst explorativ, das Gelernte ging dann an ein günstiges Modell. Kosten pro Merchant sanken von 0,89 auf 0,12 Dollar. Bedingung: eine wiederkehrende, klar umrissene Aufgabe, deren Wissen sich als Notiz, Skill oder Workflow übergeben lässt.

3. **Eigenen Reviewer auf eigenen PRs tunen.** Parcha baute einen Reviewer auf einem günstigen Modell, getunt auf eigenen PRs. 18 Cent pro Review statt 1 Dollar, und auf 30 ungesehenen PRs das 1,6-Fache der echten Bugs von Greptile. Übertragbarkeit auf andere Codebasen ist nicht belegt.

4. **Lernschleife mit Prüfung statt freiem Gedächtnis.** Mit `"learning": true` bekommt der Agent am Ende jedes Runs einen Zusatz-Turn, um vorzuschlagen, was er behalten will. Zuerst prüft Code die Form, dann bewertet ein Grader den Inhalt, bestandene Vorschläge landen per Git-Commit im Ordner des Agenten. Der nächste Run startet von diesem Stand.

5. **Skills nur aus erfolgreichen Läufen.** Notizen sind kurze Markdown-Dateien mit je einem Fakt. Skills beschreiben, wie eine Aufgabe erneut erledigt wird, und nur ein Run, der die Aufgabe abgeschlossen hat, darf einen schreiben. So entstehen keine Anleitungen aus gescheiterten Läufen.

6. **Nach drei Wiederholungen zum Workflow verdichten.** Hat ein Skill 3 Runs bedient, wird der nächste Run um einen Workflow-Entwurf gebeten. Der Entwurf läuft vor dem Speichern als Dry-Run ohne Modell und ohne Tool-Ausführung. Danach läuft der Workflow als ein einziger Tool-Call unter Kostenlimit und Berechtigungen.

7. **Typisierte Entscheidungen mit Konfidenzschwelle.** Wiederkehrende Arbeit wird als Workflow aus Tool-Calls, Modellschritten und schnellen typisierten Fragen (Ja/Nein, Auswahl, Score mit Konfidenz) gebaut, ein Agent springt nur bei unklaren Fällen ein. Im illustrierten Beispiel liegt 0,61 unter der Schwelle 0,75, also geht der Fall zur Prüfung. Der Wert ist konstruiert, nicht gemessen.

8. **Gelerntes gegen Prompt-Injection absichern.** Enthält eine Antwort ein Geheimnis, ein verstecktes Zeichen, eine Datei außerhalb des Ordners oder eine Löschung, wird die ganze Antwort verworfen. Regeln, die aus einer Webseite oder eingefügten E-Mail stammen, und Notizen mit Kontonummer werden verworfen. Riskante Regeln warten auf menschliche Freigabe.

9. **Kostenlimits, die pausieren statt scheitern.** Ein Run am Limit hält an und nennt den Mindestbetrag zum Weitermachen. Nicht bepreisbare Kosten erscheinen als „unknown“, nie als 0 Dollar. Das Prinzip lässt sich auf jedes eigene Agent-Setup übertragen.

10. **Freigaben pro Tool und keine Rechte durch Templates.** Jedes Tool ist erlaubt, fragt nach oder ist verboten, eine serverseitige Deny-Liste gilt auch im unbeaufsichtigten Modus. Ein Template vergibt keine Rechte, bis man jedes MCP-Tool selbst ankreuzt. Mit `npx @parcha/agentrun template eval DIR` laufen die Eval-Cases als echte Runs auf einem Wegwerf-Server.

11. **Unterbrochene Schreibzugriffe manuell prüfen.** Nach einem Absturz läuft ein Run weiter, abgeschlossene Schritte werden nicht wiederholt. Ein Schreibvorgang, der mitten im Call abbrach, wird als „interrupted“ markiert und nicht automatisch wiederholt. Das verhindert Doppelbuchungen, verlangt aber Nacharbeit.

12. **Inbound-Lead-Scoring als Template (B2B Sales).** Ein Webhook liefert jeden Lead, der Agent recherchiert ihn und bewertet ihn von 0 bis 100 gegen das eigene ICP. Voraussetzung: definiertes ICP und Webhook aus CRM oder Formular. Genauigkeit ist nicht belegt und sollte mit eigenen Eval-Cases gemessen werden.

13. **Schnellstart.** Node 24.22.3 oder neuer, macOS oder Linux. `npx @parcha/agentrun` startet Server und Runner auf Port 7340, legt Daten in `~/.agentrun` ab und öffnet die Konsole. Ein `OPENROUTER_API_KEY` versorgt alle Harnesses, ein Anthropic-Key pi und Claude Code, ein OpenAI-Key pi, Codex und OpenCode. Ohne laufendes Docker haben Agenten keine Shell.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 180 → 6.451 Dollar/Monat (rund 36x) | Greptile-Rechnung für Code Review bei Parcha, getrieben durch PR-Volumen | eigene Daten |
| 1 Dollar vs. 18 Cent | Preis pro Review Greptile vs. eigener Reviewer | eigene Daten |
| 1,6x | gefundene echte Bugs eigener Reviewer vs. Greptile, auf 30 ungesehenen PRs | eigene Daten, kleine Stichprobe |
| 0,89 → 0,12 Dollar | Kosten pro Merchant-Klassifikation, Opus erkundet, günstiges Modell führt aus | eigene Daten, Genauigkeit nicht genannt |
| 3 Runs | Schwelle, ab der ein Skill zum Workflow-Entwurf wird | Herstellerangabe |
| 30 Sekunden | Lease, nach der ein anderer Runner die Runs eines toten Runners übernimmt | Herstellerangabe |
| 0,61 vs. 0,75 | Konfidenz vs. Schwelle im Workflow-Beispiel | konstruiertes Beispiel |
| 8 Reviewer | unabhängige Reviewer im Template code-review | Herstellerangabe |

## Wortlaute
- „Agents are great at figuring things out. The problem is they figure out the same things over and over.“ Steht für die Kernthese: Kosten entstehen durch wiederholtes Neu-Erarbeiten.
- „A lot of agents don't need to be agents.“ Steht für das Prinzip, wiederkehrende Arbeit als typisierten Workflow zu bauen.
- „A cost AgentRun can't price reads "unknown", never $0.“ Steht für ehrliche Kostenanzeige bei Agenten.

## Grenzen und Widerspruch
- **Fallstudien dünn belegt.** Die 1,6x-Aussage beruht auf 30 PRs. Bug-Definition, Greptile-Konfiguration, verwendetes günstiges Modell und Genauigkeit bei den Merchant Codes stehen nur in verlinkten Beiträgen, nicht im README.
- **Selbstverbesserung nicht gemessen.** Offen bleibt, wie der Grader bewertet, welches Modell er nutzt, wie Drift oder schlechte Notizen erkannt werden und wie viel Tuning pro Repo nötig ist. egonschiele fragt in der Diskussion genau danach, eine Antwort der Autoren ist nicht sichtbar.
- **Abo statt API-Key unklar.** ferar fragt, ob der Claude-Code-Harness mit einem Abo nutzbar ist. Das README nennt nur API-Keys.
- **Gegenposition zu den Kosten.** ghempton hält bei vorhandenen Abos einen lokalen Orchestrator für günstiger und besser. Kein Beleg, und er betreibt ein eigenes Konkurrenzprojekt. Ob Abo-Bedingungen solchen Einsatz erlauben, ist im Einzelfall zu prüfen.
- **KYB-Datenabdeckung.** mfrye0 wendet ein, das KYB-Template stütze sich vor allem auf leicht zugängliche Register wie das britische. Seine Angaben (rund 200 Register, 500 Millionen Entitäten) sind Selbstauskunft eines Anbieters.
- **Sandbox-Einschränkung.** Daytona, Modal und E2B laufen nur mit Archil-Disk, und mit Archil wird die Docker-Sandbox abgelehnt.
- **Keine Aussage zu Souveränität.** Datenschutz, EU-Hosting und Open-Weight-Modelle kommen im sichtbaren README nicht vor. Modellquellen sind OpenRouter, Anthropic und OpenAI.
- **Unvollständige Quelle.** Das README ist abgeschnitten, von 17 Kommentaren waren 7 sichtbar.
