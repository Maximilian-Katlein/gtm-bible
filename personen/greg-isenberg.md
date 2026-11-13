# Greg Isenberg

Greg Isenberg ist Host eines Startup-Podcasts, in dem technische Gäste neue KI-Bausteine wie MCP, Agenten und Skills für Gründer einordnen. Zuhören lohnt sich, weil daraus Geschäftschancen und nachbaubare Abläufe für Solo-Gründer und kleine Teams werden.

Stand: 2026-11-13 · 3 Quellen

Verkauft: In den erfassten Quellen nicht benannt. Der Gast Ross Mike arbeitet bei Tempo. Tempo kommt in der MCP-Folge als Beispiel für einen MCP Client vor ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:07, 18:25). Der Gast Remy betreibt einen Newsletter mit eigenem Team und zeigt im Kurs sein persönliches Agenten-Setup ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 53:14).

## Kernideen

> Drei Quellen, alle aus Isenbergs Kanal. Ein Großteil der Aussagen stammt von Gästen (Ross Mike, Remy) oder einem in den Learnings nicht namentlich genannten Sprecher, nicht von Isenberg selbst. Wiederholt heißt hier: Die Idee taucht in mehreren Folgen des Kanals auf. Siehe „Wo Vorsicht geboten ist“.

### 1. Kontext ist knapp: In die Dauerdatei gehört nur, was der Agent nicht selbst wissen kann
*Wiederholt in 2 Quellen.*
- In agent.md oder claude.md gehört nur proprietäres Wissen, das in jedem Dialogschritt gebraucht wird. Den Tech-Stack muss man nicht nennen, weil der Agent die Codebasis selbst liest. „telling Claude Code this code base uses React, I don't need to because it has the codebase in context.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 02:05)
- Selbstverständlichkeiten verschwenden Kontext. Nur Abweichungen vom Standard notieren, etwa eine besondere Währung. „Don't tell the model things that should already be known“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 32:15)
- Eine 1.000 Zeilen lange claude.md kostet nach Schätzung des Sprechers rund 7.000 Tokens bei jedem Lauf ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 04:20)
- Remy nennt als Best Practice höchstens etwa 200 Zeilen für die Claude.md ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 30:44)
- Code ist selbst Kontext: Ein solides Template für Web oder Mobile gibt dem Agenten ein Fundament. Der Sprecher erwartet eine Renaissance von Templates ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 20:10)
- Das Kontextfenster füllt sich ohnehin schnell: Es startet laut Sprecher bei etwa 20.000 Tokens, und ab etwa 80 Prozent Füllstand lässt die Leistung deutlich nach ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 06:45, 31:15)

### 2. Skills entstehen aus einem gelungenen Durchlauf, nicht am Reißbrett
*Wiederholt in 2 Quellen.*
- Erst den Ablauf im Dialog mit dem Agenten Schritt für Schritt durchspielen, dann den Agenten den Verlauf prüfen und daraus die skill.md schreiben lassen ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 11:40)
- Den Skill sofort zu schreiben, nennt der Sprecher den größten Fehler. „and then they'll jump to create the skill right away. This is the worst thing you can do.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 08:30)
- Remy beschreibt denselben Weg: Aufgabe einmal manuell erledigen, dann „Hey, create a skill for what we just did.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 44:25). Sein Ads-Analyst-Skill entstand aus etwa zwei Stunden Durchlauf ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 49:09)
- Folgerung für fremde Skills: Ihnen fehlt der Kontext eines eigenen erfolgreichen Laufs ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 12:40)

