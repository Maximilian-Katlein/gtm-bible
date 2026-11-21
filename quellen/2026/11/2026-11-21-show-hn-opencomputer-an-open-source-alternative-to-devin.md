# Show HN: OpenComputer, eine Open-Source-Alternative zu Devin

> **Quelle:** [Show HN: OpenComputer – an open source alternative to Devin](https://github.com/diggerhq/opencomputer) · diggerhq (GitHub-Organisation) · Diskussion (Show HN mit README als Artikel, [HN-Thread](https://news.ycombinator.com/item?id=50581403), 69 Punkte, 22 Kommentare) · 2026-11-21
> **Sprecher verkauft:** OpenComputer, einen per Slack beauftragten Coding Agent, selbst hostbar unter Apache 2.0 oder als OpenComputer Cloud mit Abrechnung in Arbeitsminuten · **Zielmarkt der Aussagen:** Softwareteams, die einen Devin-Ersatz in der eigenen Cloud oder gehostet betreiben wollen · **Beweislage:** Alle Leistungszahlen stammen aus einem eigenen Benchmark ohne offengelegte Methodik.

## Worum es geht
Die Quelle beantwortet, wie ein Team einen Coding Agent aus Slack heraus beauftragen und das Ergebnis als Pull Request erhalten kann, ohne an einen geschlossenen Anbieter wie Devin gebunden zu sein. Sie richtet sich an Entwicklerteams, die Agenten selbst betreiben wollen. Die Diskussion zeigt, dass der Anspruch „self-hosted“ vor einem Einsatz selbst geprüft werden muss.

## Was man anwenden kann
1. **Arbeitsablauf über Slack.** Man erwähnt @Computer in einem Slack-Thread mit einer Aufgabe. Der Agent arbeitet auf einem eigenen Rechner, das Team kann zusehen und eingreifen, das Ergebnis landet als Pull Request. Voraussetzung ist Slack. Andere Chat-Plattformen wie Discord nennt das README nicht.

2. **Kein eigener Agent, sondern Orchestrierung.** Das Gateway „Calvin“ nimmt Slack Events entgegen und startet je nach Konfiguration eine Session mit Claude Code, Codex oder OpenCode. Wer OpenComputer prüft, bewertet also vor allem Infrastruktur, Isolation und Slack-Anbindung. Die eigentliche Agentenleistung hängt vom gewählten Harness und dessen Modell ab.

3. **Architektur für Self-Hosting.** Der Stack läuft laut README auf einer einzelnen VM. Der Hersteller empfiehlt, diese VM auf ausgehenden Netzwerkverkehr zu beschränken. Jede Session wird mit rootless Podman isoliert. Der Zustand geht zuerst auf die lokale Disk und wird dann in einen git-gestützten Speicher geschrieben.

4. **Cloudflare-Abhängigkeit vor Einsatz prüfen.** Der übrige Stack läuft auf Cloudflare Workers und Durable Objects. Fly und weitere Plattformen sind nur angekündigt. Wer aus Souveränitäts- oder Compliance-Gründen keine Cloudflare-Abhängigkeit will, kann OpenComputer nach aktuellem Stand vermutlich nicht vollständig im eigenen Account betreiben. Das ist eine Lesart des README, keine ausdrückliche Aussage. Prüfgrundlage ist die Datei SELFHOSTING.md im Repository.

5. **Testlauf in der Cloud.** Schnellster Einstieg laut README: registrieren, Repos verbinden, Slack App installieren. Der Trial läuft 3 Tage mit 600 Arbeitsminuten. Nötig ist ein Slack Workspace mit Installationsrechten. Preise nach dem Trial nennt die Quelle nicht.

6. **Eigenes Modellabo mitbringen.** In der Cloud lässt sich ein eigenes ChatGPT- bzw. Codex-Abonnement einbinden. Dann zahlt man beim Anbieter nur die Arbeitsminuten. Ob das auch für Claude Code gilt, bleibt offen.

7. **Positionierung über ein Vergleichsprodukt.** Das README definiert sich fast nur über Devin. Ein Kommentator rät, direkt zu erklären, was das Produkt tut. Für die eigene Positionierung heißt das: Ein Konkurrent als Ankerbegriff trägt nur, wenn die Zielgruppe ihn kennt. Ein weiterer Kommentar kritisiert, der Name „OpenComputer“ sage nichts aus und sei bereits vergeben.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 56 s vs. 185 s, Faktor 3,3 | Zeit, bis alle 4 PRs offen sind und CI grün ist, OpenComputer gegen Devin | Herstellerangabe, eigener Benchmark, nur 4 PRs, Aufgaben und Repos nicht genannt |
| 24 s vs. 62 s, Faktor 2,6 | Zeit bis zum ersten Push gegen den Durchschnitt der „4 populärsten Cloud-Agenten“ | Herstellerangabe, Agenten nicht benannt |
| 3 Tage, 600 Arbeitsminuten | Kostenloser Trial der Cloud-Variante | Herstellerangabe |
| 2 Minuten | Startzeit in der OpenComputer Cloud | Herstellerangabe |
| 2.753 Commits, 751 Stars, 80 Forks | Repository-Kennzahlen beim Abruf | eigene Daten (Abruf GitHub) |
| 69 Punkte, 22 Kommentare | Resonanz auf Hacker News | eigene Daten |

Die beiden Geschwindigkeitsangaben messen Verschiedenes und sind nicht vergleichbar. Zu Codequalität oder Erfolgsquote gibt es keine Zahl.

## Wortlaute
- „OpenComputer is the open source, self hostable alternative to Devin.“ (README) Steht für die Positionierung allein über den Vergleich mit einem Wettbewerber.
- „It is open source from the compute layer up, so you can run all of it in your own cloud account“ (README) Steht für den Offenheitsanspruch, den die Diskussion hinterfragt.
- „We built it to feel as fast as Claude Code on your laptop“ (README) Steht für das Designziel lokaler Geschwindigkeit, belegt nur durch den eigenen Benchmark.

## Grenzen und Widerspruch
- **Benchmark ohne Methodik.** Unbekannt sind Aufgaben, Repos, Modelle, Wiederholungen und die vier verglichenen Cloud-Agenten. Niemand in der vorliegenden Diskussion hat die Zahlen nachgeprüft.
- **Offenheit fraglich.** andyjtyler fragt, ob wirklich alles offen ist oder nur der Harness-Code. Die Cloudflare-Bindung verstärkt die Frage. Eine Antwort der Autoren liegt nicht vor.
- **Keine lokalen Modelle.** SilentM68 vermisst Ollama und ein Heimserver-Szenario. OpenComputer delegiert an Claude Code, Codex oder OpenCode. Open-Weight-Modelle auf eigener Hardware erwähnt das README nicht. Für Sovereign-AI-Anforderungen ist das eine Lücke.
- **Abgrenzung fehlt.** swyx fragt nach dem Unterschied zu OpenHands (früher OpenDevin), einer bestehenden Open-Source-Alternative. Keine Antwort im Auszug.
- **Preis unklar.** namanyayg fragt, wie das Projekt so günstig sein kann. Die Prämisse ist nicht belegt, denn die Quelle nennt keine Preise außer dem Trial.
- **Sicherheitsmodell dünn.** Secrets, Repo-Rechte und Netzwerkfilter sind nicht beschrieben. Unklar bleibt auch, wie Slack Events eine VM mit reinem Outbound-Zugang erreichen.
- **Datenlage.** Nur 7 von 22 Kommentaren lagen vor, darin keine Praxisberichte. Verlinkte Seiten (Benchmark, Docs, SELFHOSTING.md) wurden nicht ausgewertet.
