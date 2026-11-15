# Greg Isenberg

Greg Isenberg ist Host eines Startup-Podcasts, in dem technische Gäste neue KI-Bausteine wie MCP, Agenten, Skills und schnelle Entscheidungsmodelle für Gründer einordnen oder live Apps bauen und Isenberg selbst vorführt, wie aus wachsenden Reddit-Communities Startup-Ideen, Firmennamen und Content entstehen, und zuhören lohnt sich, weil daraus Geschäftschancen und nachbaubare Abläufe für Solo-Gründer und kleine Teams werden.

Stand: 2026-11-15 · 6 Quellen

Verkauft: Isenberg nennt als eigenes Unternehmen die Designagentur designscientist.com mit Fokus auf Copy und Conversion, nach eigener Aussage ein Seven-Figure-Business, und spricht von mehreren weiteren Multi-Millionen-Unternehmen aus Reddit-Ideen, ohne sie zu benennen ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16, 20:36). Das Recherche-Tool Gummy Search wird ausführlich gezeigt. Ob eine Partnerschaft besteht, wird nicht offengelegt ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 06:40). Der Gast Ross Mike arbeitet bei Tempo. Tempo kommt in der MCP-Folge als Beispiel für einen MCP Client vor ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:07, 18:25). Der Gast Remy betreibt einen Newsletter mit eigenem Team und zeigt im Kurs ein persönliches Agenten-Setup ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 53:14). Der Gast Riley verweist in der App-Folge auf Beobachtungen aus einer eigenen Community, deren Name und Angebot in den Learnings nicht genannt werden ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 37:35). Die Jev-Folge bewirbt Vercel (AI Gateway und AI Package) als sofortigen Zugangsweg zum Modell. Ob dafür bezahlt wurde und ob die Sprecher zum Anbieter von Jev gehören, geht aus den Learnings nicht hervor ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 26:30).

## Kernideen

*Sechs Quellen, alle aus Isenbergs Kanal. In fünf davon stammt ein Großteil der Aussagen von Gästen (Ross Mike, Remy, Riley) oder von in den Learnings nicht namentlich genannten Sprechern. Nur die Reddit-Folge zeigt Isenbergs eigene Methode (Kernideen 15 und 16). Wiederholt heißt hier: Die Idee taucht in mehreren Folgen des Kanals auf. Siehe „Wo Vorsicht geboten ist“.*

### 1. Kontext ist knapp: In die Dauerdatei gehört nur, was der Agent nicht selbst wissen kann
*Wiederholt in 3 Quellen.*
- In agent.md oder claude.md gehört nur proprietäres Wissen, das in jedem Dialogschritt gebraucht wird. Den Tech-Stack muss man nicht nennen, weil der Agent die Codebasis selbst liest. „telling Claude Code this code base uses React, I don't need to because it has the codebase in context.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 02:05)
- Selbstverständlichkeiten verschwenden Kontext. Nur Abweichungen vom Standard notieren, etwa eine besondere Währung. „Don't tell the model things that should already be known“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 32:15)
- Eine 1.000 Zeilen lange claude.md kostet nach Schätzung des Sprechers rund 7.000 Tokens bei jedem Lauf ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 04:20)
- Remy nennt als Best Practice höchstens etwa 200 Zeilen für die Claude.md ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 30:44)
- Code ist selbst Kontext: Ein solides Template für Web oder Mobile gibt dem Agenten ein Fundament. Der Sprecher erwartet eine Renaissance von Templates ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:10). Mehr dazu in Kernidee 13.
- Das Kontextfenster füllt sich ohnehin schnell: Es startet laut Sprecher bei etwa 20.000 Tokens, und ab etwa 80 Prozent Füllstand lässt die Leistung deutlich nach ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 06:45, 31:15)
- Die Kehrseite: Was das Modell nicht wissen kann, muss man liefern. Modelle kennen veraltete API-Syntax, deshalb die aktuelle Dokumentation per Perplexity suchen und den Code-Ausschnitt an Cursor übergeben ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 47:20)

### 2. Skills entstehen aus einem gelungenen Durchlauf, nicht am Reißbrett
*Wiederholt in 3 Quellen.*
- Erst den Ablauf im Dialog mit dem Agenten Schritt für Schritt durchspielen, dann den Agenten den Verlauf prüfen und daraus die skill.md schreiben lassen ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 11:40)
- Den Skill sofort zu schreiben, nennt der Sprecher den größten Fehler. „and then they'll jump to create the skill right away. This is the worst thing you can do.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 08:30)
- Remy beschreibt denselben Weg: Aufgabe einmal manuell erledigen, dann „Hey, create a skill for what we just did.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 44:25). Remys Ads-Analyst-Skill entstand aus etwa zwei Stunden Durchlauf ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 49:09)
- Folgerung für fremde Skills: Ihnen fehlt der Kontext eines eigenen erfolgreichen Laufs ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 12:40)
- Frühe Form desselben Gedankens ohne Skills: Erprobte Prompts und App-Muster in einer chat.md im Projektordner sammeln, damit KI und andere Nutzer bei neuen Anfragen auf funktionierende Vorlagen zugreifen ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 31:15)

### 3. Prozesswissen gehört in Skills, die erst bei Bedarf geladen werden
*Wiederholt in 2 Quellen.*
- Umfangreiches Wissen aus der claude.md „probably should be a skill“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 04:20)
- Progressive Disclosure: Bis zum Abruf liegen nur Name und Beschreibung im Kontext. Gemessen 53 statt 944 Tokens für einen Skill ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 30:40)
- Aufbau, Farben und Preisposition eines Angebots gehören in einen Skill, nicht in die memory.md. Sonst iteriert man jede Woche erneut 15 bis 30 Minuten ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 40:51)
- Abgrenzung: Die Dauerdatei hält, wer man ist und wie man arbeitet (Rolle, Geschäftsmodell, ICP, Präferenzen). Skills halten, wie eine konkrete Aufgabe erledigt wird ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 20:26)

### 4. Sicherheit heißt vor allem: Zugriff begrenzen
*Wiederholt in 4 Quellen.*
- Ein autonomer E-Mail-Agent bekommt eine eigene Adresse statt Zugriff auf das Hauptpostfach. „I haven't given it access to my email, because there's like attack vectors and I've been hacked before“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 07:35)
- Remy: Agenten mit Budget- oder Systemzugriff, etwa ein Meta-Ads-Agent, bekommen nur so viele Rechte, dass der Schaden bei Kompromittierung begrenzt bleibt, zum Beispiel Read-only. „I like to think of security as in just like scoping what they have access to.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 08:59)
- Fremde Skills von Marktplätzen sind ein einfacher Angriffsweg ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 12:40)
- Schon in der MCP-Folge: „you have to make sure the llm doesn't hallucinate or do something stupid“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 06:26)
- Verwandt beim Bauen: Änderungen der KI umkehrbar halten. In Cursor „Save all“ statt „Accept all“ nutzen, weil Letzteres laut Sprecher nicht rückgängig zu machen ist. „hit save all instead of accept all. Accept all is not reversible.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 34:40)