### 3. Prozesswissen gehört in Skills, die erst bei Bedarf geladen werden
*Wiederholt in 2 Quellen.*
- Umfangreiches Wissen aus der claude.md „probably should be a skill“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 04:20)
- Progressive Disclosure: Bis zum Abruf liegen nur Name und Beschreibung im Kontext. Gemessen 53 statt 944 Tokens für einen Skill ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 30:40)
- Aufbau, Farben und Preisposition eines Angebots gehören in einen Skill, nicht in die memory.md. Sonst iteriert man jede Woche erneut 15 bis 30 Minuten ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 40:51)
- Abgrenzung: Die Dauerdatei hält, wer man ist und wie man arbeitet (Rolle, Geschäftsmodell, ICP, Präferenzen). Skills halten, wie eine konkrete Aufgabe erledigt wird ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 20:26)

### 4. Sicherheit heißt vor allem: Zugriff begrenzen
*Wiederholt in 3 Quellen.*
- Ein autonomer E-Mail-Agent bekommt eine eigene Adresse statt Zugriff auf das Hauptpostfach. „I haven't given it access to my email, because there's like attack vectors and I've been hacked before“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 07:35)
- Remy: Agenten mit Budget- oder Systemzugriff, etwa ein Meta-Ads-Agent, bekommen nur so viele Rechte, dass der Schaden bei Kompromittierung begrenzt bleibt, zum Beispiel Read-only. „I like to think of security as in just like scoping what they have access to.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 08:59)
- Fremde Skills von Marktplätzen sind ein einfacher Angriffsweg ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 12:40)
- Schon in der MCP-Folge: „you have to make sure the llm doesn't hallucinate or do something stupid“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 06:26)

### 5. Der Wert entsteht in der Schicht um das Modell
*Wiederholt in 3 Quellen.*
- Ein Sprachmodell allein sagt nur Text voraus. „llms by themselves are incapable of doing anything meaningful“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 02:39)
- Eine Chatbot-Oberfläche mit Tools sei in zwei Stunden gebaut. Schwer und teuer seien fehlerfreie Nutzererfahrung und begrenzte Halluzinationen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 18:25)
- Bei ähnlichen Basismodellen bestimmen Harness und Werkzeuge die Ausgabequalität mit, etwa Cursor, Claude Code oder Codex. „the harness... is going to matter even more.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 27:10)
- Für die Einarbeitung in ein neues Harness wie OpenClaw sollte man rund zwei Wochen einplanen ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 23:50)

### 6. Agenten brauchen explizite Kriterien und einen messbaren Endpunkt
*Wiederholt in 2 Quellen.*
- Ein Agent beendet seine Schleife aus Beobachten, Entscheiden und Handeln erst, wenn er die Aufgabe für erledigt hält. Messbare Vorgaben legen das Ende fest. „you might say compile 10 sources, and then create a report as a PowerPoint.“ ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 05:23)
- Ohne feste Kriterien stufte ein E-Mail-Agent jede Sponsoranfrage als seriös ein. Erst eine Prüfregel machte das Filtern brauchbar. „If two of these don't exist are not in good standing, automatic rejection.“ ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 09:30)

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

### 11. Erst beobachten, dann handeln, solange der Standard nicht fertig ist
- Nicht-technischen Gründern rät der Sprecher, zu beobachten, welche Plattformen MCP ausbauen. Handeln sollen sie erst, wenn der Standard final ist und die Anbieter ihre Server gebaut haben. „I don't see any crazy business opportunities right now for a non-technical person even for a technical person“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 19:21)
- Der Grund: Die Einrichtung war zum Zeitpunkt der Aufnahme umständlich und für nicht-technische Teams nicht selbst machbar ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 13:57)
- **Entwicklung:** In der MCP-Folge (erfasst 2026-11-09) lautete der Rat „abwarten“. Im Kurs (erfasst 2026-11-13) richtet Remy MCP-Anbindungen für einen Solo-Workflow vor der Kamera ein, und Isenberg spricht von 10- bis 20-fachem Produktivitätsgewinn ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57, 38:44). Die Daten sind Erfassungsdaten, nicht Veröffentlichungsdaten. Die Reihenfolge der Aufnahmen ist daher nicht gesichert.

## Methoden und Abläufe

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

