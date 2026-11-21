# Claude Code klar erklärt (und wie man es nutzt)

> **Quelle:** [Claude Code Clearly Explained (and how to use it)](https://www.youtube.com/watch?v=zxMjOqM7DFs) · Greg Isenberg, Ras Mic, Late Checkout · Video · 2026-11-21
> **Sprecher verkauft:** nicht ausgewiesen; Greg Isenberg zeigt idealbrowser.com, Ras Mic verweist auf den eigenen YouTube-Kanal und das Repository ralphy · **Zielmarkt der Aussagen:** Creator und kleine Firmen, die ohne Entwicklerteam Software bauen · **Beweislage:** Live-Demos im Terminal, Faustregeln aus eigener Praxis, keine Messungen.

## Worum es geht
Das Video beantwortet die Frage, wie man mit Coding-Agenten wie Claude Code, OpenCode oder Codex Software baut, die andere Menschen benutzen können, statt Code-Müll zu erzeugen. Kern ist ein Ablauf: gründlich planen, das Produkt in Features zerlegen, jedes Feature einzeln bauen und testen. Erst danach kommt ein automatisierter Loop. Die Zielgruppe sind Gründer, Creator und kleine Teams ohne tiefe Entwicklungserfahrung.

## Was man anwenden kann

1. **Plan als wichtigstes Input-Artefakt behandeln.** Ras Mic setzt die Qualität der Ausgabe gleich mit der Qualität der Eingabe: PRD, Aufgabenliste oder Plan (01:40, 03:00). Er vergleicht das mit einem menschlichen Ingenieur, der bei dürftigen Anweisungen raten muss (02:30). Das Prinzip gilt laut Ras Mic für Claude Code, OpenCode und Codex gleichermaßen (01:25).

2. **Produkt in Kernfeatures zerlegen.** Statt ein Produkt pauschal zu beschreiben, wird es in etwa vier Kernfunktionen aufgeteilt. Sind alle vier gebaut, gilt das Produkt als fertig (04:00). Beispiel ist eine Tagesidee von idealbrowser.com: ein Diagnosewerkzeug für Haushaltsgeräte-Techniker gegen teure Wiederholungsbesuche (03:30).

3. **Test als Schranke zwischen Features.** Bevor der Agent mit Feature 2 beginnt, schreibt er einen Test für Feature 1. Erst wenn der Test besteht, geht es weiter (05:00).

4. **Plan-Modus einschalten.** In Claude Code schaltet Shift + Tab in den Plan-Modus (06:10). Der Startprompt im Video verlangt einen Plan für eine TikTok-UGC-App einer Marketingagentur und lässt ihn in `prd.md` schreiben (06:20). Gezeigt wird Claude Code v2.1.9 mit Opus 4.5 im Claude-Max-Abo (06:40).

5. **Plan per AskUserQuestionTool verhören lassen.** Nach dem ersten Plan liest Claude Code die Datei erneut und interviewt den Nutzer über das integrierte AskUserQuestionTool (07:25, 07:40). Runde 1 fragt nach Video-Workflow, Umgang mit HeyGen-API-Kosten und Limits sowie Hosting (Supabase/Vercel oder klassisch PostgreSQL/Node) (10:30). Runde 2 fragt nach dem Modell für Skripte, UI-Stil und Versionsverwaltung von Skripten (11:30). Der normale Plan-Modus war nach zwei Fragerunden baubereit. Das Interview fragte zusätzlich nach Avatar-Typen, Download oder Cloud-Speicher und Ordnerstruktur für Kampagnen (13:40).

6. **Unbekannte Fragen an einen zweiten Chatbot geben.** Wer eine Interviewfrage nicht beantworten kann, kopiert sie in ChatGPT oder Claude Chat, lässt sich die Optionen erklären und gibt die Entscheidung zurück an den Agenten (10:15).

7. **Ohne Terminal-Kenntnisse einsteigen.** Terminal-Befehle kann man sich von einer KI erklären lassen. Alternativ öffnet man in der Claude-Desktop-App den Code-Bereich und gibt einen Ordner frei (05:40). Ras Mic selbst nutzt den Terminal-Emulator Ghostty, nennt das aber reine Vorliebe (24:00).

8. **Ralph-Loop verstehen.** Ein Ralph-Loop nimmt die Aufgabenliste aus `prd.md`, lässt das Modell die erste Aufgabe erledigen, protokolliert sie in `progress.txt` und wiederholt das bis zum Ende der Liste (17:40). Ras Mics Variante erzwingt nach jedem Feature einen Test und Linting. Scheitert ein Test, arbeitet das Modell am betroffenen Feature weiter, statt fortzufahren (19:40).

9. **Loop per Prompt installieren.** Das gezeigte Repository ist `michaellatman/ralphy` auf GitHub (20:30). Man kopiert die URL in Claude Code mit der Anweisung, diesen Loop ausführen zu wollen; der Agent leitet durch die Installation (20:40). Gestartet wird mit `./ralphy.sh` (21:08). Im Testlauf baut der Loop einen minimalen Bun-HTTP-Server mit `/health` und `/hello`; `progress.txt` meldet danach Port 3000, 3 von 3 Tests bestanden und erfolgreiche TypeScript-Typprüfung (20:55, 22:48).

10. **Loop erst nach dem ersten eigenen Deployment.** Ras Mic rät Anfängern von Ralph-Loops ab. Voraussetzung ist, dass man schon ohne Automatisierung etwas gebaut und unter einer Live-URL, etwa auf Vercel, bereitgestellt hat (14:55, 25:08). Wer Features einzeln baut und prüft, entwickelt ein Gespür für Qualität, das jemand im Video „Vibe QA Testing“ nennt (15:35).

11. **Kontextfenster höchstens zur Hälfte füllen.** Bei Opus 4.5 mit 200.000 Tokens Kontext soll man ab etwa 100.000 Tokens, spätestens bei 40 bis 50 Prozent Auslastung, eine neue Session starten. Darüber verschlechtere sich die Ausgabe (26:00).

12. **Nicht an MCP, Skills und Markdown-Dateien festbeißen.** `prompt.md` und `agent.md` sind reine Markdown-Dateien, Plugins sind Skills mit etwas mehr Funktion (16:40). Scheitert ein Produkt, liegt es laut Ras Mic fast immer am Plan, nicht an fehlenden MCPs (24:45).

13. **Auf Papier skizzieren.** Als Beispiel zeigt Greg Isenberg die Lauf-App „Animo“, die eine Route nach der aktuellen Stimmung erzeugt. Deren Entwickler zeichnete vor dem Coden Szenarien, Wireframes, Farben und Papier-Prototypen, um Interaktionen selbst festzulegen (28:10, 29:30).

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 4 Kernfeatures | Beispielhafte Zerlegung eines Produkts | Faustregel des Sprechers |
| 2 Fragerunden | Normaler Plan-Modus bis zur Baubereitschaft in der Demo | im Video gezeigt |
| 200.000 Tokens | Kontextfenster von Opus 4.5 | Sprecherangabe |
| 50 % / 100.000 Tokens | Grenze, ab der eine neue Session starten soll | Erfahrungswert, nicht gemessen |
| 3/3 Tests, Port 3000 | Ergebnis des Bun-Testlaufs mit ralphy | im Video gezeigt |
| v2.1.9 | Gezeigte Claude-Code-Version | Bildschirm |
| 17,5K Abonnenten | YouTube-Kanal von Ras Mic | Bildschirm |

## Wortlaute

- „I want to build a TikTok UGC generating app for my marketing agency. please help me create a plan. Write this in a prd.md file.“ (06:20) Startprompt im Plan-Modus.
- „Read this plan file and interview me in detail using AskUserQuestionTool about literally anything: technical implementation, UI & UX, concerns, tradeoffs, etc.“ (07:40) Prompt, der das Interview zum Plan auslöst.
- „Before moving on to feature two, what I'm going to do is I'm going to get the model to write a test“ (05:00) Testschranke zwischen Features.
- „Building personal software is easy. But building software others are going to use is very, very difficult.“ (14:00) Begründung für den Planungsaufwand.

## Grenzen und Widerspruch

- Die Behauptung, ein besserer Plan spare Tokens (12:00), wird nicht beziffert. Es gibt keinen Kostenvergleich mit und ohne AskUserQuestionTool.
- Die 50-Prozent-Regel für den Kontext ist eine persönliche Einschätzung („in my opinion“), keine Messung.
- Ras Mic rät vom offiziellen Ralph-Wiggum-Plugin in Claude Code ab, weil angeblich selbst der Erfinder der Methode dagegen sei (18:55). Quelle und Begründung fehlen, ebenso ein Vergleich der Fehlerraten mit ralphy.
- Der Bun-Testlauf ist trivial. Ob der Loop bei einer echten App mit externen APIs wie HeyGen gleich zuverlässig läuft, zeigt das Video nicht.
- Zum Erfolg der Animo-App gibt es keine Nutzer- oder Umsatzzahlen.
- Alle Aussagen stammen aus der Perspektive von Einzelentwicklern und kleinen Teams. Für Unternehmen mit Code-Review-Prozessen, Sicherheitsvorgaben oder Datenschutzpflichten trifft das Video keine Aussagen.
- Die Demo läuft auf Opus 4.5 im Max-Abo. Wie sich der Ablauf mit kleineren oder günstigeren Modellen verhält, bleibt offen.