### 5. Der Wert entsteht in der Schicht um das Modell
*Wiederholt in 5 Quellen.*
- Ein Sprachmodell allein sagt nur Text voraus. „llms by themselves are incapable of doing anything meaningful“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 02:39)
- Eine Chatbot-Oberfläche mit Tools sei in zwei Stunden gebaut. Schwer und teuer seien fehlerfreie Nutzererfahrung und begrenzte Halluzinationen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 18:25)
- Bei ähnlichen Basismodellen bestimmen Harness und Werkzeuge die Ausgabequalität mit, etwa Cursor, Claude Code oder Codex. „the harness... is going to matter even more.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 27:10)
- Für die Einarbeitung in ein neues Harness wie OpenClaw sollte man rund zwei Wochen einplanen ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 23:50)
- Das Modell selbst ist im Prototyp austauschbar: Bei anhaltenden API-Fehlern ließ der Sprecher Cursor den Code von OpenAI auf Anthropic umstellen. „Can you change this to Anthropic, please?“ Die Ursache des Fehlers blieb dabei ungeklärt ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 51:10)
- GTM-Folgerung für Produkte auf fremden Modellen: Ein „OpenAI Wrapper“ rechnet sich nur, wenn die monatlichen Abo-Einnahmen pro Nutzer die variablen API-Kosten pro Nutzung übersteigen ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 36:00)
- Neu in der Jev-Folge: Auch die Architektur um das Modell zählt. Ein schneller Klassifikator sortiert vor, das teure LLM bekommt nur die unklaren Fälle ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 19:40). Mehr dazu in Kernidee 18.

### 6. Agenten brauchen explizite Kriterien und einen messbaren Endpunkt
*Wiederholt in 4 Quellen.*
- Ein Agent beendet seine Schleife aus Beobachten, Entscheiden und Handeln erst, wenn er die Aufgabe für erledigt hält. Messbare Vorgaben legen das Ende fest. „you might say compile 10 sources, and then create a report as a PowerPoint.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 05:23)
- Ohne feste Kriterien stufte ein E-Mail-Agent jede Sponsoranfrage als seriös ein. Erst eine Prüfregel machte das Filtern brauchbar. „If two of these don't exist are not in good standing, automatic rejection.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 09:30)
- Dasselbe gilt für Interfaces: Datenfelder, Stil und Interaktionslogik samt Farben ausschreiben und den Zweck einer Funktion mitnennen, damit das Modell passende UI-Muster wählt. „I like to make sure I tell it the purpose because it will actually use that in the prompt.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 10:45, 13:30)
- Zugespitzt beim Klassifikator: Statt Freitext ein festes Ausgabeschema mit allen erlaubten Optionen. Das Modell verteilt nur Wahrscheinlichkeiten auf diese Optionen und erfindet keine eigenen Kategorien. „you define an input ... and then the output is a schema.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 03:15)
- Auch hier eine harte Schwelle wie beim Sponsorfilter: Eine Agentur bearbeitet Kontaktanfragen mit einem Lead-Score ab 0,98 sofort ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00)

### 7. Klein anfangen: ein Agent, dann Skills, dann Sub-Agenten
*Wiederholt in 2 Quellen.*
- „if you want to scale for productivity, it starts with one agent and you building up the skills.“ Sub-Agenten erst, wenn Workflows feststehen. Der Sprecher steuert heute einen Hauptagenten mit fünf Sub-Agenten ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 14:35)
- Remy organisiert nach Firma oder Kunde, darunter je Funktion ein Bereich mit eigener Rolle und eigenen Skills, ein Orchestrator darüber ist optional ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:52)

### 8. MCP ist ein Standard und kein technischer Durchbruch. Sein Wert hängt an der Verbreitung.
- MCP legt fest, wie Sprachmodelle mit externen Diensten sprechen. Nützlich wird es erst, wenn viele Anbieter mitmachen. „from a technological perspective all they did was create a standard“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 12:51)
- Gesetzt ist der Standard nicht: Anthropic könnte ihn ändern, oder ein anderer Anbieter bringt einen eigenen. „I don't know if mCP has fully won I think it needs to be challenged“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 17:43)
- Das Wissen lässt sich auf den nächsten Standard übertragen. Wer das Prinzip verstanden hat, kann sofort loslegen, sobald ein Standard final ist, auch wenn es am Ende nicht MCP wird ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 19:33)
- Isenberg vergleicht MCP mit HTTPS und SMTP: Auf verbreiteten Protokollen seien große Unternehmen entstanden ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54)
- Im Kurs laufen Gmail, Granola, Stripe und Notion bereits über MCP-Anbindungen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57). Das spricht für wachsende Verbreitung, belegt aber nicht, dass der Standard gesetzt ist.

### 9. Die Integrationsarbeit wandert vom KI-Produkt zum Dienstanbieter
- Den MCP Server baut der Anbieter des Dienstes. Eine Datenbankfirma, die von KI-Clients genutzt werden will, muss ihn also selbst liefern. „the mCP server is now in the hands of the service provider“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:59)
- GTM-Folgerung: Wer wachsen und Partner oder Entwickler anbinden will, muss seine Schnittstelle in einer Form anbieten, die für diese Sinn ergibt. Für Sprachmodelle ist diese Form laut Sprecher MCP ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 13:06)

### 10. Einzeln verdrahtete Tools skalieren nicht
- Jeder Anbieter baut seine API anders. Das bedeutet viel Handarbeit, Planung Schritt für Schritt und viele Randfälle, an denen die Kette scheitert ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 09:38)
- Eine feste Kette wie „Slack-Nachricht lesen und als SMS weiterleiten“ bricht, sobald einer der Dienste seine API ändert. Je mehr Dienste beteiligt sind, desto höher der Wartungsaufwand ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 10:18)
- Passend dazu brauchte ein Report-Generator mit acht Datenquellen fünf Korrekturschleifen bis zum fehlerfreien Lauf ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:45)
- Auch im Prototyp zeigt sich das: Der Stack aus V0, Cursor, Replit und Firebase verlangt Handarbeit zwischen den Werkzeugen, etwa manuell ausgeführte npm-Befehle, und wechselnde LLM-APIs brechen Code, den das Modell mit veralteter Syntax schreibt ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 33:35, 47:20)

### 11. Erst beobachten, dann handeln, solange der Standard nicht fertig ist
- Nicht-technischen Gründern rät der Sprecher, zu beobachten, welche Plattformen MCP ausbauen. Handeln sollen sie erst, wenn der Standard final ist und die Anbieter ihre Server gebaut haben. „I don't see any crazy business opportunities right now for a non-technical person even for a technical person“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 19:21)
- Der Grund: Die Einrichtung war zum Zeitpunkt der Aufnahme umständlich und für nicht-technische Teams nicht selbst machbar ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 13:57)
- **Entwicklung:** In der MCP-Folge (erfasst 2026-11-09) lautete der Rat „abwarten“. Im Kurs (erfasst 2026-11-13) richtet Remy MCP-Anbindungen für einen Solo-Workflow vor der Kamera ein, und Isenberg spricht von 10- bis 20-fachem Produktivitätsgewinn ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57, 38:44). Die Daten sind Erfassungsdaten, nicht Veröffentlichungsdaten. Die Reihenfolge der Aufnahmen ist daher nicht gesichert.

### 12. Fehlermeldungen sind Rohstoff für die nächste Korrektur
*Wiederholt in 2 Quellen.*
- „Error messages are good. Blank screens are bad.“ Cursor kann einen Stacktrace lesen und gezielt korrigieren, ein leerer Bildschirm liefert der KI nichts ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 44:20)
- Reagiert eine Funktion stumm, die KI ausdrücklich um Error Logs bitten und die sichtbare Meldung wörtlich zurück in den Chat kopieren. „can you please add error logs to the AI input field. I have no way of knowing what the problem is.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 39:35)
- Bei Skills derselbe Gedanke: nach Fehlschlag die genaue Fehlermeldung zurückgeben und die Lösung in die skill.md schreiben lassen. „give that failure back... update the skill so this doesn't happen again.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:45)
- **Entwicklung:** In der App-Folge (erfasst 2026-11-14) kopiert der Mensch Fehler von Hand zwischen Browser, Replit und Cursor hin und her. In der Folge zu Agenten und Skills (erfasst 2026-11-13) fragt der Agent selbst nach der Fehlermeldung und schreibt die Korrektur dauerhaft fest. Der verwendete Stack (V0, Replit, OpenAI-Wrapper) spricht dafür, dass die App-Folge älter ist, gesichert ist die Reihenfolge nicht.