### Prüfregel statt Bauchgefühl beim Filtern
Sponsoranfragen werden auf Twitter, YouTube, Trustpilot und Finanzierung geprüft. Fehlen zwei Signale oder sind schlecht, folgt automatische Ablehnung und ein Eintrag „no contact“ im Google Sheet ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 09:30). Übertragbar auf Lead-Qualifizierung, dort aber nicht geprüft.

### Beispiele aus den Folgen
- **Datenbank per MCP:** Ist ein Modell mit Convex oder Supabase verbunden, legt es auf Zuruf einen Eintrag an. „it's connected to my database via mCP and it knows exactly what to do and how to do“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 09:26)
- **Vom Meeting zum Angebot in einem Prompt:** Meeting-Notizen aus Granola lesen, Angebotsmail als Gmail-Entwurf, Stripe-Zahlungslink, Projekt in Notion. Mit fiktivem Prospect ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57)
- **Ads-Analyst für Wettbewerber:** Nur die URL der Meta Ads Library als Eingabe. Der Skill scrapt rund 220 Anzeigen, macht Screenshots der Landingpages und liefert je Anzeige eine visuelle und eine Copy-Analyse plus Master-Report ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 49:09)

### Startup-Ideen aus den Folgen (ungeprüft)
- **MCP-Verzeichnis mit Ein-Klick-Bereitstellung:** Eine Seite listet MCP Server mit ihrem GitHub-Code. Der Nutzer klickt auf „install“ oder „deploy“ und bekommt eine eigene URL für seinen MCP Client. Markttest, Wettbewerb und Geschäftsmodell fehlen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 16:41)
- **Vorab gebaute Websites per Cold Email:** Agenten bauen Websites für Kleinunternehmen vorab und bieten sie für 250 Dollar an. „Hey, I built you this website, so-and-so business. Do you want it? It's going to cost $250.“ Wirksamkeit und Zulässigkeit sind nicht belegt ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:17)

## Formulierungen und Formate

- **Format „Clearly Explained“:** Isenberg lässt sich ein technisches Thema von einem Gast erklären, zieht selbst die Analogie (HTTPS, SMTP) und schließt mit der Frage nach Geschäftschancen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54, 16:41, 19:21). Dasselbe Titelformat trägt die Folge zu Agenten und Skills ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md))
- **Format „Full Course“:** Ein Gast zeigt sein echtes Setup live am Bildschirm, mit Demos bis zum fertigen Ergebnis ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md))
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

## Zahlen, die sie nennt

