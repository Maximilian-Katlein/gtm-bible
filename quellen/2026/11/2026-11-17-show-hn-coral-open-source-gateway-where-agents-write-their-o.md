# Coral: Open-Source-Gateway, in dem Agenten ihre eigenen Tools schreiben

> **Quelle:** [Show HN: Coral (Open-source gateway where agents write their own tools)](https://github.com/withcoral/coral) · withcoral (Coral-Team), Kommentare u. a. von antonmry (nach eigener Angabe Coral-Mitarbeiter) · Diskussion (Show HN) mit README des Repos · 2026-11-17
> **Sprecher verkauft:** Open-Source-Gateway zum Selbsthosten mit Policy-Prüfung pro Tool-Aufruf, Credential-Verwaltung, Freigabe-Workflow und Custom Tools; Enterprise-Edition angekündigt · **Zielmarkt der Aussagen:** Engineering- und Betriebsteams in Unternehmen (SRE, Support, SecOps, BI), die Agenten mit Schreibrechten einsetzen · **Beweislage:** alle Zahlen sind Herstellerangaben ohne offengelegte Baseline, die HN-Diskussion liefert keine unabhängige Praxiserfahrung.

## Worum es geht
Wie gibt man KI-Agenten Schreibzugriff auf Unternehmenssysteme, ohne ihnen pauschal ganze APIs freizuschalten, und wie verhindert man, dass sie jede Aufgabe von vorn lösen? Coral setzt dafür ein Gateway zwischen Agent und Zielsystem, das jeden Aufruf prüft und erfolgreiche Programme als wiederverwendbare Tools speichert. Relevant für Teams, die Agenten in SRE, Support, SecOps oder BI produktiv einsetzen wollen.

## Was man anwenden kann
1. **Regeln in Tool-Code statt nur Sichtbarkeit.** Laut Team entscheiden die meisten MCP-Gateways nur, welche Tools ein Agent sieht. Wer `update_record` darf, darf damit jeden Datensatz beliebig ändern. Coral setzt auf Custom Tools, die Regeln als Code enthalten, etwa `closeStaleTicket`: ändert nur ein Feld und nur bei Tickets ohne Aktivität seit 30 Tagen. Allow, Ask oder Block wird dann auf dieses Tool gesetzt. Übertragbares Prinzip, unabhängig vom Produkt.

2. **Doppelte Prüfung.** Ein Custom Tool bekommt eine eigene Einstufung, umgeht aber die Workspace-Policy nicht. Jeder Provider-Aufruf innerhalb des Tools wird erneut geprüft. Das verhindert, dass ein gespeichertes Tool zur Hintertür wird.

3. **Freigabe auf Aufrufebene.** Pro Provider-Tool und Custom Tool lässt sich Allow, Ask oder Block setzen. Der Genehmigende sieht den exakten Aufruf mit Argumenten. Security kann so einen einzelnen Refund-Lookup freigeben statt der ganzen Payments-API. Standard: lesende Tools laufen sofort, alles andere wartet auf Freigabe, das Programm pausiert so lange.

4. **Filtern im Programm, nicht im Modellkontext.** Agenten schicken kurze TypeScript-Programme über das MCP-Tool `exec`. Ein Programm ruft mehrere Tools auf, filtert und gibt nur das Nötige zurück. Beispiel aus dem README: offene Pull Requests holen, die ohne angefragte Reviewer filtern, Liste nach `#engineering` in Slack posten, nur die PR-Nummern an den Agenten zurückgeben. Das ist der behauptete Mechanismus hinter den Token-Einsparungen.

5. **Ablauf Tool-Suche.** Erst ruft ein Programm `coral.search` auf und liest die TypeScript-Signaturen der verfügbaren Tools. Dann folgt das Programm, das die Arbeit erledigt. Provider-Tools (z. B. Datadog, Slack) und Custom Tools erscheinen in derselben Suche.

6. **Lebenszyklus eines Custom Tools.** Erster Durchlauf: Agent schreibt Code, Slack-Post wird freigegeben, Agent speichert das Programm. Danach ruft er es in einem Schritt als `coral.private.<name>({ ... })` auf. Ein Workspace-Owner kann es unter `coral.shared` für alle im Workspace veröffentlichen.

7. **Tools teilen, Tokens nicht.** Pro Provider lässt sich einstellen, dass der Account des jeweiligen Aufrufers genutzt wird. Teammitglieder teilen Custom Tools, ohne API-Tokens zu teilen. Setzt voraus, dass jeder Nutzer beim Provider einen eigenen Account hat.

8. **Isolierte Ausführung.** Jedes Programm läuft in einem frischen V8-Isolate ohne Netzwerk, ohne Credentials, ohne Imports. Credentials ergänzt erst Coral nach der Policy-Prüfung. Jeder Run wird der startenden Person oder dem Agenten zugeordnet und läuft serverseitig weiter, wenn der Agent die Verbindung verliert.

9. **Einbindung in bestehende Agenten.** Workspace-MCP-URL aus der Coral-UI kopieren. Claude Code: `claude mcp add --scope user --transport http coral <your-mcp-url>`. Codex: `codex mcp add coral --url <your-mcp-url>`. Erster Test laut README: „What are my open pull requests?“. Provider kommen aus dem Katalog oder per eigenem OpenAPI-Dokument bzw. MCP-Server.

10. **Betrieb.** Einzelnutzer: Desktop-App (macOS Apple Silicon, Windows x64, Linux x86_64). Teams: Shared Server per Docker Compose oder Kubernetes. Pflicht sind ein OIDC-Identity-Provider, ein Reverse Proxy für TLS und SQLite oder Postgres. Ohne OIDC kein Teambetrieb.

11. **Einsatzmuster mit Grenze im Code.** SRE: Rollbacks nur für benannte Services. Support: Erstattungen, Eskalation an Menschen in definierten Fällen. BI: Tools aggregieren Warehouse-, CRM- und Billing-Daten und geben nur Metriken weiter. SecOps: Geräte nur in genehmigten Gruppen isolieren. Als Muster beschrieben, ohne Kundenfälle mit Zahlen.

12. **Upgrade von 0.x heißt Neuaufsetzen.** v1 ersetzt das SQL-Interface durch TypeScript-Programme, startet mit frischem State und konvertiert nichts aus 0.x.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 37 % weniger Tokens, 31 % weniger Kosten, 29 % weniger Zeit | 34 Aufgaben auf GitHub, Linear, Slack mit Opus 5.5, mit Custom Tools; Baseline nicht ausdrücklich genannt | Herstellerangabe |
| Opus-5.5-Genauigkeit zum Haiku-5.5-Preis | „für viele Aufgaben“, ohne Zahlen oder Methode | Herstellerangabe |
| 100 Unternehmensaufgaben | Blind-Benchmark gegen „andere MCP-Gateways“, Wettbewerber und Werte nicht genannt | Herstellerangabe |
| mehr als 450 Unternehmen, „Tausende Entwickler“ | Nutzerbasis | Herstellerangabe |
| mehr als 5.000 | anbindbare Datenbanken und SaaS-Tools über MCP oder OpenAPI | Herstellerangabe |
| 5.0k Sterne, 224 Forks, 1.547 Commits | GitHub-Repo zum Erfassungszeitpunkt | öffentlich sichtbar |
| 52 Punkte, 24 Kommentare | HN-Beitrag | öffentlich sichtbar |
| 30 Tage | Beispielregel im Custom Tool `closeStaleTicket` | Beispiel des Herstellers |

## Wortlaute
- „if an agent can call update_record, it can update any record in any way the tool allows.“ Die Kernkritik an reiner Tool-Sichtbarkeit als Sicherheitsmodell.
- „By default, tools that read data run right away and everything else needs your approval.“ Sinnvoller Startwert für Freigabe-Policies.
- „Only the pull request numbers go back to the agent, not the full GitHub response.“ Das Muster für Token-Einsparung durch Filtern im Code.
- „They re-read tool schemas, retry failed calls, and spend tokens rewriting code for steps they got right yesterday.“ Die Problemformulierung, mit der das Produkt positioniert wird.

## Grenzen und Widerspruch
- **Alle Zahlen sind Herstellerangaben.** Baseline, Aufgabenliste, Bewertung von „Genauigkeit“ und die verglichenen Gateways stehen nicht im README, nur Verweise auf externe Seiten. Die 37/31/29 Prozent gelten nur für GitHub, Linear, Slack mit Opus 5.5.
- **Nur das README.** Die verlinkten Seiten zu Policy, Rollen, Konzepten und Benchmarks lagen nicht vor.
- **Offene Sicherheitsfragen.** Nicht behandelt: Prompt Injection über Tool-Ergebnisse, Review und Versionierung von Custom Tools vor dem Teilen, Umgang mit fehlerhaft gespeicherten Tools.
- **„Zero data egress“ gilt nur für Coral selbst.** Was nach dem Filtern ans genutzte LLM geht, verlässt die eigene Infrastruktur, sofern das Modell nicht selbst gehostet ist.
- **Enterprise fehlt noch.** SAML, SCIM, erweitertes RBAC, unveränderliches Audit-Log und SLAs sind „coming soon“, ohne Preis und Termin. Die Open-Source-Edition protokolliert laut Hersteller jede Freigabe. Der Kern steht unter Apache 2.0 ohne Limits, `ee/` unter eigener Lizenz.
- **ISO/IEC 27001:2022** wird genannt, der Geltungsbereich (Produkt, Firma, Prozesse) nicht.
- **Run-Traces für Post-Training** eines eigenen Modells: Behauptung ohne Beleg. Datenschutz in den Traces wird nicht behandelt.
- **Diskussion dünn und belastet.** Viele frühe Kommentare sind kurzes Lob. jrflo und wavemode äußern den Verdacht auf Bot-Accounts, wavemode nennt das Projekt „vibecoded slop“ und flaggt den Beitrag; ein Beleg dafür fehlt. antonmry lobt die einfache Integration, arbeitet aber nach eigener Angabe für Coral. Die Fragen von ocamoglu (Deployment-Erfahrungen) und eb379 (Berechtigungen über mehrere Agenten) blieben in den ersten Kommentaren unbeantwortet.
- **Namenskonflikt.** fg137 verweist auf Googles eingestellte Coral-Plattform und viele gleichnamige Produkte; das Projekt ist über die Suche schlecht auffindbar.