### 13. Vorlagen sind der größte Zeithebel
*Wiederholt in 2 Quellen.*
- Die im Titel genannten 67 Minuten gelten nur mit fertigem Template. Ohne Vorlage kostet allein die Einrichtung von Bibliotheken und Ordnerstruktur Anfänger laut Sprecher bis zu 3 Stunden, eine vollständige App 6 bis 7 Stunden. „when I was first starting, that would take me 3 hours.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 08:35)
- Ein solides Template für Web oder Mobile gibt dem Agenten ein Fundament, der Sprecher erwartet eine Renaissance von Templates ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:10)
- Neben Code-Vorlagen auch Prompt-Vorlagen: erprobte Prompts in einer chat.md sammeln ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 31:15)

### 14. Die Lernkurve ist kurz, aber nicht null
*Wiederholt in 2 Quellen.*
- Riley schätzt, dass man mit 10 bis 15 Stunden Übung typische Fehler mit Claude systematisch beheben lernt. Riley hatte 50 Tage vor der Aufnahme nie programmiert. „You can create some really cool things in like 10 to 15 hours of practice.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 02:25)
- Die meisten Einsteiger scheitern laut Riley an den ersten Schritten. Wer hartnäckig weiterfragt, kommt meist im zweiten oder dritten Anlauf ans Ziel. „by the second or third try, like you will will your way to a working app.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 37:35)
- Auch Erfahrene brauchen Zeit: Die Einarbeitung in ein neues Harness wie OpenClaw dauerte rund zwei Wochen ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 23:50)

### 15. Ideen dort suchen, wo Menschen ihren Bedarf öffentlich äußern
*Bisher in 1 Quelle, aber Isenbergs eigene Methode.*
- Nicht die größten, sondern mittelgroße und wachsende Communities ansehen. Subreddits mit 10.000 bis 100.000 Mitgliedern nach Wachstum sortiert deuten auf neue, gerade trendende Themen hin und beantworten so die Why-now-Frage. „the mistake people make here is they focus just on these big subreddits“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:11)
- Zu jeder Community drei Fragen: Ist das interessant, habe ich einen unfairen Vorteil durch eigene Betroffenheit oder Kontakte, kann ich dafür etwas bauen. „do I have an unfair advantage in that subreddit“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:55)
- Beiträge in fester Reihenfolge lesen: erst Ärger und Schmerz, dann Kaufberatungsfragen, zuletzt Lösungswünsche samt bestehendem Wettbewerb, mit Blick auf Upvotes und Kommentare. „these are people screaming they want these products to exist“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 10:34)
- Dieselbe Quelle liefert auch den Namen: Eine Formulierung aus der Community wurde zu designscientist.com. „I wish a designer was more like a scientist less art more science“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 18:04)
- Ergänzend Kommentare unter den Top-Videos der Nischen-Creators lesen und auf einem One-Pager verdichten, bevor gebaut wird ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:08)
- Verwandt mit Kernidee 2: Auch hier steht Handarbeit am Original vor dem Bauen.
- Ein zweiter Suchweg kommt aus der Jev-Folge: nicht nach geäußertem Schmerz suchen, sondern nach Betrieben mit teurer oder langsamer Eingangs-Queue (siehe Kernidee 18).

### 16. Ein Produkt allein reicht nicht mehr: Publikum und Vertrieb gehören dazu
*Bisher in 1 Quelle, von Isenberg selbst.*
- Gründer müssten Publikum und Community aufbauen, deshalb nutzt Isenberg dieselbe Recherche für Produkt- und Content-Ideen. „it's not about just building a product anymore you need to attract an audience“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 01:10)
- Ein bestehender Markt schreckt Isenberg nicht ab, weil etablierte Anbieter oft schwaches Marketing machen und in Social Media fehlen. Dazu kommen Partnerschaften mit Creators. „more often than not you'll notice that the marketing is bad and they're not doing anything on social“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 09:20)
- Content-Formate aus dem Top Content derselben Community ableiten: Laufen lange Geschichten oder Memes? „you see the types of formats that work is it long stories is it memes“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 18:48)
- Für designscientist.com folgte auf das Wireframe in Framer direkt das Posten darüber ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16)
- Anknüpfung an Kernidee 5: Dort liegt der Engpass in Nutzererfahrung statt Technik, hier in Aufmerksamkeit statt Produkt. In beiden Fällen ist das Bauen selbst nicht der knappe Teil.
- **Entwicklung:** Mit „anymore“ markiert Isenberg selbst einen Wandel gegenüber früher. Eine ältere gegenteilige Aussage liegt in den erfassten Quellen nicht vor.

### 17. KI-Ausgaben sind eine Richtung, kein Beleg
*Wiederholt in 4 Quellen.*
- KI-Zusammenfassungen von Community-Beiträgen sind nicht verlässlich genau. Muster am Originalbeitrag gegenprüfen. „sometimes that Gummy Search isn't 100% accurate so you want to double check these things“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 11:05)
- „Validiert“ heißt in der Reddit-Methode nur, dass Bedarf geäußert wird. Zahlungsbereitschaft, Marktgröße und Wettbewerb sind separat zu prüfen ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md))
- Eine vom Agenten gebaute Website enthielt trotz Recherche-Tool falsche E-Mail-Adresse und falschen Wohnort ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 12:39)
- Die Demo-App leitet Marktgrößen und Prognosen aus Videotranskripten ab, ungeprüft ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 55:35)
- Ein Klassifikator ohne Begründung verlangt Stichproben: Jev liefert nur das Ergebnis, kein Reasoning. Die Sprecher räumen ein, dass das Vertrauen kostet, und folgenreiche Entscheidungen brauchen menschliche Prüfung. „There's no internal reasoning or anything like that.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 13:00)
- Grenze im eigenen Test der Sprecher: Minütliche Kauf-, Halte- und Verkaufssignale für Bitcoin waren schlecht. „I would not put this model in front of like your stock portfolio“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 23:00)

### 18. Ein schneller Klassifikator vor dem teuren Prozess
*Bisher in 1 Quelle, Sprecher in den Learnings nicht namentlich zugeordnet.*
- Nicht jede Entscheidung braucht ein großes Sprachmodell. Ein Klassifikator mit festem Schema entscheidet laut Sprecher in etwa 200 Millisekunden pro Abfrage, herkömmliche LLMs bräuchten bis zu 30 Sekunden. „it takes around 200 milliseconds per query“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 19:15)
- Architektur „AI Traffic Cop“: Hohe Konfidenz geht direkt an Menschen, mittlere an ein LLM zur Vorverarbeitung, sehr niedrige wird verworfen. LLM-Kosten fallen so nur für unklare Fälle an. „Jev is basically this ... AI traffic cop.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 19:40)
- GTM-Einsatz Inbound: Eine Grafikdesign-Agentur bewertet Kontaktformular-Anfragen mit einem Feld „is good lead“ von 0 bis 1 und bearbeitet ab 0,98 sofort. Zahlen zur Abschlussquote fehlen ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00)
- GTM-Einsatz Bestand: Dasselbe Schema rückwirkend über alte Postfächer laufen lassen, um übersehene Anfragen und wertvolle Altkunden für eine erneute Ansprache zu finden. „are there any leads I missed?“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 18:05)
- Support: Tickets in Echtzeit dem zuständigen Produktteam zuweisen, wenn die Teams als feste Optionen im Schema stehen. Nicht gezeigt ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 18:45)
- Gründermuster: einen Betrieb mit teurer Eingangs-Queue suchen und den Klassifikator davorsetzen, etwa bei einem Vermittler lokaler Dienstleistungen. „find a business with an expensive queue of incoming information and then just put Jev at the front of that queue.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 21:10)
- Grenze: Nur für Aufgaben, deren mögliche Antworten vorher vollständig bekannt sind. Wo externes Wissen oder Abwägung nötig ist, etwa bei Finanzentscheidungen, schnitt ein LLM mit Nachrichtenzugriff (GPT-6 Astra) besser ab ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 03:15, 23:00)
- Anknüpfung an Kernidee 5: Die Wrapper-Rechnung (Abo-Einnahmen größer als API-Kosten) wird günstiger, wenn das teure Modell nur einen Teil der Fälle sieht. Und an Kernidee 6: Das feste Schema ist die strengste Form expliziter Kriterien.
- *Einordnung: In der App-Folge galt das Modell als austauschbar (Kernidee 5). Hier ist die Modellwahl selbst der Hebel, allerdings für eine andere Aufgabe (Entscheiden statt Generieren). Ein Widerspruch derselben Person liegt nicht vor, da die Sprecher verschieden sind.*

