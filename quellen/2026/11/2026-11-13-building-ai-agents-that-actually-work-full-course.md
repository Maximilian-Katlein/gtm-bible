# KI-Agenten bauen, die wirklich funktionieren (kompletter Kurs)

> **Quelle:** [Building AI Agents that actually work (Full Course)](https://www.youtube.com/watch?v=eA9Zf2-qYYM) · Remy Gaskill (Gast), Moderation Greg Isenberg, Firma unklar · Video · 2026-11-13
> **Sprecher verkauft:** Im Material nichts Konkretes; implizit Remys eigenes „AI OS“-Setup sowie Werkzeuge wie Claude Co-work und Monologue, ohne Vergleich mit Alternativen · **Zielmarkt der Aussagen:** SMB und Creator (Solo-Gründer, Agenturinhaber) · **Beweislage:** vorbereitete Demos mit fiktiven Fällen, alle Produktivitätszahlen sind Selbstaussagen ohne Messung.

## Worum es geht
Wie richtet man einen KI-Agenten so ein, dass er mit kurzen Prompts brauchbare Arbeit liefert und aus Korrekturen lernt? Das Video zeigt dafür vier Bausteine (Kontextdatei, Memory, Tool-Anbindung per MCP, Skills) in Claude Code, Codex und Antigravity. Es richtet sich an Solo-Gründer und kleine Teams, die Assistenz-, Marketing- und Vertriebsaufgaben an Agenten abgeben wollen.

## Was man anwenden kann
1. **Abschlusskriterien in den Prompt schreiben.** Ein Agent läuft im Kreis aus Beobachten, Entscheiden und Handeln, bis er die Aufgabe für erledigt hält (03:42). Wann das ist, steuern messbare Vorgaben im Prompt, etwa „10 Quellen sammeln, daraus eine PowerPoint bauen“ (05:23). Ohne solche Kriterien entscheidet der Agent selbst, wann er aufhört.

2. **Eine Kontextdatei mit exakt dem richtigen Namen anlegen.** Im Projektordner liegt ein dauerhafter System Prompt: `Claude.md` in Claude Code, `Gemini.md` bei Gemini, `agents.md` bei Codex und Open Claw (20:26). Inhalt laut Demo: Person, Geschäftsmodell, Arbeitspräferenzen, genutzte Tools mit Zweck, ideales Kundenprofil (21:02). Ohne diese Datei fragt der Agent bei „Schreib mir eine Cold Email“ erst nach Angebot, Zielgruppe und Ton (17:52); mit ihr kommt direkt ein brauchbarer Entwurf.

3. **Die Kontextdatei per Interview erzeugen lassen.** Wer keine Datei hat, lässt Claude Chat oder Co-work Fragen im Interviewstil stellen und daraus die Datei schreiben (21:15). Das ist der schnellste Einstieg und braucht keine Vorlage.

4. **Viel Kontext in einen Ordner auslagern.** Bei umfangreichem Material legt Remy einen Ordner `context` an (über mich, Brand Voice, Ideal Customer Profile). Die Hauptdatei enthält nur die Anweisung, diesen Ordner vor jeder Aufgabe zu lesen (23:28). Ohne diese Anweisung lädt der Agent den Ordner nicht. Auf demselben Weg lässt sich ein Obsidian-Vault einbinden.

5. **memory.md plus Update-Regel einrichten.** Agenten speichern Korrekturen nicht von selbst: „Unterschreib mit Warm regards“ ist in der nächsten Session vergessen (25:58). Abhilfe: eine leere `memory.md` mit denselben Abschnitten wie die Kontextdatei, und oben in der Hauptdatei ein Regelblock: Context-Ordner lesen, memory.md lesen, bei Korrektur den passenden Abschnitt aktualisieren, Veraltetes ersetzen (27:12). In der Demo speichert der Agent danach eine Präferenz selbstständig. Manche Harnesses wie Open Claw haben das eingebaut (28:50).

6. **Hauptdatei klein halten.** Remy nennt als Best Practice höchstens etwa 200 Zeilen für die `Claude.md` (30:44). Gegen widersprüchliche Regeln: nur substanzielle Korrekturen speichern lassen und gelegentlich von Hand aufräumen.

7. **Einen Ordner je Firma, einen Unterordner je Funktion.** Pro Kunde oder Firma ein Ordner, darin je ein „Head of Department“ (Marketing, Executive Assistant, Content Team) mit eigenen Skills, Tool-Anbindungen und Kontext (14:52). Die Kontextdatei beginnt dort mit einer Rolle wie „Du bist mein Head of Marketing“ (24:22). Ein übergeordneter Orchestrator kann die Rollen koordinieren (48:19).

8. **Tools per MCP anbinden statt zwischen Apps zu kopieren.** Standardmäßig haben die meisten Harnesses nur Websuche (33:25). Remy hat Gmail, Google Calendar, Drive, Granola, Stripe und Notion angebunden (35:42). Demo mit fiktivem Prospect: Meeting-Notizen aus Granola lesen, Angebotsmail entwerfen, Stripe-Zahlungslink erzeugen, Notion-Projekt anlegen, Gmail-Entwurf ablegen, alles in einem Prompt (36:57).

9. **Zugriffsrechte nach dem schlimmsten Fall begrenzen.** Für Agenten mit Zugriff auf Budgets, etwa einen Meta-Ads-Agenten, rät Remy zu Read-only-Rechten auf kritischen Plattformen, damit eine Kompromittierung wenig Schaden anrichtet (08:59). Open Claw nennt Remy im Vergleich zu Claude Code, Codex und Antigravity „Wild West“ (09:58).

10. **Wiederkehrende Prozesse in Skills verwandeln.** Ein Skill ist eine Arbeitsanweisung als Markdown-Datei, optional mit Referenzdateien, abgelegt z. B. unter `.claude/skills` (40:20). Prozessdetails wie Aufbau und Farben eines Angebots gehören in einen Skill, nicht in memory.md (40:51). Zwei Wege: aus einem transkribierten Kurs mit dem eingebauten Skill Creator (43:39) oder nach einem manuellen Durchlauf mit „Erstell einen Skill aus dem, was wir gerade gemacht haben“ (44:25). Remys Ads-Analyst-Skill entstand so aus rund zwei Stunden Arbeit in einer frischen Session (49:34).

11. **Skills zeitlich planen und verketten.** Per Scheduled Task in Co-work oder Claude Code läuft ein Daily-Brief-Skill täglich um 9:00 Uhr und fasst Kalender, Inbox und Notion zusammen (45:41). Er kann einen Recherche-Skill aufrufen, wenn Meetings oder Podcastgäste anstehen (51:12). Remys Newsletter-Team lässt donnerstags morgens Twitter und Reddit nach AI-Neuigkeiten durchsuchen (53:14).

12. **Recherchierte Fakten vor Veröffentlichung prüfen.** Die live generierte Portfolio-Seite für Greg enthielt eine falsche E-Mail-Adresse und einen falschen Wohnort (12:39), obwohl der Agent per Perplexity recherchiert und das Ergebnis per Screenshot selbst geprüft hatte (13:37).

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1 bis 2 Stunden pro Tag | versprochene Zeitersparnis durch einen Executive-Assistant-Agenten (15:21) | Behauptung ohne Beleg |
| 10 bis 20 mal | Produktivität von Gründern mit Agenten, Aussage Greg (38:44) | Behauptung ohne Beleg |
| etwa 7 mal schneller | Demo-Aufgabe Prospect-Follow-up, Schätzung Remy (38:44) | Behauptung ohne Beleg |
| 3 bis 4 Stunden | manueller Aufwand der Ads-Analyse zu Agenturzeiten (49:34) | Anekdote, Schätzung |
| rund 220 | gescrapte Anzeigen einer E-Com-Marke aus der Meta Ads Library (49:09) | eigene Daten, Demo |
| etwa 2 Stunden | Aufwand, um den Ads-Analyst-Prozess einmal durchzuspielen (49:34) | Anekdote |
| etwa 200 Zeilen | empfohlene Obergrenze der Claude.md (30:44) | Anekdote, nicht begründet |
| 15 bis 30 Minuten | Iteration an einem Angebot ohne Skill (40:51) | Anekdote |
| etwa 15 Minuten | Ersparnis je Weiterempfehlung mit Mini-Skill (46:52) | Anekdote |
| 3 bis 5 Prozesse pro Woche | empfohlenes Tempo, um Abläufe in Skills zu überführen (37:23) | Behauptung ohne Beleg |
| 250 Dollar | Preisidee für vorgebaute Websites per Cold Email (14:17) | Behauptung ohne Beleg, nicht getestet |

## Wortlaute
- „before answering any questions or before doing any tasks, read my context folder to understand about myself and my business.“ (23:28) Pointer-Anweisung in der Hauptdatei.
- „when I correct you or you learn something new, update the relevant section in memory.md.“ (27:12) Kernregel, die Korrekturen dauerhaft macht.
- „Hey, take this course on viral hooks and create a viral hook skill.“ (43:39) Skill aus Kursmaterial erzeugen.
- „once you've done the task, 'Hey, create a skill for what we just did.'“ (44:25) Skill nach manuellem Durchlauf.
- „Use my daily brief skill to prepare me for my day.“ (45:41) Prompt für die tägliche geplante Aufgabe.
- „Hey, I built you this website, so-and-so business. Do you want it? It's going to cost $250.“ (14:17) Cold-Email-Idee, ungetestet.

## Grenzen und Widerspruch
- **Keine Messung.** Alle Produktivitätszahlen sind Selbstaussagen ohne Vergleichsbasis. Die Demos nutzen vorbereitete, fiktive Fälle (Fake-Meeting in Granola, selbst geschickte Prospect-Mail), keine echten Kundenfälle.
- **Unvollständig.** Das Material endet bei 53:54 mitten im Satz; der angekündigte Open-Claw-Teil fehlt. Wortlaut von agents.md, memory.md-Regeln und Skill-Dateien ist nur auf dem Bildschirm zu sehen. Aufbau und Frontmatter einer skill.md werden nicht erklärt.
- **Sicherheit oberflächlich.** Prompt Injection über eingehende E-Mails oder gescrapte Seiten wird nicht behandelt. Der Agent hat in der Demo Schreibrechte auf Gmail, Stripe und Notion, im Widerspruch zum eigenen Rat, Rechte eng zu fassen.
- **Datenschutz fehlt.** E-Mails, Meeting-Notizen, Zahlungs- und Kundendaten laufen über US-Cloud-Modelle. DSGVO, Auftragsverarbeitung, lokale oder Open-Weight-Modelle kommen nicht vor. Für Firmen in der EU ist das vor dem Nachbau zu klären.
- **Keine Kosten.** Tokenverbrauch, Modellwahl pro Aufgabe und Fehlerquoten fehlen. Der Harness-Vergleich beruht auf einem einzigen Lauf und der Optik einer Website.
- **Zielgruppe eng.** Belegt ist nur der Alltag von Solo-Gründern und Kleinstfirmen. Für Mid-Market- oder Enterprise-Vertrieb mit Freigabeprozessen und CRM-Pflicht gibt es keine Einordnung.
- **Fehlerfälle fehlen.** Widersprüchliche Memory-Regeln oder Skills, die nicht ausgelöst werden, werden nur erwähnt, nicht gezeigt.
