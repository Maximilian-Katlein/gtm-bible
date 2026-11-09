# Model Context Protocol (MCP), klar erklärt (und warum es zählt)

> **Quelle:** [Model Context Protocol (MCP), clearly explained (why it matters)](https://www.youtube.com/watch?v=7j_NE6Pjv-E) · Ross Mike (Tempo), Greg Isenberg (Startup Empire) · Video · 2026-11-09
> **Sprecher verkauft:** Im Inhalt nichts; Ross Mike arbeitet bei Tempo, das er selbst als MCP Client nennt, Greg bewirbt im Werbeblock seine Mitgliedschaft Startup Empire · **Zielmarkt der Aussagen:** unklar, Publikum sind Gründer und Startup-Bauer · **Beweislage:** rein konzeptionelle Erklärung ohne Zahlen, Kundenfälle oder Vorführung, gestützt auf Einschätzungen und Anekdoten aus der Arbeit bei Tempo.

## Worum es geht
Das Video erklärt Nicht-Technikern, was MCP ist: ein Standard, über den ein Sprachmodell mit externen Diensten spricht, und kein technischer Durchbruch. Es ordnet MCP in drei Stufen ein (LLM allein, LLM plus Tools, LLM plus MCP) und fragt, ob Gründer daraus schon ein Geschäft machen können. Die Antwort des Gasts ist zurückhaltend: Er rät eher zum Beobachten als zum Bauen.

## Was man anwenden kann
1. **Drei Stufen als Prüfraster nutzen.** Stufe 1: Ein LLM allein sagt nur den nächsten Text voraus und kann zum Beispiel keine E-Mail senden (02:39, 03:22). Stufe 2: Entwickler geben dem Modell Tools, also Zugriff auf externe Dienste wie eine Suche oder eine Automation in Zapier oder n8n (04:19, 04:46). Stufe 3: MCP als einheitliche Schicht zwischen Modell und Diensten (08:45). Mit dem Raster lässt sich bei jedem KI-Produkt prüfen, wo es steht und wo seine Schwächen liegen.

2. **Integrationsaufwand in Stufe 2 ehrlich einplanen.** Wer mehrere Tools an ein Modell hängt, wird laut Ross Mike zum „Kleber“: Jeder Anbieter baut seine API anders, mit anderen Feldern und Einrichtungsschritten (08:13). Dazu kommen Schritt-für-Schritt-Planung und viele Randfälle, in denen die Kette scheitert (09:38). Das gilt besonders für Assistenten, die viele Dienste gleichzeitig nutzen sollen.

3. **Ketten auf Änderungen der Fremd-API prüfen.** Sein Beispiel: Jede Slack-Nachricht wird vom Modell gelesen und als SMS weitergeleitet. Ändert Slack seine API oder der SMS-Dienst etwas, bricht die Kette, umso schlimmer, je mehr Dienste daran hängen (10:18). Praktisch heißt das: Für jede fest verdrahtete Integration jemanden benennen, der Änderungen beobachtet und Brüche behebt.

4. **Die vier Teile von MCP auseinanderhalten.** MCP Client (die Seite zu Nutzer und Modell, genannt werden Tempo, Windsurf und Cursor), Protokoll (Zweiwegverbindung), MCP Server (übersetzt Fähigkeiten eines Dienstes für den Client) und der Dienst selbst (11:07 bis 11:34). Wer eine Integration plant, klärt zuerst, auf welcher dieser Seiten er baut.

5. **Als Anbieter selbst den MCP Server bauen.** Der Server liegt in der Hand des Dienstanbieters. Wer etwa eine Datenbankfirma betreibt und will, dass Modelle darauf zugreifen, muss den Server selbst liefern (11:59). Das gilt für Anbieter von Dev Tools, Datenbanken und anderen Diensten, die Drittentwickler oder Partner anbinden wollen (13:06). Ross Mike beobachtet, dass Anbieter bereits Server und Repos veröffentlichen, nennt aber keine Namen (12:36).

6. **Schreibzugriff per MCP nur kontrolliert freigeben.** Sein Beispiel: Das Modell ist per MCP mit einer Datenbank wie Convex oder Supabase verbunden und legt auf Zuruf einen neuen Eintrag an (09:26). Wie Berechtigungen, Prüfungen oder Rücknahmen dabei laufen, sagt das Video nicht. Diese Fragen muss man selbst klären.

7. **Einrichtungsaufwand realistisch einschätzen.** Zum Zeitpunkt der Aufnahme hieß Einrichten eines Servers in einem Client: herunterladen, Dateien verschieben, Werte kopieren, vieles lokal betreiben (13:57). Für nicht-technische Teams war MCP damals kein Selbstbedienungswerkzeug.

8. **Startup-Idee: Verzeichnis mit Ein-Klick-Bereitstellung.** Eine Website listet MCP Server aus den Repos, zeigt den GitHub-Code und stellt den Server per Klick auf „install“ oder „deploy“ bereit. Der Nutzer bekommt eine eigene URL, die er in seinen Client einträgt (16:41). Gilt nur für technische Gründer. Es gibt keinen Markttest, keine Wettbewerbsanalyse und kein Geschäftsmodell.

9. **Nicht-Techniker: beobachten statt bauen.** Er rät, zu verfolgen, welche Plattformen MCP-Fähigkeiten ausbauen und wohin sich der Standard entwickelt (17:31). Für Techniker wie Nicht-Techniker sah er zum Zeitpunkt der Aufnahme keine großen Geschäftschancen (19:21). Das Verständnis des Prinzips lohne sich trotzdem, weil es auf einen späteren Standard übertragbar sei (19:33).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 4 | Teile des MCP-Ökosystems: Client, Protokoll, Server, Dienst (11:07) | Erklärmodell des Sprechers |
| 2 Stunden | Zeit, in der Ross Mike nach eigener Aussage eine Chatbot-Oberfläche mit Tools bauen könnte, ohne fehlerfreie Nutzererfahrung (18:25) | Anekdote, nicht vorgeführt |
| 3 Stufen | LLM allein, LLM plus Tools, LLM plus MCP (02:39 bis 08:45) | Erklärmodell des Sprechers |

## Wortlaute
- „the mCP server is now in the hands of the service provider“ (11:59). Steht für die Kernthese: Die Integrationsarbeit wandert vom Bauer des KI-Produkts zum Dienstanbieter.
- „I can sit in two hours and build something like this but building out that user experience making it Flawless limiting the hallucinations it's very very hard“ (18:25). Steht für den Unterschied zwischen Prototyp und belastbarem Produkt.
- „I don't know if mCP has fully won I think it needs to be challenged“ (17:43). Steht für die eigene Einschränkung des Sprechers.

## Grenzen und Widerspruch
- **Keine Belege.** Es gibt keine Zahlen zur Verbreitung, keine namentlich genannten Anbieter mit eigenem MCP Server, keine Messwerte und keinen Kundenfall.
- **Keine Anleitung.** Es fehlen Konfiguration, Beispiel-Prompts und eine Liste konkreter Server. Ab 01:32 teilt Ross Mike den Bildschirm. Gezeigte Diagramme sind in dieser Auswertung nicht erfasst, weil sie nur auf automatischen Untertiteln beruht.
- **Offene Risiken.** Sicherheit und Berechtigungen bei Schreibzugriff, Kosten und Zuverlässigkeit werden nicht behandelt. Halluzinationen gelten im Video als Problem von Stufe 2. Ob MCP sie verringert, bleibt offen.
- **Kein Vergleich.** Andere Ansätze wie Function Calling oder OpenAPI werden nicht eingeordnet. Welche Modellanbieter außer Anthropic MCP unterstützen, bleibt offen.
- **Innerer Widerspruch.** Erst heißt es, REST sei ein Standard, dem jede Firma folgt (02:09), später, jeder Anbieter baue seine API anders (08:13). Damit bleibt offen, warum MCP als Standard einheitlicher werden sollte als REST.
- **Einschätzungen statt Fakten.** „Anthropic spielt 3D-Schach“ (11:54) und die Erwartung, alle Firmen würden folgen (12:56), sind Meinungen. Ross Mike relativiert sie selbst: MCP habe nicht gewonnen, ein anderer Anbieter könne einen eigenen Standard vorlegen (17:43, 19:25).
- **Interessen.** Ross Mike nennt seinen Arbeitgeber Tempo als MCP Client in einer Reihe mit Windsurf und Cursor. Greg bewirbt Startup Empire (06:50 bis 07:41). Angekündigt waren mehrere Startup-Ideen (00:35), geliefert wird eine.
- **Zeitstand.** Die Aussagen beschreiben einen frühen Stand von MCP. Die Hinweise zu umständlicher Einrichtung und fehlenden Geschäftschancen sind vor heutiger Anwendung zu prüfen.
- **Bezug zu B2B Go-to-Market** gibt es nur mittelbar: über die Frage, ob Anbieter ihren Dienst per MCP Server für KI-Clients zugänglich machen.
