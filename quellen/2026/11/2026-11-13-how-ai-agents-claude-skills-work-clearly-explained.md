# Wie KI-Agenten und Claude Skills funktionieren (klar erklärt)

> **Quelle:** [How AI agents & Claude skills work (Clearly Explained)](https://www.youtube.com/watch?v=S_oN3vlzpMw) · Ross Mike (Michael Shimeles) und Greg Isenberg, Late Checkout · Video · 2026-11-13
> **Sprecher verkauft:** Content, AI-Building-Education und Community; Ross Mike zeigt sein eigenes Skill-Repository auf GitHub · **Zielmarkt der Aussagen:** Developer, AI Builder, Creator, Kleinbetriebe (00:15) · **Beweislage:** Praxiserfahrung eines einzelnen Builders mit einer Token-Messung am Bildschirm, viele Prozentangaben sind Faustregeln ohne Messung.

## Worum es geht
Wie steuert man den Kontext eines Coding- oder Workflow-Agenten so, dass brauchbare Ergebnisse statt „Slop“ entstehen? Das Video erklärt, wann eine agent.md oder claude.md sinnvoll ist, wann ein Skill die bessere Wahl ist und wie man Skills aus einem echten Durchlauf ableitet statt sie vorab zu schreiben. Es richtet sich an Einzelentwickler, Creator und kleine Teams, die mit Claude Code, Codex oder OpenClaw arbeiten.

## Was man anwenden kann
1. **agent.md und claude.md radikal kürzen.** Der Agent liest die Codebasis selbst. Hinweise wie „wir nutzen React“ oder ein Tech-Stack aus Next.js, Convex und Supabase sind überflüssig, weil der Code selbst Kontext ist (02:05, 19:15). In die Datei gehört nur proprietäres Wissen, das in jedem einzelnen Dialogschritt gebraucht wird (03:05). Gilt für Entwickler, deren Codebasis der Agent direkt lesen kann.

2. **Nur Abweichungen vom Standard notieren.** Keine Selbstverständlichkeiten vorgeben. Eine Sonderregel wie eine abweichende Währung gehört hinein, die Regel „Dollarzeichen für Geld“ nicht (32:15).

3. **Wiederkehrendes Wissen als Skill statt als Dauerkontext ablegen.** Eine claude.md mit rund 1.000 Zeilen kostet laut Sprecher etwa 7.000 Tokens bei jedem Lauf (04:20). Skills arbeiten mit Progressive Disclosure: Geladen werden zunächst nur Name und Beschreibung, der volle Inhalt erst bei Bedarf (03:25). Eine Skill-Datei besteht aus `name`, `description` und darunter den Anweisungen (05:00).

4. **Skills aus einem erfolgreichen Durchlauf ableiten, nicht vorab schreiben.** Drei Schritte (11:40): Workflow identifizieren. Den Prozess im Dialog Schritt für Schritt mit dem Agenten durchspielen und korrigieren. Nach dem gelungenen Lauf den Agenten seinen Verlauf prüfen und daraus die skill.md erstellen lassen. Den Skill sofort nach dem Erkennen eines Workflows zu schreiben, nennt der Sprecher den größten Fehler (08:30). Für das Schreiben selbst gibt es bereits einen Skill, der Skills erzeugt („Skillception“, 12:25).

5. **Skills rekursiv härten.** Ablauf (20:45): Entwurf erstellen, Agent laufen lassen, bei einem Fehlschlag gezielt nach der genauen Fehlermeldung fragen, Fehler beheben lassen, Lösung in die skill.md zurückschreiben. Beim gezeigten Report-Generator, der acht Datenquellen abfragt (u. a. Notion, Dub Analytics, YouTube Analytics, Twitter Analytics), brauchte es fünf solcher Schleifen, bis der rund zehnminütige Lauf fehlerfrei war (22:15).

6. **Prüfkriterien explizit machen.** Ohne Regeln stufte der Agent jede Sponsor-Mail als seriös ein, eine eigene Recherche fand nicht statt (08:00). Erst die Vorgabe, Twitter, YouTube, Trustpilot und eine Finanzierungsrunde zu prüfen und bei zwei fehlenden oder schlechten Signalen automatisch abzulehnen, machte die Bewertung brauchbar (09:30). Abgelehnte Anfragen trägt der Agent als „no contact“ in ein Google Sheet ein (09:55). Belegt nur für einen Creator, der Sponsoranfragen filtert.

7. **E-Mail-Agenten vom Hauptpostfach trennen.** Der OpenClaw-Agent des Sprechers hat eine eigene Mailadresse und keinen Zugriff auf das persönliche Postfach, wegen Angriffsflächen wie Prompt Injection (07:35). Schutzprotokolle darüber hinaus nennt er nicht.

8. **Keine fremden Skills von Marktplätzen importieren.** Zwei Gründe (12:40): Dem eigenen Agenten fehlt der Kontext eines erfolgreichen Laufs, und fremde Skills sind ein einfaches Einfallstor für Angriffe.

9. **Mit einem Agenten anfangen, Sub-Agenten erst später.** 15 Sub-Agenten und 30 Skills zum Start hält der Sprecher für Show statt Produktivität (14:35). Er selbst hat erst nach festen Workflows Sub-Agenten ergänzt und steuert heute einen Hauptagenten mit fünf Sub-Agenten, u. a. für Marketing, Business und Privates (25:50).

10. **Kontextfenster im mittleren Bereich halten.** Faustregel des Sprechers: zwischen frisch und etwa 70 Prozent Füllstand arbeiten, ab etwa 80 Prozent werde der Agent „dumm“ (31:15). Das Fenster startet bei etwa 20.000 Tokens aus System-Prompt, agent.md, Skill-Beschreibungen, Tools, Codebasis und Dialog und wächst bis zum Limit, ab dem Claude Code und Codex automatisch verdichten (06:05, 06:45).

11. **Mit soliden Templates starten.** Ein sauberes Web- oder App-Template wird zum Kontextfundament, auf dem der Agent aufbaut. Der Sprecher erwartet eine Renaissance von Templates (20:10), das ist eine Prognose.

12. **Rund zwei Wochen Einarbeitung einplanen.** Für ein neues Agenten-Harness wie OpenClaw nennt der Sprecher etwa zwei Wochen mühsame Anfangsinvestition, basierend auf seiner eigenen Erfahrung (23:50).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 95 % | Anteil der Entwickler, die keine agent.md oder claude.md brauchen | Schätzung des Sprechers ohne Messung |
| ca. 7.000 Tokens | Kosten einer 1.000-Zeilen-claude.md pro Lauf | Schätzung des Sprechers |
| 944 Tokens / 4.495 Zeichen | Vollständige Datei code-structure/SKILL.md im OpenAI Tokenizer | Am Bildschirm gemessen (30:40) |
| 53 Tokens / 304 Zeichen | Nur Name und Beschreibung derselben Datei | Am Bildschirm gemessen (30:40) |
| ca. 20.000 Tokens | Startgröße des Kontextfensters eines Coding-Agenten | Angabe des Sprechers, abhängig von Setup |
| 250.000 Tokens | Genanntes Limit, ab dem verdichtet wird | Angabe des Sprechers, je nach Modell und Werkzeug verschieden |
| 10 bis 70 % | Empfohlener Füllstand des Kontextfensters | Faustregel ohne Messung |
| 8 Quellen, 5 Schleifen, ca. 10 Minuten | Report-Generator des Sprechers | Eigener Fall |
| 1 + 5 | Hauptagent und Sub-Agenten im Setup des Sprechers | Eigener Fall |
| 2 Wochen | Einarbeitung in ein Agenten-Harness | Eigene Erfahrung |
| 1,8 Mrd. USD | Wert einer angeblich vollständig vibe-gecodeten App | Anekdote, unklar ob Umsatz oder Bewertung |
| 150.000 USD pro Jahr | Umsatz eines Zuschauers mit einem Kuchen-Business | Anekdote, nicht überprüfbar |

## Wortlaute
- „check their Twitter, check their YouTube, check their Trustpilot, check if they raised any money. If two of these don't exist are not in good standing, automatic rejection.“ (09:30) Steht für eine Prüfregel, die ein Agent ohne Ermessensspielraum abarbeiten kann.
- „Once I've had that back and forth, then I tell the AI review what you did and then create the skill.“ (11:40) Steht für die Anweisung, mit der aus einem gelungenen Dialog ein Skill wird.
- „There is a name, there is a description, and then underneath is a bunch of information.“ (05:00) Steht für den minimalen Aufbau einer skill.md.

## Grenzen und Widerspruch
- Die 95-Prozent-Aussage zu agent.md ist eine Schätzung. Für Teams mit Konventionen, die nicht im Code sichtbar sind (Freigabeprozesse, Namensregeln, Sicherheitsvorgaben), kann eine kurze agent.md trotzdem sinnvoll sein. Der Sprecher räumt diesen Fall selbst ein (03:05).
- Kontextgrößen und Grenzwerte wie 250.000 Tokens oder 70 Prozent hängen von Modell und Werkzeug ab und sind nicht gemessen. Sie taugen als Orientierung, nicht als Vorgabe.
- Der erwähnte Qualitätsunterschied zwischen Cursor, Claude Code und Codex trotz ähnlicher Modelle (27:10) wird ohne Benchmark, Messwerte oder Testaufbau angeführt.
- Der Prompt des Sponsor-Agenten wird nicht vollständig gezeigt. Die Prüfregel ist auf einen Creator zugeschnitten, der Sponsoren filtert, nicht auf B2B-Lead-Qualifizierung im Unternehmen.
- Sicherheit wird nur angerissen: eigene Mailadresse, keine fremden Skills. Konkrete Schutzmaßnahmen gegen Prompt Injection fehlen.
- Erfolgsgeschichten (1,8 Mrd. USD, Kuchen-Business mit 150.000 USD) sind Anekdoten ohne Beleg und sagen nichts über die beschriebene Methode aus.
- Aussagen zur Funktionsweise von Sprachmodellen („sie denken nicht, sie sagen Tokens vorher“, 10:20) sind stark vereinfacht und dienen als Erklärhilfe.
- Alle Erfahrungen stammen von einem Einzelentwickler und Creator. Für größere Organisationen mit Rechte-, Compliance- und Freigabefragen gibt es keine Daten.