## Methoden und Abläufe

### Startup-Ideen aus Reddit finden (Isenbergs Ablauf)
1. **Communities filtern:** Subreddits mit 10.000 bis 100.000 Mitgliedern, sortiert nach Wachstum ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:11)
2. **Zeitfenster wechseln:** täglich, wöchentlich und monatlich ansehen, weil die Tagesansicht Treffer zeigt, die im Monat untergehen. Die Liste alle paar Wochen erneut prüfen ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 04:06)
3. **Drei Fragen notieren:** interessant, unfairer Vorteil, baubar ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:55)
4. **Kategorien auswerten:** In Gummy Search eine Audience anlegen. Das Tool gruppiert Beiträge in Pain and Anger, Hot Discussions, Top Content, Advice Requests, Solution Requests und Money Talk und fasst Muster per KI zusammen ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 06:40). Reihenfolge: Pain and Anger, dann Advice Requests, dann Solution Requests für den Wettbewerb ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 10:34)
5. **Gegenprüfen:** KI-Muster am Originalbeitrag kontrollieren ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 11:05)
6. **Creators der Nische sammeln:** per Perplexity die etwa 25 beliebtesten YouTube-Creators auflisten lassen und in ein Google Sheet übernehmen. Liefert der Prompt Unterhaltung, auf lehrreiche Kanäle nachschärfen. „I don't want funny YouTubes I'm talking about the top youtubeers that are educational for dogs“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 14:42)
7. **Kommentare lesen:** bei 20 bis 25 Top-Videos die meistgelikten Kommentare auf einem One-Pager verdichten ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:08)
8. **Namen aus der Community ableiten** ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 18:04)
9. **Wireframe und Website**, etwa in Framer in wenigen Stunden, dann darüber posten ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16)
10. **Content-Formate ableiten:** Top Content derselben Community auf funktionierende Formate prüfen, die Audience in Gummy Search direkt fragen, etwa ob sie Memes mag ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 18:48)

Nicht enthalten: Prüfung von Zahlungsbereitschaft, Marktgröße und Wettbewerb in der Tiefe (siehe Kernidee 17).

### Drei Stufen als Prüfraster für KI-Produkte
1. **LLM allein:** sagt nur Text voraus. „llms by themselves are incapable of doing anything meaningful“
2. **LLM plus Tools:** greift auf Dienste zu, aber jede Integration ist einzeln verdrahtet.
3. **LLM plus MCP:** eine einheitliche Übersetzungsschicht zu allen Diensten.

Quelle: [MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 02:39

### Die vier Teile des MCP-Ökosystems
1. **Client:** die Seite zu Nutzer und Modell, zum Beispiel Cursor, Windsurf oder Tempo
2. **Protokoll:** die Verbindung in beide Richtungen
3. **Server:** übersetzt, was ein Dienst kann
4. **Dienst:** das eigentliche Angebot, etwa eine Datenbank

„you have an mCP client you have the protocol you have an mCP server and you have a service“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:07)

### Woraus das Kontextfenster besteht
System-Prompt, agent.md, Skill-Beschreibungen, Tools, Codebasis und Dialog. Startwert laut Sprecher etwa 20.000 Tokens. Claude Code und Codex verdichten automatisch, wenn das Limit erreicht ist ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 06:45)

**Faustregel:** Zwischen frisch und etwa 70 Prozent Füllstand arbeiten. Ab etwa 80 Prozent neue Sitzung starten oder verdichten ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 31:15)

### Kontextdatei aufsetzen
1. **Richtiger Dateiname im Projektordner:** Claude.md (Claude Code), Gemini.md (Gemini), agents.md (Codex, Open Claw). Sie wird zu Beginn jeder Session geladen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 20:26)
2. **Inhalt:** Rolle, Geschäftsmodell, Arbeitspräferenzen, Tools mit Zweck, ideales Kundenprofil (ebd.)
3. **Ohne Vorlage:** Claude Chat oder Co-work Interviewfragen stellen lassen und daraus die Datei schreiben lassen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 21:15)
4. **Bei viel Material:** Ordner context anlegen (über mich, Brand Voice, ICP) und in die Hauptdatei nur die Anweisung schreiben, ihn vor jeder Aufgabe zu lesen. Ohne diese Anweisung lädt der Agent den Ordner nicht ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 23:28)
5. **Schlank halten:** nur Proprietäres und Abweichungen vom Standard, Richtwert etwa 200 Zeilen (siehe Kernidee 1)

### memory.md für dauerhaftes Lernen
- **Problem:** Korrekturen im Gespräch speichert der Agent nicht selbst. „never sign off emails with cheers, say warm regards.“ ist in der nächsten Session vergessen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 25:58)
- **Lösung:** Leere memory.md mit denselben Abschnitten wie die Kontextdatei anlegen. Oben in die Hauptdatei: memory.md lesen, bei Korrektur den passenden Abschnitt aktualisieren, Veraltetes ersetzen. „when I correct you or you learn something new, update the relevant section in memory.md.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 27:12)
- **Pflege:** Nur substanzielle Korrekturen speichern lassen und gelegentlich manuell aufräumen, damit keine widersprüchlichen Regeln entstehen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 30:44)

### Aufbau einer skill.md
name, description, darunter die Anweisungen. Die description entscheidet, wann der Agent den Skill lädt, und sollte die Anwendungsbedingung klar benennen. „There is a name, there is a description, and then underneath is a bunch of information.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 05:00)

### Skills bauen und härten
1. **Workflow identifizieren.**
2. **Im Dialog durchspielen,** bis der Ablauf einmal gelingt.
3. **Skill erzeugen lassen:** „review what you did and then create the skill“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 11:40) oder per eingebautem Skill Creator „create a skill for what we just did“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 44:25)
4. **Rekursiv härten:** Agent laufen lassen, bei Fehlschlag nach der genauen Fehlermeldung fragen, Fehler beheben lassen, Lösung in die skill.md zurückschreiben. „give that failure back... update the skill so this doesn't happen again.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:45)

**Variante:** Skill aus fremdem Lernmaterial, etwa einem transkribierten Kurs („mach daraus einen Viral-Hook-Skill“). Das Material muss als Text vorliegen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 44:25)

### Skills zeitgesteuert starten und verketten
- Per Scheduled Task in Co-work oder Claude Code: Ein Daily-Brief-Skill fasst um 9:00 Uhr Kalender, Inbox und Notion zusammen und ruft bei anstehenden Meetings einen Recherche-Skill für Talking Points auf ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 45:41)
- Remys Newsletter-Team: Ein Weekly-Research-Skill durchsucht jeden Donnerstagmorgen Twitter und Reddit nach AI-Neuigkeiten ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 53:14)

