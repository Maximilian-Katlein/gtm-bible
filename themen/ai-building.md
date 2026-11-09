# AI Building (Agenten, Produkte, Werkzeuge)

Diese Seite sammelt, was Quellen über den Bau und Betrieb von KI-Agenten, KI-Produkten und Integrationsstandards wie MCP sagen. Dazu gehört auch, wie Organisationen Coding-Agenten einführen, begrenzen und kontrollieren.

Stand: 2026-11-09 · 3 Quellen · 30 Learnings

## Was mehrfach belegt ist

- **Ein Prototyp ist schnell gebaut, das Produkt daraus ist teuer (2 Quellen).** Ross Mike sagt, er baue eine Chatbot-Oberfläche mit Tools in zwei Stunden. Schwer und teuer seien eine fehlerfreie Nutzererfahrung und das Begrenzen von Halluzinationen; laut ihm ist das bei Tempo ein Großteil der Arbeit (Anekdote) [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md). Ein Empfänger von Trader-Tools aus dem Fachbereich beschreibt, was realistisch mit solchen Prototypen passiert: Sie werden komplett umgebaut oder verschwinden im Backlog. Verbessert werden sie nicht (Anekdote eines HN-Kommentators, nicht ausdrücklich bei Goldman) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Agenten mit Zugriff auf produktive Systeme brauchen eine Kontrollschicht (2 Quellen).** Ein Coding-Agent im Fachbereich kann ein Skript erzeugen, das ohne Review, Tests und Deployment-Kontrolle in den Tagesbetrieb gelangt. Es läuft dann mit den Rechten des Nutzers und auf Rechnern mit Kundendaten [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md). Wer externe Dienste anbindet, muss sicherstellen, dass das Modell nicht halluziniert oder Unsinn ausführt. Das gilt besonders bei Schreibzugriff auf Datenbanken [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).

## Taktiken und Abläufe

### Coding-Agenten in Organisationen steuern

