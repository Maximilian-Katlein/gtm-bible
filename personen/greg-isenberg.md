# Greg Isenberg

Greg Isenberg ist Host eines Startup-Podcasts. Man hört ihm zu, weil er mit technischen Gästen neue KI-Bausteine wie MCP für Gründer einordnet und daraus Geschäftschancen ableitet.

Stand: 2026-11-09 · 1 Quelle

Verkauft: In den bisher erfassten Quellen nicht benannt. Der Gast Ross Mike arbeitet bei Tempo. Tempo kommt in der Folge als Beispiel für einen MCP Client vor ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:07, 18:25).

## Kernideen

> Bisher gibt es nur eine Quelle. Ob Isenberg diese Ideen wiederholt, ist noch nicht belegt. Ein Großteil der Aussagen stammt vom Gast Ross Mike und nicht von Isenberg selbst (siehe „Wo Vorsicht geboten ist“).

### 1. MCP ist ein Standard und kein technischer Durchbruch. Sein Wert hängt an der Verbreitung.
- MCP legt fest, wie Sprachmodelle mit externen Diensten sprechen. Nützlich wird es erst, wenn viele Anbieter mitmachen. „from a technological perspective all they did was create a standard“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 12:51)
- Gesetzt ist der Standard nicht: Anthropic könnte ihn ändern, oder ein anderer Anbieter bringt einen eigenen. „I don't know if mCP has fully won I think it needs to be challenged“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 17:43)
- Das Wissen lässt sich auf den nächsten Standard übertragen. Wer das Prinzip verstanden hat, kann sofort loslegen, sobald ein Standard final ist, auch wenn es am Ende nicht MCP wird ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 19:33)
- Isenberg vergleicht MCP mit HTTPS und SMTP: Auf verbreiteten Protokollen seien große Unternehmen entstanden ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54)

### 2. Die Integrationsarbeit wandert vom KI-Produkt zum Dienstanbieter
- Den MCP Server baut der Anbieter des Dienstes. Eine Datenbankfirma, die von KI-Clients genutzt werden will, muss ihn also selbst liefern. „the mCP server is now in the hands of the service provider“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 11:59)
- GTM-Folgerung: Wer wachsen und Partner oder Entwickler anbinden will, muss seine Schnittstelle in einer Form anbieten, die für diese Sinn ergibt. Für Sprachmodelle ist diese Form laut Sprecher MCP ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 13:06)

### 3. Einzeln verdrahtete Tools skalieren nicht
- Jeder Anbieter baut seine API anders. Das bedeutet viel Handarbeit, Planung Schritt für Schritt und viele Randfälle, an denen die Kette scheitert ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 09:38)
- Eine feste Kette wie „Slack-Nachricht lesen und als SMS weiterleiten“ bricht, sobald einer der Dienste seine API ändert. Je mehr Dienste beteiligt sind, desto höher der Wartungsaufwand ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 10:18)

### 4. Erst beobachten, dann handeln, solange der Standard nicht fertig ist
- Nicht-technischen Gründern rät der Sprecher, zu beobachten, welche Plattformen MCP ausbauen. Handeln sollen sie erst, wenn der Standard final ist und die Anbieter ihre Server gebaut haben. „I don't see any crazy business opportunities right now for a non-technical person even for a technical person“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 19:21)
- Der Grund: Die Einrichtung war zum Zeitpunkt der Aufnahme umständlich und für nicht-technische Teams nicht selbst machbar ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 13:57)

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

### Beispiel: Datenbank per MCP ansteuern
Ist ein Modell per MCP mit Convex oder Supabase verbunden, legt es auf Zuruf einen neuen Eintrag an und weiß selbst, wie das geht. „it's connected to my database via mCP and it knows exactly what to do and how to do“ ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 09:26)

### Startup-Idee für technische Gründer: MCP-Verzeichnis mit Ein-Klick-Bereitstellung
Eine Seite listet MCP Server mit ihrem GitHub-Code. Der Nutzer klickt auf „install“ oder „deploy“ und bekommt eine eigene URL für seinen MCP Client. Markttest, Wettbewerb und Geschäftsmodell fehlen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 16:41)

## Formulierungen und Formate

- **Format:** Isenberg lässt sich ein technisches Thema von einem Gast erklären, zieht selbst die Analogie (HTTPS, SMTP) und schließt mit der Frage, welche Geschäftschancen daraus entstehen ([MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 15:54, 16:41, 19:21)
- „every time there's been a popularized protocol for example https or SMTP there's been a lot of big businesses that were created on top of it“ (Isenberg, 15:54)
- „understanding how this works means you'll understand how the next thing works and when that becomes finalized you hit the ground running“ (19:33)
- „you have to make sure the llm doesn't hallucinate or do something stupid“ (06:26)

## Zahlen, die sie nennt

| Zahl | Aussage | Beleg | Quelle |
|---|---|---|---|
| 2 Stunden | Ross Mike sagt, er könne eine Chatbot-Oberfläche mit Tools in zwei Stunden bauen. Schwer und teuer seien eine fehlerfreie Nutzererfahrung und das Begrenzen von Halluzinationen. Das sei bei Tempo ein Großteil der Arbeit. | Anekdote | [MCP clearly explained](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), 18:25 |

## Wo Vorsicht geboten ist

- **Die meisten Aussagen stammen nicht von Isenberg.** Die Erklärungen zu MCP kommen überwiegend vom Gast Ross Mike. Isenberg selbst ist sicher nur die HTTPS/SMTP-Analogie zuzuordnen (15:54).
- **Eigeninteresse des Gasts:** Ross Mike arbeitet bei Tempo, und Tempo wird als Beispiel für einen MCP Client genannt (11:07, 18:25).
- **Nichts davon ist belegt.** Alle Aussagen sind Behauptungen ohne Beleg oder Anekdoten.
- **Früher Stand von MCP:** Die umständliche Einrichtung (13:57) und die Einschätzung, es gebe keine großen Geschäftschancen (19:21), beschreiben die Lage zum Zeitpunkt der Aufnahme. Den aktuellen Stand vor der Anwendung prüfen.
- **Standardrisiko:** Selbst der Sprecher hält MCP nicht für gesetzt (17:43). Wer darauf baut, trägt dieses Risiko.
- **Analogie statt Beleg:** Der Vergleich mit HTTPS und SMTP zeigt nicht, dass MCP eine ähnliche Rolle einnehmen wird (15:54).
- **Sicherheit fehlt:** Wie man Schreibzugriff per MCP absichert, etwa auf eine produktive Datenbank, behandelt das Video nicht (06:26).
- **Ungeprüfte Startup-Idee:** Für das MCP-Verzeichnis gibt es keinen Markttest, keine Wettbewerbsanalyse und kein Geschäftsmodell (16:41).

## Alle Quellen

- [Model Context Protocol (MCP), clearly explained (why it matters)](../quellen/2026/11/2026-11-09-model-context-protocol-mcp-clearly-explained-why-it-matters.md), erfasst am 2026-11-09, mit Gast Ross Mike. Learnings L-20261109-036 bis L-20261109-051