### Ordnerstruktur für ein persönliches Agenten-Setup
Ein Ordner je Firma oder Kunde, darin ein Unterordner je Funktion (Marketing, Executive Assistant, Content Team) mit eigener Rolle, eigenen Skills und Tool-Anbindungen, optional ein Orchestrator darüber ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:52)

### Klassifikator als Vorsortierung („AI Traffic Cop“)
1. **Queue finden:** einen Eingangsstrom mit vielen eindeutigen Fällen, der heute teuer oder langsam ist, etwa Kontaktformular, Postfach, Support-Tickets ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 21:10)
2. **Schema festlegen:** Eingabeobjekt und Ausgabefelder mit allen erlaubten Optionen. Beispiel Mail-Triage mit vier Feldern: Kategorie (Shopping, Work, Marketing, Finance, Security), Priorität (low bis urgent), Spam-Score in Prozent, Wahrscheinlichkeit einer nötigen manuellen Antwort. Komplette Mailobjekte gehen ohne Vorverarbeitung hinein ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 03:15, 04:50)
3. **Schwellen selbst setzen:** hohe Konfidenz direkt an Menschen, mittlere an ein LLM, sehr niedrige verwerfen. Die Agentur im Beispiel arbeitet mit 0,98 als Sofort-Schwelle für Leads ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00, 19:40)
4. **Stichproben prüfen,** weil das Modell keine Begründung liefert ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 13:00)
5. **Rückwirkend anwenden:** dasselbe Schema auf Altbestände, um übersehene Leads und Altkunden für Reaktivierung zu finden ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 18:05)
6. **Kosten vorab messen,** da die genannten Kostenangaben nicht zueinander passen (siehe „Wo Vorsicht geboten ist“)

**Zugang laut Quelle:** Warteliste beim Anbieter oder sofort über Vercel AI Gateway und Vercel AI Package ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 26:30)

### Einsatzfälle für ein Entscheidungsmodell finden
Einem KI-Agenten die Dokumentation des Modells geben, das eigene Geschäft beschreiben und nach täglichen Workflows fragen, die ein Entscheidungsmodell übernehmen könnte. „what sort of workflows do I do on the daily basis that could benefit from a decision maker like Jev?“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 26:45). Verwandt mit der Interviewmethode beim Aufsetzen der Kontextdatei.

### Prototyp-Stack ohne Programmierkenntnisse
Arbeitsteilung laut Sprecher, gedacht für Einzelpersonen und Prototypen, nicht für Produktivsoftware ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 25:50):
1. **V0:** Next.js-Frontend
2. **Cursor:** Backend und Logik
3. **Replit:** Ausführung und Deployment
4. **Firebase:** Datenbank und Login

Stolpersteine aus der Demo:
- **npm-Befehle von Hand ausführen:** Von der KI vorgeschlagene Befehle laufen nicht automatisch. Sie müssen in der Replit-Shell ausgeführt werden, sonst fehlen Bibliotheken wie framer-motion oder lucide-react ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 33:35)
- **„Save all“ statt „Accept all“** in Cursor, damit Änderungen umkehrbar bleiben (Stand der im Video gezeigten Version) ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 34:40)
- **Mit Template starten,** sonst kostet allein das Setup Stunden (siehe Kernidee 13)

### UI-Prompts in V0 schrittweise aufbauen
1. **Datenfelder festlegen.**
2. **Grundstil vorgeben.**
3. **Details ausschreiben:** Rahmen, Hintergrundtextur, Interaktionslogik samt Farben. „Sip is positive, spit is negative, sip should be green, spit should be red.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 10:45)
4. **Zweck jeder Funktion mitnennen,** damit das Modell passende UI-Muster wählt ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 13:30)
5. **Wenn Text nicht reicht:** Screenshot machen, Korrekturen farbig einzeichnen, Bild in den Chat einfügen ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 21:15)

### Debugging-Ablauf beim Bauen mit KI
1. **Stumme Fehler sichtbar machen:** die KI um Error Logs bitten ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 39:35)
2. **Meldung wörtlich zurückgeben:** Stacktrace in Cursor kopieren und gezielt korrigieren lassen ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 44:20)
3. **Bei API-Fehlern aktuelle Doku holen:** per Perplexity suchen, Code-Ausschnitt an Cursor übergeben ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 47:20)
4. **Notausgang:** auf einen anderen Modellanbieter umstellen lassen. Umgeht das Problem, klärt aber die Ursache nicht ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 51:10)
5. **Lösung festhalten:** in der chat.md (Prototyp) oder in der skill.md (Agent), siehe Kernidee 12 und 13

### Wirtschaftlichkeit eines Wrappers prüfen
Abo-Einnahmen pro Nutzer und Monat den variablen API-Kosten pro Nutzung gegenüberstellen. Nur wenn die Einnahmen höher liegen, rechnet sich das Produkt ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 36:00). Fixkosten laut Sprecher: Replit-Hosting ca. 20 USD, V0 15 bis 20 USD im Monat, Firebase anfangs kostenlos ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 26:55). Ein vorgeschalteter Klassifikator kann die variablen Kosten senken, weil das teure Modell nur unklare Fälle sieht (siehe Kernidee 18).

### Prüfregel statt Bauchgefühl beim Filtern
Sponsoranfragen werden auf Twitter, YouTube, Trustpilot und Finanzierung geprüft. Fehlen zwei Signale oder sind schlecht, folgt automatische Ablehnung und ein Eintrag „no contact“ im Google Sheet ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 09:30). Übertragbar auf Lead-Qualifizierung, dort aber nicht geprüft. Eine Variante mit Score statt Regel zeigt die Jev-Folge: Lead-Wert von 0 bis 1, Sofortbearbeitung ab 0,98 ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00).

### Beispiele aus den Folgen
- **Designagentur aus Reddit-Beiträgen:** Startup-Gründer klagten, ihre Websites sähen gut aus, konvertierten aber nicht. Daraus entstand designscientist.com mit Fokus auf Copy und Conversion, Wireframe in wenigen Stunden in Framer, danach Posts darüber. Wie daraus Kunden wurden, sagt Isenberg nicht ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16)
- **Datenbank per MCP:** Ist ein Modell mit Convex oder Supabase verbunden, legt es auf Zuruf einen Eintrag an. „it's connected to my database via mCP and it knows exactly what to do and how to do“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 09:26)
- **Vom Meeting zum Angebot in einem Prompt:** Meeting-Notizen aus Granola lesen, Angebotsmail als Gmail-Entwurf, Stripe-Zahlungslink, Projekt in Notion. Mit fiktivem Prospect ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57)
- **Ads-Analyst für Wettbewerber:** Nur die URL der Meta Ads Library als Eingabe. Der Skill scrapt rund 220 Anzeigen, macht Screenshots der Landingpages und liefert je Anzeige eine visuelle und eine Copy-Analyse plus Master-Report ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 49:09)
- **Ideen-App aus Videotranskripten:** Die Demo-App lässt die KI aus Transkripten Geschäftsideen samt Marktgröße und Prognose ableiten, etwa „projected market size by 2028.“ Die Zahlen werden nicht geprüft ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 55:35)
- **Mail-Triage:** 1.700 Mails mit vier Schemafeldern in wenigen Sekunden klassifiziert ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 04:50, 06:25)
- **Lead-Score im Kontaktformular:** Grafikdesign-Agentur, Sofortbearbeitung ab 0,98, ohne Ergebniszahlen ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00)
- **Video-Clipping:** Wort-Transkript plus Bewertungskriterien, 17 Momente in etwa 3 Sekunden bewertet, Füllwörter ausgeschlossen. „scores 17 moments in around like three seconds.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 24:10)
- **Browser-Agent mit vielen Kleinentscheidungen:** Flug Zürich nach London in 7,1 Sekunden ausgewählt. Der Vergleich mit einer bis drei Minuten bei anderen Browser-Agents ist geschätzt ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 25:40)