- **Richtlinien nach Rolle und Werkzeugtyp schneiden.** Goldman Sachs trennt laut Bloomberg Chat-Assistenz von ausführenden Coding-Agenten. Der hauseigene Assistent mit Modellen mehrerer Anbieter bleibt für alle offen. Claude Code und GitHub sind seit Oktober auf Entwickler und Strats beschränkt. Eine frühere Einschränkung in Hongkong richtete sich nach Standort und Vertragsbedingungen, die neue richtet sich nach der Rolle. Das passt zu regulierten Großunternehmen [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Für jedes Tool einen verantwortlichen Engineer benennen.** Bevor Coding-Agenten an Nicht-Entwickler gehen, sollte für jedes daraus entstehende Tool ein namentlich benannter Engineer die Verantwortung übernehmen, bevor es Produktionsdaten berührt. Das empfiehlt die Redaktion von State of AI [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Agenten im Betrieb des Engineerings laufen lassen.** Goldman nutzt Claude weiter, aber unter Kontrolle des Engineerings. Laut Goldman halfen Anthropic-Engineers sechs Monate lang beim Bau von Agenten für Trade Accounting und Client Onboarding. Betrieben werden diese Agenten im Back Office von Goldmans Engineering (Herstellerangabe) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Vor dem Entzug eines Werkzeugs erfassen, wofür es genutzt wurde.** Bei Goldman waren das die Überwachung von Kundenflüssen, die Modellierung von Positionen und das Erstellen von Unterlagen. Diese Bedarfe könnte das Engineering übernehmen [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Eine Rücknahme erklären und Ersatz nennen.** State of AI hält die Einschränkung für richtig. Die Redaktion kritisiert aber, dass der CIO im Juli das Vibe Coding von Tradern lobte und der Zugang im Oktober per Richtlinien-Update entzogen wurde, ohne dass ein Ersatz genannt wurde. Das gilt für jede Rücknahme eines zuvor beworbenen KI-Werkzeugs (Meinung der Redaktion) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Eine abgesicherte Umgebung bauen, statt Agenten zu entziehen.** Das Engineering kann eine Programmierumgebung mit Abstraktionen bauen, in der Agenten aus dem Fachbereich arbeiten, ohne Schaden anzurichten. Das setzt Plattform-Kapazität im Engineering voraus. Der Vorschlag stammt aus der HN-Diskussion; siehe auch „Strittig“ [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).

### Modelle auswählen und testen

- **Mit einem API-Test anfangen, bevor man Hardware anschafft.** Moonshot bietet neben den Gewichten von Kimi K3.1 Pro auch Kimi-Chat und eine API an (Quickstart unter platform.kimi.ai). Ein API-Test mit eigenen Aufgaben ist der günstigere erste Schritt, bevor man über Hardware mit mehreren Knoten entscheidet. Bei diesem Test verlassen die Daten die eigene Infrastruktur [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).
- **Kosten pro Aufgabe im Pilot selbst messen**, weil die Card keine Zahlen zu Latenz, Tokenverbrauch oder niedrigeren Reasoning-Stufen nennt; siehe „Warnungen“ [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).

### Integrationen und MCP verstehen

- **Drei Stufen als Prüfraster für KI-Produkte.** Ein LLM allein sagt nur Text voraus. Mit Tools greift es über einzeln verdrahtete Integrationen auf Dienste zu. Mit MCP nutzt es eine einheitliche Übersetzungsschicht zu allen Diensten [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **Das MCP-Ökosystem hat vier Teile.** Der Client ist die Seite zu Nutzer und Modell, etwa Cursor, Windsurf oder Tempo. Das Protokoll ist die Zweiwegverbindung. Der Server übersetzt die Fähigkeiten eines Dienstes. Dazu kommt der Dienst selbst [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **MCP ist ein Standard und technisch kein Durchbruch.** Über ihn kommunizieren Sprachmodelle mit externen Diensten. Sein Wert hängt allein davon ab, wie viele Anbieter ihn umsetzen [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **Das Prinzip lernen, nicht nur den Standard.** Wer MCP versteht, kann sofort loslegen, sobald ein Standard final ist. Das gilt auch, wenn es am Ende nicht MCP wird [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **Startup-Idee für technische Gründer.** Gemeint ist ein Verzeichnis von MCP Servern mit GitHub-Code und Bereitstellung per Klick, das dem Nutzer eine eigene URL für seinen MCP Client liefert. Markttest, Wettbewerbsanalyse und Geschäftsmodell fehlen [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).

## Zahlen und Richtwerte

- **Goldman Sachs hat rund 47.000 Beschäftigte, davon mehr als 12.000 Entwickler**, also gut ein Viertel (Prozentwert ist eigene Rechnung). Die Entwickler waren laut CIO Argenti die erste Welle der KI-Einführung. Auf genau diese Gruppe beschränkt die Richtlinie vom Oktober die Coding-Agenten (Herstellerangabe) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Sechs Monate** waren Anthropic-Engineers laut Goldman in der Bank, um Agenten für Trade Accounting und Client Onboarding zu bauen (Herstellerangabe) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Harvey Legal Agent:** Kimi K3.1 Pro erreicht 23,7, Claude Fable 5.1 kommt auf 19,1 und DeepSeek auf 21,0. Für GPT-6 Astra, Opus 5.5 und GLM-5.3 sind keine Werte angegeben (Herstellerangabe) [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).
- **Messbedingungen der Kimi-Benchmarks:** Reasoning-Effort max, temperature 1.0, top-p 0.95 bei allen Werten (Herstellerangabe) [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).
- **Zwei Stunden** braucht Ross Mike nach eigener Aussage für eine Chatbot-Oberfläche mit Tools. Für ein fehlerfreies Produkt reicht das bei Weitem nicht (Anekdote) [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).

## Werkzeuge

- **Claude Code und GitHub:** Bei Goldman sind sie seit Oktober auf Entwickler und Strats beschränkt. Der hauseigene Chat-Assistent mit Modellen mehrerer Anbieter bleibt für alle offen [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Gemini mit Pauschalabrechnung und Drosselung:** Laut einem Kommentator wechselt seine Organisation für Nutzer außerhalb des Engineerings zu Gemini, weil Anthropic keinen normalisierten Abrechnungssatz anbiete (Anekdote) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Kimi K3.1 Pro:** Es gibt offene Gewichte, Kimi-Chat und eine API (platform.kimi.ai). Preise und Rate-Limits nennt die Card nicht [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).
- **MCP Clients:** Cursor, Windsurf, Tempo [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **Datenbanken über MCP:** Ist ein Modell per MCP mit Convex oder Supabase verbunden, legt es auf Zuruf einen neuen Eintrag an und weiß, wie das geht [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).

## Wortlaute und Vorlagen

- „Information barriers, data entitlements and software approval rules still apply when the code came from a prompt.“ [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- „a named engineer should take responsibility for it before it touches production data.“ [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- „when a tool is taken away, it's worth recording what people were using it for.“ [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- „Withdrawing access through a guideline update, with no replacement mentioned in Bloomberg's reporting, tells the traders who found good uses that they were the risk.“ [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- „Completely overhauled to be operationally viable, perhaps. Thrown into the dark recesses of the backlog, more likely.“ [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- „llms by themselves are incapable of doing anything meaningful“ [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md)
- „understanding how this works means you'll understand how the next thing works and when that becomes finalized you hit the ground running“ [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md)

## Warnungen und Fehler

### Agenten in Fachbereichen und regulierten Branchen

- **Informationsbarrieren gelten auch für agentengebaute Tools.** Das betrifft zum Beispiel die Trennung zwischen Deal-Bankern und Tradern. Ein Tool, das ein Trader mit einem Agenten baut, kennt diese Kontrollen nicht, und das Engineering sieht es nur, wenn jemand es vorlegt. Das gilt in der regulierten Finanzbranche [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Die eigentlichen Hürden für Code aus Fachbereichen sind regulatorisch:** Zugriffsberechtigungen, Datenschutz, Datenlizenzen, granulare Datenberechtigungen, auditierbarer Datenzugriff, auditierbare Freigabeketten und Finanzrisiko. Ein Kommentator sagt, der Agent beschleunige nur ein altes Muster: Fachbereiche bauen einen POC und drängen die IT, ihn in Produktion zu bringen [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Auch Entwickler verlieren den Überblick.** Bei hohem Agenten-Output verlieren laut einem Kommentator auch Entwickler die Fähigkeit, Code sorgfältig zu lesen. Der Artikel nennt einen Meta-Engineer, der Code ausliefere, den er nicht vollständig erklären kann [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Tokenbasierte Abrechnung läuft bei breiter Verteilung aus dem Ruder.** Ein Kommentator berichtet, seine Organisation nehme Claude wegen chronischer Kostenüberschreitungen zurück. Für Goldman selbst gibt es keinen Kostenbeleg (Anekdote) [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).

### Integrationen und MCP

- **Viele Tools an einem Modell skalieren schlecht.** Jeder Anbieter baut seine API anders, die Abläufe müssen Schritt für Schritt geplant werden, und in vielen Randfällen scheitert die Kette [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **Fest verdrahtete Ketten brechen bei API-Änderungen.** Ein Beispiel ist eine Kette, die eine Slack-Nachricht liest und als SMS weiterleitet. Je mehr Dienste daran hängen, desto größer wird der Wartungsaufwand [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **MCP-Server einzurichten war umständlich.** Zum Zeitpunkt der Aufnahme hieß das: herunterladen, Dateien verschieben, Werte kopieren, vieles davon lokal. Für nicht-technische Teams war MCP damals kein Werkzeug zur Selbstbedienung. Den heutigen Stand vor der Anwendung prüfen (Anekdote) [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- **Wer auf MCP baut, trägt ein Standardrisiko.** Der Sprecher hält MCP selbst nicht für gesetzt: Anthropic könne den Standard ändern, oder ein anderer Anbieter könne einen eigenen vorlegen [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).

### Modelle und Benchmarks

- **Die Kimi-Benchmarks wurden nur auf der höchsten Stufe gemessen** (Reasoning-Effort max). Für niedrigere Stufen, Latenz und Tokenverbrauch gibt es keine Zahlen (Herstellerangabe) [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).
- **Rechtsaufgaben sind schwach abgedeckt.** Kein gelistetes Modell kommt im Harvey Legal Agent über 23,7. Nach diesen Zahlen eignet sich keines für autonome juristische Agenten (Herstellerangabe) [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md).

### Quellenlage

- **Die Goldman-Meldung ist kein Urteil gegen Frontier-Modelle.** Die Grenze ist rollenbasiert, Goldman baut weiter Claude-Agenten und ist laut S-1 vom 26. Oktober zusammen mit Morgan Stanley Lead Underwriter des Anthropic-Börsengangs. Bewertungen von 1,5 oder 2 Billionen Dollar stammen nur aus Schlagzeile und Kommentaren [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).
- **Die Goldman-Quelle ist schwach.** Sie erzählt einen Bloomberg-Bericht mit anonymen Quellen nach und erscheint auf einer Seite mit Sponsoring-Label, die Kommentatoren für KI-geschrieben halten. Zahlen und Zitate vor jeder Weiterverwendung gegen Bloomberg und Financial Times prüfen [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md).

## Strittig

- **Coding-Agenten entziehen oder eine abgesicherte Umgebung bauen?** Goldman beschränkt Claude Code auf Entwickler und Strats. State of AI hält das für richtig und verlangt für jedes Tool einen verantwortlichen Engineer [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md). Aus der HN-Diskussion kommt der Gegenvorschlag: Das Engineering soll eine Programmierumgebung bauen, in der Agenten aus dem Fachbereich keinen Schaden anrichten können [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md). Vermutlich entscheiden zwei Bedingungen: ob Plattform-Kapazität im Engineering vorhanden ist und wie streng die Regulierung ist. Beide Positionen stammen aus derselben Quelle, aber von verschiedenen Stimmen (Redaktion und Kommentator).
- **Reicht die Beschränkung auf Engineers als Kontrolle?** Die Goldman-Richtlinie geht davon aus, dass Entwickler mit Coding-Agenten sicher umgehen. Laut CIO waren sie die erste Welle der Einführung [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md). Ein Kommentator hält dagegen: Bei hohem Agenten-Output verlieren auch Entwickler die Fähigkeit, Code sorgfältig zu lesen [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md). Den Unterschied erklärt vermutlich das Volumen an Agentencode pro Entwickler.

## Offene Fragen

- Wie wird MCP mit Schreibzugriff auf Datenbanken oder produktive Systeme abgesichert? Das Video behandelt das nicht [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md).
- Ist die Einrichtung von MCP-Servern inzwischen für nicht-technische Teams machbar? [MCP erklärt](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md)
- Was kosten Kimi K3.1 Pro pro Aufgabe, welche Latenz hat es auf niedrigeren Reasoning-Stufen, und welche Preise und Rate-Limits gelten für die API? [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- Hatte Goldman eigene Kostenprobleme mit tokenbasierter Abrechnung, oder ging es nur um Kontrolle? [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
- Bestätigen Bloomberg und Financial Times die Zahlen und Zitate zu Goldman? [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