| Zahl | Aussage | Beleg | Quelle |
|---|---|---|---|
| 2 Stunden | Ross Mike sagt, er könne eine Chatbot-Oberfläche mit Tools in zwei Stunden bauen. Schwer und teuer seien eine fehlerfreie Nutzererfahrung und das Begrenzen von Halluzinationen. Das sei bei Tempo ein Großteil der Arbeit. | Anekdote | [MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 18:25 |
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

## Wo Vorsicht geboten ist

- **Die meisten Aussagen stammen nicht von Isenberg.** Die MCP-Erklärungen kommen vom Gast Ross Mike, der Kurs überwiegend von Remy. In der Folge zu Agenten und Skills ist der Sprecher in den Learnings nicht namentlich zugeordnet. Isenberg selbst sicher zuzuordnen sind die HTTPS/SMTP-Analogie (15:54 in der MCP-Folge) und die Angabe von 10 bis 20 mal Produktivitätsgewinn (38:44 im Kurs).
- **Eigeninteresse des Gasts:** Ross Mike arbeitet bei Tempo, und Tempo wird als Beispiel für einen MCP Client genannt ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:07, 18:25).
- **Kaum Belege.** Fast alles sind Behauptungen oder Anekdoten aus dem eigenen Setup. Echte Messung gibt es nur beim Tokenvergleich (944 zu 53) und bei den gezeigten Demos.
- **Produktivitätszahlen sind Selbstaussagen.** 10 bis 20 mal, 7 mal und 1 bis 2 Stunden pro Tag haben weder Messmethode noch Vergleichsgruppe und beziehen sich auf Solo-Gründer und Kleinstfirmen, nicht auf größere Organisationen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 38:44).
- **Demos sind vorbereitet.** Der Angebots-Workflow läuft mit einem fiktiven Prospect, nicht mit einem echten Kunden ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 36:57).
- **Agenten erfinden Fakten.** Auch mit Recherche-Tool und Selbstprüfung per Screenshot enthielt eine vom Agenten gebaute Website falsche E-Mail-Adresse und falschen Wohnort. „That's not my email address and I don't live in South Canada anymore.“ Vor Veröffentlichung manuell prüfen ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 12:39).
- **Sicherheit nur angerissen.** Eigene Mailadresse und begrenzte Rechte werden empfohlen. Prompt Injection, konkrete MCP-Berechtigungen und die Absicherung von Schreibzugriff auf produktive Datenbanken behandeln die Folgen nicht ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 06:26; [AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 07:35; [AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 08:59).
- **DSGVO fehlt.** Das gezeigte Setup leitet E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten über US-Cloud-Modelle. Auftragsverarbeitung sowie lokale oder Open-Weight-Alternativen werden nicht angesprochen und sind vor einem Nachbau in der EU zu klären ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)).
- **Cold-Email-Idee rechtlich heikel.** Massen-Kaltansprache per E-Mail ist in der EU stark reguliert. Antwortquoten und Wirksamkeit sind nicht belegt ([AI Agents Full Course](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), 14:17).
- **Richtwerte ohne Begründung.** 200 Zeilen, 70 und 80 Prozent sowie 20.000 Tokens hängen von Modell und Werkzeug ab und werden nicht hergeleitet.
- **Harness-These ohne Benchmark.** Dass Harness und Werkzeuge bei ähnlichen Modellen die Qualität bestimmen, wird ohne Vergleichsmessung behauptet ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 27:10).
- **Sponsorfilter nicht auf B2B geprüft.** Die Prüfregel stammt aus dem Creator-Alltag. Für B2B-Lead-Qualifizierung ist sie nicht getestet ([AI agents & Claude skills](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), 09:30).
- **Früher Stand von MCP:** Die umständliche Einrichtung (13:57) und die Einschätzung, es gebe keine großen Geschäftschancen (19:21), beschreiben die Lage zum Zeitpunkt der Aufnahme. Den aktuellen Stand vor der Anwendung prüfen.
- **Standardrisiko:** Selbst der Sprecher hält MCP nicht für gesetzt ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 17:43). Wer darauf baut, trägt dieses Risiko.
- **Analogie statt Beleg:** Der Vergleich mit HTTPS und SMTP zeigt nicht, dass MCP eine ähnliche Rolle einnehmen wird ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54).
- **Ungeprüfte Startup-Ideen:** Für das MCP-Verzeichnis und die Website-Idee gibt es keinen Markttest, keine Wettbewerbsanalyse und kein durchgerechnetes Geschäftsmodell.
- **Zeitliche Reihenfolge unsicher:** Die Daten der Quellen sind Erfassungsdaten. Die Entwicklung bei MCP (Kernidee 11) ist deshalb als Tendenz zu lesen, nicht als gesicherter Meinungswandel.

## Alle Quellen

- [Model Context Protocol (MCP), clearly explained (why it matters)](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), erfasst am 2026-11-09, mit Gast Ross Mike. Learnings L-20261109-036 bis L-20261109-051
- [How AI agents & Claude skills work (Clearly Explained)](../quellen/2026/11/2026-11-13-how-ai-agents-claude-skills-work-clearly-explained.md), erfasst am 2026-11-13, Sprecher in den Learnings nicht namentlich genannt. Learnings L-20261113-087 bis L-20261113-103
- [Building AI Agents that actually work (Full Course)](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md), erfasst am 2026-11-13, mit Gast Remy. Learnings L-20261113-104 bis L-20261113-122