### Startup-Ideen aus den Folgen (ungeprüft)
- **MCP-Verzeichnis mit Ein-Klick-Bereitstellung:** Eine Seite listet MCP Server mit ihrem GitHub-Code. Der Nutzer klickt auf „install“ oder „deploy“ und bekommt eine eigene URL für seinen MCP Client. Markttest, Wettbewerb und Geschäftsmodell fehlen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 16:41)
- **Vorab gebaute Websites per Cold Email:** Agenten bauen Websites für Kleinunternehmen vorab und bieten sie für 250 Dollar an. „Hey, I built you this website, so-and-so business. Do you want it? It's going to cost $250.“ Wirksamkeit und Zulässigkeit sind nicht belegt ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:17)
- **Klassifikator vor einer teuren Queue:** etwa ein Vermittler lokaler Dienstleistungen, der Anfragen sofort dem passenden Anbieter zuordnet. Konzept ohne gezeigten Fall ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 21:10)

## Formulierungen und Formate

- **Format „Clearly Explained“:** Isenberg lässt sich ein technisches Thema von einem Gast erklären, zieht selbst die Analogie (HTTPS, SMTP) und schließt mit der Frage nach Geschäftschancen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54, 16:41, 19:21). Dasselbe Titelformat trägt die Folge zu Agenten und Skills ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md))
- **Format „Full Course“:** Ein Gast zeigt sein echtes Setup live am Bildschirm, mit Demos bis zum fertigen Ergebnis ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md))
- **Format Live-Build mit Zeitversprechen:** Ein Gast baut eine App vor der Kamera, der Titel nennt die Dauer („in 67 mins“) und die Werkzeuge. Die Zeitangabe gilt nur mit fertigem Template ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 08:35)
- **Format „How I use …“:** Isenberg führt die eigene Methode am Bildschirm vor, an einer Beispielnische (Hundebesitzer) und schließt mit dem eigenen Erfolgsbeispiel ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 20:36)
- **Format Tool-Launch („… is HERE. How to use it“):** Ein neues Modell wird mit mehreren Demos vorgestellt, an einem Grenzfall getestet (Bitcoin) und mit Zugangsweg und Gründermuster abgeschlossen. Der Zugangsweg ist zugleich Werbung für Vercel ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 21:10, 23:00, 26:30)
- **Begriffe:** „Why now“, „unfair advantage“, „One-Pager“ ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:11, 02:55, 16:08), „AI Traffic Cop“, „expensive queue“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 19:40, 21:10)
- „the mistake people make here is they focus just on these big subreddits“ (Isenberg, [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:11)
- „do I have an unfair advantage in that subreddit“ (Isenberg, [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:55)
- „these are people screaming they want these products to exist“ (Isenberg, [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 10:34)
- „it's not about just building a product anymore you need to attract an audience“ (Isenberg, [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 01:10)
- „more often than not you'll notice that the marketing is bad and they're not doing anything on social“ (Isenberg, [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 09:20)
- „I wire framed it up put it up in a few hours on framer and just started posting about it“ (Isenberg, [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16)
- „every time there's been a popularized protocol for example https or SMTP there's been a lot of big businesses that were created on top of it“ (Isenberg, [MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54)
- „understanding how this works means you'll understand how the next thing works and when that becomes finalized you hit the ground running“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 19:33)
- „you have to make sure the llm doesn't hallucinate or do something stupid“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 06:26)
- „Don't tell the model things that should already be known“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 32:15)
- „This is the worst thing you can do.“ über Skills ohne vorherigen Durchlauf ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 08:30)
- „the closer you get to 99, 100%... it starts to get dumb“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 31:15)
- „downloading some random person's skills is an easy way to attack somebody.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 12:40)
- „it starts with one agent and you building up the skills.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 14:35)
- „I like to think of security as in just like scoping what they have access to.“ (Remy, [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 08:59)
- „you start to fit like a week in a day and then seven weeks in a week.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 38:44)
- „Error messages are good. Blank screens are bad.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 44:20)
- „hit save all instead of accept all. Accept all is not reversible.“ ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 34:40)
- „by the second or third try, like you will will your way to a working app.“ (Riley, [App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 37:35)
- „find a business with an expensive queue of incoming information and then just put Jev at the front of that queue.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 21:10)
- „Jev is basically this ... AI traffic cop.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 19:40)
- „I would not put this model in front of like your stock portfolio“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 23:00)
- „There's no internal reasoning or anything like that.“ ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 13:00)

## Zahlen, die sie nennt

| Zahl | Aussage | Beleg | Quelle |
|---|---|---|---|
| 10.000 bis 100.000 Mitglieder | Größenfilter für wachsende Subreddits bei der Ideensuche. | Anekdote | [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 02:11 |
| 25 Creators | Perplexity listet die 25 beliebtesten YouTube-Creators der Nische. | eigene Daten | [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 14:42 |
| 20 bis 25 Videos | So viele Top-Videos wertet Isenberg für den One-Pager über Kommentare aus. | Anekdote | [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:08 |
| wenige Stunden | Wireframe und Website von designscientist.com in Framer. | Anekdote | [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16 |
| siebenstellig, mehrere Multi-Millionen | designscientist.com sei ein Seven-Figure-Business aus dieser Methode, Reddit-Ideen hätten mehrere Multi-Millionen-Unternehmen gebracht. Umsatz, Zeitraum und Anteil der Recherche am Erfolg fehlen. | Behauptung ohne Beleg | [Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 20:36 |
| 2 Stunden | Ross Mike sagt, eine Chatbot-Oberfläche mit Tools lasse sich in zwei Stunden bauen. Schwer und teuer seien eine fehlerfreie Nutzererfahrung und das Begrenzen von Halluzinationen. Das sei bei Tempo ein Großteil der Arbeit. | Anekdote | [MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 18:25 |
| 7.000 Tokens | Eine claude.md mit 1.000 Zeilen kostet nach Schätzung des Sprechers rund 7.000 Tokens bei jedem Lauf. | Behauptung ohne Beleg | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 04:20 |
| 944 zu 53 Tokens | Vollständige SKILL.md gegenüber nur Name und Beschreibung, gemessen im OpenAI Tokenizer. Ersparnis bis zum Abruf rund 94 Prozent. | eigene Daten | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 30:40 |
| 20.000 Tokens | Ungefährer Startwert des Kontextfensters eines Coding-Agenten, abhängig von Modell und Werkzeug. | Behauptung ohne Beleg | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 06:45 |
| 70 und 80 Prozent | Bis etwa 70 Prozent Füllstand arbeiten, ab etwa 80 Prozent lässt die Leistung deutlich nach. | Behauptung ohne Beleg | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 31:15 |
| 5 Schleifen, 8 Datenquellen | Ein Report-Generator mit acht Datenquellen brauchte fünf Härtungsschleifen bis zum fehlerfreien Lauf. | Anekdote | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:45 |
| 1 plus 5 | Der Sprecher steuert einen Hauptagenten mit fünf Sub-Agenten. | Anekdote | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 14:35 |
| 2 Wochen | Einarbeitung in ein neues Agenten-Harness wie OpenClaw. „it took me two weeks.“ | Anekdote | [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 23:50 |
| 200 Zeilen | Remys Obergrenze für die Claude.md, nicht begründet. | Anekdote | [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 30:44 |
| 15 bis 30 Minuten | Wöchentliche Nacharbeit an einem Angebot, wenn Prozessdetails nicht in einem Skill stehen. | Anekdote | [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 40:51 |
| 220 Anzeigen, 3 bis 4 Stunden | Der Ads-Analyst-Skill wertet rund 220 Anzeigen aus. Remy schätzt den manuellen Aufwand auf 3 bis 4 Stunden, der Skill entstand aus etwa 2 Stunden Durchlauf. | eigene Daten, Zeiten geschätzt | [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 49:09 |
| 10 bis 20 mal, 7 mal, 1 bis 2 Stunden pro Tag | Produktivitätsgewinn laut Isenberg (10 bis 20 mal) und Remy (etwa 7 mal schneller), Zeitersparnis durch einen Executive-Assistant-Agenten. Ohne Messmethode oder Vergleichsgruppe. | Behauptung ohne Beleg | [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 38:44 |
| 250 Dollar | Preis für vorab gebaute Websites in der Cold-Email-Idee. | Behauptung ohne Beleg | [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:17 |
| 67 Minuten, 3 Stunden, 6 bis 7 Stunden | 67 Minuten für eine App nur mit fertigem Template. Ohne Vorlage kostet Anfänger allein das Setup bis zu 3 Stunden, eine vollständige App 6 bis 7 Stunden. | eigene Daten | [App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 08:35 |
| 10 bis 15 Stunden, 50 Tage | Übungszeit, bis man typische Fehler mit Claude systematisch behebt. Riley hatte 50 Tage vor der Aufnahme nie programmiert. | Anekdote | [App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 02:25 |
| 2. oder 3. Anlauf | Laut Riley kommen hartnäckige Einsteiger meist im zweiten oder dritten Versuch zu einer laufenden App. | Behauptung ohne Beleg | [App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 37:35 |
| 20 USD, 15 bis 20 USD, über 1.000 USD | Replit-Hosting ca. 20 USD, V0 15 bis 20 USD im Monat, Firebase bis zu einer nicht genannten Nutzerzahl kostenlos. Das eigene KI-Budget des Sprechers liegt über 1.000 USD im Monat. Preisstand zum Aufnahmezeitpunkt. | eigene Daten | [App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 26:55 |
| 1.700 Mails, 4,2 Mio. und 0,5 Mio. Tokens, 18 Cent | Mail-Triage in der Demo in wenigen Sekunden. Der Wortlaut lässt offen, ob 18 Cent gesamt oder pro Mail gelten. | eigene Daten, Bezug unklar | [Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 06:25 |
| 200 Millisekunden, 30 Sekunden | Latenz pro Abfrage unabhängig von der Schemagröße, gegenüber bis zu 30 Sekunden bei herkömmlichen LLMs. | eigene Daten | [Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 19:15 |
| 0,98 | Lead-Score, ab dem eine Agentur Kontaktanfragen sofort bearbeitet. Keine Zahlen zur Abschlussquote. | Kundenfall | [Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00 |
| 17 Momente, 3 Sekunden, 1,1 Mio. Tokens | Video-Clipping: Bewertung der Momente aus einem Wort-Transkript. | eigene Daten | [Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 24:10 |
| 7,1 Sekunden, 1 bis 3 Minuten | Flugauswahl Zürich nach London per Browser-Agent. Der Vergleichswert für andere Agents ist geschätzt, nicht gemessen. | eigene Daten, Vergleich geschätzt | [Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 25:40 |
| 5 USD, 10 USD, 1/1.000 Cent | 5 USD Startguthaben reichten für zwei Tage intensiver Tests, 10 USD sollen im Testbetrieb etwa drei Monate halten. Die genannten 1/1.000 Cent pro Abfrage passen nicht zur Mail-Demo mit rund 0,01 Cent pro Mail. | eigene Daten, widersprüchlich | [Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 16:30 |

## Wo Vorsicht geboten ist

- **Die meisten Aussagen stammen nicht von Isenberg.** Die MCP-Erklärungen kommen vom Gast Ross Mike, der Kurs überwiegend von Remy, die App-Folge von Riley oder einem nicht immer namentlich zugeordneten Sprecher. In der Folge zu Agenten und Skills und in der Jev-Folge sind die Sprecher in den Learnings nicht namentlich zugeordnet. Isenberg selbst sicher zuzuordnen sind die HTTPS/SMTP-Analogie (15:54 in der MCP-Folge), die Angabe von 10 bis 20 mal Produktivitätsgewinn (38:44 im Kurs) und die gesamte Reddit-Methode ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md)).
- **Eigenes Erfolgsbeispiel ohne Zahlen.** designscientist.com ist Isenbergs eigenes Unternehmen. Seven-Figure-Business und mehrere Multi-Millionen-Unternehmen sind unbelegt, Umsatz, Zeitraum und der Anteil der Reddit-Recherche am Erfolg fehlen. Wie aus dem Posten Kunden wurden, bleibt offen ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 16:16, 20:36).
- **„Validiert“ heißt nur: Bedarf wird geäußert.** Zahlungsbereitschaft, Marktgröße und Wettbewerb prüft die Reddit-Methode nicht, Schwellenwerte für Upvotes oder Kommentare nennt sie nicht ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 10:34). Die These vom schwachen Marketing etablierter Anbieter wird ohne gezeigte Wettbewerbsrecherche aufgestellt ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 09:20).
- **Gummy Search:** Eine mögliche Partnerschaft wird nicht offengelegt, der Preis des Bezahlplans nicht genannt. Verfügbarkeit des Tools vor Nutzung prüfen. Die KI-Zusammenfassungen sind laut Isenberg selbst nicht immer genau ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 06:40, 11:05).
- **Reddit-Methode ist B2C und Solo gezeigt.** Die Demo nutzt Hundebesitzer, die Zielgruppe muss auf Reddit aktiv sein. Für B2B-Käufer und die These „Produkt plus Publikum“ im B2B-Vertrieb gibt es keinen Beleg ([Reddit-Ideen](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), 01:10, 18:48).
- **Eigeninteresse des Gasts:** Ross Mike arbeitet bei Tempo, und Tempo wird als Beispiel für einen MCP Client genannt ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:07, 18:25). Riley stützt Aussagen auf eine eigene Community, deren Angebot nicht offengelegt ist ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 37:35).
- **Jev-Folge ist eine Produktvorstellung mit Werbung.** Die Folge bewirbt Vercel als Zugangsweg, eine Bezahlung wird nicht offengelegt. Ob die Sprecher zum Anbieter von Jev gehören, ist unklar. Fast alle Zahlen stammen aus eigenen Demos der Sprecher, ein unabhängiger Test fehlt ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 06:25, 26:30).
- **Kein Vergleich mit Alternativen.** Die Jev-Folge vergleicht weder mit Open-Weight-Klassifikatoren noch mit kleinen feinjustierten Modellen und legt keine Architektur offen. Ob Jev besser klassifiziert als lokal betreibbare Alternativen, bleibt unbelegt ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md)). Der Vergleich mit GPT-6 Astra beruht auf einem einzigen Bitcoin-Test ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 23:00).
- **Kostenangaben zu Jev widersprechen sich.** 18 Cent für 1.700 Mails ergeben rund 0,01 Cent pro Mail, genannt werden 1/1.000 Cent pro Abfrage. *Einordnung: Bei 18 Cent pro einzelner Mail kämen für die Demo rund 306 USD zusammen, was nicht zu 5 USD Startguthaben für zwei Testtage passt. Gesamtkosten sind wahrscheinlicher, gesichert ist das nicht.* Eigene Kosten vorab messen ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 06:25, 16:30).
- **Klassifikator ohne Begründung.** Jev liefert nur das Ergebnis. Bei kundenwirksamen oder regulierten Entscheidungen sind Stichproben und menschliche Prüfung nötig. Für Entscheidungen, die externes Wissen oder Abwägung brauchen, taugt das Modell laut eigenem Test nicht ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 13:00, 23:00).
- **Lead-Score ohne Ergebnis.** Die 0,98-Schwelle der Agentur kommt ohne Zahlen zu Abschlussquote oder übersehenen Leads. Rückwirkende Lead-Suche und Ticket-Routing sind nur als Idee genannt, nicht gezeigt ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 17:00, 18:05, 18:45).
- **Kaum Belege.** Fast alles sind Behauptungen oder Anekdoten aus dem eigenen Setup. Echte Messung gibt es nur beim Tokenvergleich (944 zu 53) und bei den gezeigten Demos, darunter der Live-Build der App, die Reddit-Recherche am Bildschirm und die Jev-Demos.
- **Titelversprechen gilt nur unter Bedingungen.** Die 67 Minuten setzen ein fertiges Template voraus. Ohne Vorlage nennt der Sprecher selbst 6 bis 7 Stunden ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 08:35).
- **Produktivitätszahlen sind Selbstaussagen.** 10 bis 20 mal, 7 mal und 1 bis 2 Stunden pro Tag haben weder Messmethode noch Vergleichsgruppe und beziehen sich auf Solo-Gründer und Kleinstfirmen, nicht auf größere Organisationen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 38:44). Dasselbe gilt für Rileys 10 bis 15 Stunden Übung und den „zweiten oder dritten Anlauf“.
- **Demos sind vorbereitet.** Der Angebots-Workflow läuft mit einem fiktiven Prospect, nicht mit einem echten Kunden ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57).
- **Prototyp ist nicht Produkt.** Der Stack aus V0, Cursor, Replit und Firebase ist für Prototypen von Einzelpersonen gedacht. Wartung, Tests, Sicherheit und Skalierung behandelt die Folge nicht ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 25:50).
- **Agenten erfinden Fakten.** Auch mit Recherche-Tool und Selbstprüfung per Screenshot enthielt eine vom Agenten gebaute Website falsche E-Mail-Adresse und falschen Wohnort. „That's not my email address and I don't live in South Canada anymore.“ Vor Veröffentlichung manuell prüfen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 12:39). Ebenso leitet die Demo-App Marktgrößen und Prognosen aus Videotranskripten ab, ohne sie zu prüfen. Solche Werte brauchen eine Gegenrecherche, bevor sie in Entscheidungen einfließen ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 55:35). Siehe Kernidee 17.
- **Anbieterwechsel ist keine Fehlerbehebung.** Das Umstellen von OpenAI auf Anthropic umgeht das Problem, ohne die Ursache zu klären ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 51:10).
- **Werkzeughinweise veralten.** Der Rat zu „Save all“ statt „Accept all“ bezieht sich auf die im Video gezeigte Cursor-Version und ist nicht unabhängig geprüft. Die genannten Preise für Replit, V0 und Firebase sind Preisstand zum Aufnahmezeitpunkt ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 34:40, 26:55). Jev war zum Aufnahmezeitpunkt direkt nur per Warteliste verfügbar ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 26:30).
- **Wrapper-Rechnung unvollständig.** Die Faustregel Abo-Einnahmen größer als API-Kosten lässt Hosting, Zahlungsgebühren, Akquisekosten und Preisänderungen der Modellanbieter außen vor ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 36:00).
- **Sicherheit nur angerissen.** Eigene Mailadresse und begrenzte Rechte werden empfohlen. Prompt Injection, konkrete MCP-Berechtigungen und die Absicherung von Schreibzugriff auf produktive Datenbanken behandeln die Folgen nicht ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 06:26; [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 07:35; [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 08:59).
- **DSGVO fehlt.** Das gezeigte Setup leitet E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten über US-Cloud-Modelle. Auftragsverarbeitung sowie lokale oder Open-Weight-Alternativen werden nicht angesprochen und sind vor einem Nachbau in der EU zu klären ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)). Gleiches gilt für Login- und Nutzerdaten in Firebase beim Prototyp-Stack ([App in 67 Minuten](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), 25:50) und für komplette Mailobjekte und Kontaktanfragen, die bei Jev über US-Anbieter wie Vercel laufen ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 04:50, 26:30).
- **Cold-Email-Idee rechtlich heikel.** Massen-Kaltansprache per E-Mail ist in der EU stark reguliert. Antwortquoten und Wirksamkeit sind nicht belegt ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:17). Dasselbe gilt für die erneute Ansprache von Altkunden aus rückwirkend durchsuchten Postfächern ([Jev](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), 18:05).
- **Richtwerte ohne Begründung.** 200 Zeilen, 70 und 80 Prozent sowie 20.000 Tokens hängen von Modell und Werkzeug ab und werden nicht hergeleitet. Ebenso die Spanne von 10.000 bis 100.000 Mitgliedern bei Subreddits und die Lead-Schwelle von 0,98.
- **Harness-These ohne Benchmark.** Dass Harness und Werkzeuge bei ähnlichen Modellen die Qualität bestimmen, wird ohne Vergleichsmessung behauptet ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 27:10).
- **Sponsorfilter nicht auf B2B geprüft.** Die Prüfregel stammt aus dem Creator-Alltag. Für B2B-Lead-Qualifizierung ist sie nicht getestet ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 09:30).
- **Früher Stand von MCP:** Die umständliche Einrichtung (13:57) und die Einschätzung, es gebe keine großen Geschäftschancen (19:21), beschreiben die Lage zum Zeitpunkt der Aufnahme. Den aktuellen Stand vor der Anwendung prüfen.
- **Standardrisiko:** Selbst der Sprecher hält MCP nicht für gesetzt ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 17:43). Wer darauf baut, trägt dieses Risiko.
- **Analogie statt Beleg:** Der Vergleich mit HTTPS und SMTP zeigt nicht, dass MCP eine ähnliche Rolle einnehmen wird ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54).
- **Ungeprüfte Startup-Ideen:** Für das MCP-Verzeichnis, die Website-Idee und das Klassifikator-Gründermuster gibt es keinen Markttest, keine Wettbewerbsanalyse und kein durchgerechnetes Geschäftsmodell.
- **Zeitliche Reihenfolge unsicher:** Die Daten der Quellen sind Erfassungsdaten. Die Entwicklungen bei MCP (Kernidee 11), beim Umgang mit Fehlern (Kernidee 12) und der von Isenberg angedeutete Wandel zu „Produkt plus Publikum“ (Kernidee 16) sind deshalb als Tendenz zu lesen, nicht als gesicherter Meinungswandel.

## Alle Quellen

- [Model Context Protocol (MCP), clearly explained (why it matters)](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), erfasst am 2026-11-09, mit Gast Ross Mike. Learnings L-20261109-036 bis L-20261109-051
- [How AI agents & Claude skills work (Clearly Explained)](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), erfasst am 2026-11-13, Sprecher in den Learnings nicht namentlich genannt. Learnings L-20261113-087 bis L-20261113-103
- [Building AI Agents that actually work (Full Course)](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), erfasst am 2026-11-13, mit Gast Remy. Learnings L-20261113-104 bis L-20261113-122
- [I can't believe we coded an app with AI in 67 mins (V0, Cursor AI, Replit, Claude AI)](../quellen/2026/11/2026-11-14-i-can-t-believe-we-coded-an-app-with-ai-in-67-mins-v0-cursor.md), erfasst am 2026-11-14, mit Gast Riley. Learnings L-20261114-063 bis L-20261114-079
- [How I use Reddit and AI to find winning startup ideas](../quellen/2026/11/2026-11-14-how-i-use-reddit-and-ai-to-find-winning-startup-ideas.md), erfasst am 2026-11-14, Isenberg als Hauptsprecher. Learnings L-20261114-246 bis L-20261114-260
- [Jev is HERE. How to use it](../quellen/2026/11/2026-11-15-jev-is-here-how-to-use-it.md), erfasst am 2026-11-15, Sprecher in den Learnings nicht namentlich genannt, mit Werbung für Vercel. Learnings L-20261115-098 bis L-20261115-114
