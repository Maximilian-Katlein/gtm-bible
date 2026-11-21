# Wie ich Obsidian und Claude Code nutze, um mein Leben zu organisieren

> **Quelle:** [How I Use Obsidian + Claude Code to Run My Life](https://www.youtube.com/watch?v=6MBq1paspVU) · Vin (Internet Vin), NEW, im Gespräch mit Greg Isenberg, Late Checkout · Video · 2026-11-16
> **Sprecher verkauft:** Content, Wissenssysteme, KI-Workflows und Startup-Strategien (Podcast-Format, keine eigene Software im Angebot gezeigt) · **Zielmarkt der Aussagen:** Creator, Tech-Gründer und Knowledge Worker (51:30) · **Beweislage:** Live-Demo am eigenen Vault einer Einzelperson, keine Messung, keine Vergleichsdaten.

## Worum es geht
Wie baut man aus lokalen Markdown-Notizen ein Gedächtnis, auf das ein KI-Agent zugreifen kann, statt ihm in jeder Session das eigene Projekt neu zu erklären? Vin zeigt dafür seinen Obsidian-Vault, die Obsidian CLI und rund ein Dutzend selbst gebauter Claude-Code-Befehle. Das Material richtet sich an Einzelpersonen, die viel schreiben; Übertragung auf Teams wird nur angedacht.

## Was man anwenden kann
1. **Kontext als Datei statt als Chat.** Vin lässt Claude Code eine Projektbeschreibung als lokale Datei anlegen, etwa für eine minimalistische To-do-App, die Kalender, Nachrichten und Slack liest (04:30). In einer neuen Session referenziert er nur die Datei, das Modell hat den Kontext sofort und stellt Scoping-Fragen (06:19). Bedingung: Arbeit im Terminal mit Claude Code, nicht im Web-Interface.

2. **Notizen für Muster, nicht für Oberbegriffe.** Links auf allgemeine Begriffe wie „Podcast“ oder „Fitness“ bringen wenig. Vin legt je Theorie, Muster, Projekt oder Perspektive eine eigene Notiz an und verlinkt darauf (20:20). Personen bekommen eigene Dateien, die per doppelter eckiger Klammer aus Tagesnotizen verlinkt werden (07:58).

3. **Vault per Obsidian CLI an den Agenten anschließen.** Laut Vin gibt die Obsidian CLI Claude Code Zugriff auf Dateiinhalte und zusätzlich auf Backlinks und Graph-Struktur (10:45). Erst damit funktionieren die Befehle, die Zusammenhänge über Monate auswerten. Bei großen Vaults dauert eine Anfrage spürbar länger, in der Demo über fünf Minuten (36:00).

4. **Eigene Slash-Befehle für wiederkehrende Denkaufgaben.** Vin zeigt Befehle mit klar umrissener Aufgabe: `/context` lädt Arbeits-, Tages- und Kontextnotizen samt Backlinks (12:45), `/today` baut aus Kalender, Aufgaben, iMessage und den Tagesnotizen der letzten Woche einen priorisierten Tagesplan (13:40), `/closeday` zieht offene Aufgaben heraus und fragt nach zu aktualisierenden Confidence-Markern (14:30). Die Befehle schreibt er nicht selbst, sondern bittet Claude Code, sie zu erstellen (17:50).

5. **Befehle zur Selbstprüfung.** `/challenge` prüft aktuelle Überzeugungen gegen die eigene Vault-Historie (15:35), `/drift` vergleicht erklärte Absichten mit dem Verhalten der letzten 30 bis 60 Tage (16:30), `/emerge` sucht Schlüsse, die aus verstreuten Notizen folgen, aber nie formuliert wurden (16:00), `/trace` zeichnet nach, wie sich eine Idee entwickelt hat (17:05). Voraussetzung: genug datierte Tagesnotizen. Der gezeigte `/trace`-Lauf deckt 13 Monate ab (19:15).

6. **Confidence Ratings für eigene Hypothesen.** Vin vergibt für Ideen im Vault eine Einschätzung, wie gefestigt sie sind (14:40). Der Abendbefehl erinnert daran, diese Werte nachzuziehen. So kann der Agent gefestigte Annahmen von Arbeitshypothesen unterscheiden.

7. **Strikte Schreibtrennung zwischen Mensch und Agent.** Agenten legen keine Dateien im Vault an. Vorschläge erscheinen im Terminal, Vin übernimmt sie in eigenen Worten (33:20). Zweck laut Vin: Der Vault bleibt ein Abbild seines Denkens, nicht des Modells.

8. **Kalenderentscheidung mit Notizabgleich.** `/schedule` prüft eine Terminanfrage gegen Kalender und Tagesnotizen und empfahl in der Demo eine Absage für 14 Uhr wegen Auslastung (25:55).

9. **Meeting-Notizen in Projektordner.** Notizen aus Granola werden in den passenden Projektordner gelegt und getaggt, damit Agenten sie im Projektkontext finden (32:20). Für Kernprojekte pflegt Vin ausführliche Kontextdateien mit Format, Kernüberzeugungen, Team und jüngsten Änderungen (37:15).

10. **Den Agenten nach dem nächsten Befehl fragen.** Statt Einzelaufgaben zu stellen, lässt Vin das Modell anhand des Vaults einschätzen, wo er steht, und Befehle für die nächste Stufe vorschlagen (47:40). Aus dem Vorschlag `/graduate` (Ideen aus Tagesnotizen finden, dann entscheiden: eigene Notiz, an bestehende Datei anhängen oder verwerfen) wird per „create it“ ein lauffähiger Befehl (43:15, 49:15).

11. **Vault als einzige Quelle für alle Agenten.** Vin pflegt nur noch den Vault und lässt Agenten wie OpenClaw daraus lesen (27:15). Als Erweiterung nennt er einen Team-Vault, den alle befüllen und abfragen (43:50), sowie Aufgaben, die direkt in der Tagesnotiz stehen und von einem Agenten ausgeführt werden (44:40). Beides ist Idee bzw. Vorschlag aus dem Ideen-Report, nicht als laufender Betrieb gezeigt.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 13 Monate | Zeitraum der `/trace`-Analyse, Januar 2025 bis Januar 2026 (19:15) | Eigene Daten, Demo |
| 30 bis 60 Tage | Vergleichsfenster des Befehls `/drift` (16:30) | Eigene Daten, Befehlsbeschreibung |
| 30 Tage | Scan-Fenster des Befehls `/ideas` (16:40) | Eigene Daten, Befehlsbeschreibung |
| über 5 Minuten | Laufzeit einer Anfrage über einen großen Vault mit der Obsidian CLI (36:00) | Eigene Daten, Beobachtung in der Demo |
| 99,99 % | Anteil der Menschen, die so ein System laut Greg Isenberg nicht aufbauen werden (55:00) | Behauptung ohne Beleg |

## Wortlaute
- „make a file on my desktop that says hello Greg in plain text“ (02:31). Einstiegsbeispiel für Dateisteuerung per natürlicher Sprache.
- „Load full context about my life, work, and current state, reads context files, daily notes and follows back links to build a complete picture.“ (12:45). Beschreibung von `/context`.
- „morning review, pulls calendar, tasks, iMessages and the past week of daily notes into a prioritized plan for the day.“ (13:40). Beschreibung von `/today`.
- „pressure tests current beliefs using the Vault's own history, finds contradictions, counter evidence and shifts in thinking.“ (15:35). Beschreibung von `/challenge`.
- „It compares my stated intentions against actual behavior over 30 to 60 days. Surfaces what I am avoiding.“ (16:30). Beschreibung von `/drift`.
- „Surface ideas the vault implies but never states, conclusions from scattered premises, unnamed patterns, unarticulated directions.“ (16:00). Beschreibung von `/emerge`.
- „Build a command that scans recent daily notes, identifies ideas tagged or not and prompts you to decide: Create a standalone note, add to an existing file, or dismiss.“ (43:15). Vom Modell vorgeschlagener Befehl `/graduate`.
- „suggest the kinds of commands I should use that would take me from the level I'm at, to a higher level.“ (47:40). Meta-Prompt für die Weiterentwicklung des eigenen Systems.

## Grenzen und Widerspruch
- **Einzelfall.** Alles stammt aus dem Vault einer Person mit ausgeprägter Schreibgewohnheit. Es gibt keine Messung, ob Planung, Entscheidungen oder Output besser werden. Für B2B-Teams ist nichts belegt; der Team-Vault bleibt eine Überlegung.
- **Datenschutz fehlt.** Agenten wie OpenClaw bekommen Lesezugriff auf private Notizen, iMessages und Kalender. Wie sensible Inhalte geschützt werden und welche Daten an das Modell gehen, wird nicht besprochen. Für Firmendaten ist das vor einem Einsatz zu klären.
- **Kein Code.** Die Befehle werden nur im Terminal vorgeführt. Wie sie aufgebaut sind, sieht man nicht; Nachbauen heißt, sie selbst von Claude Code erzeugen zu lassen und zu prüfen.
- **Aufwand unbeziffert.** Der tägliche Pflegeaufwand für Verlinkung, Kontextdateien und Confidence Ratings wird erwähnt, aber nicht gemessen. Ohne regelmäßiges Schreiben liefern `/drift`, `/trace` oder `/emerge` wenig.
- **Laufzeit.** Bei großen Vaults dauern Anfragen mehrere Minuten (36:00).
- **Zugespitzte Thesen.** Die Aussage, ohne zentrales Markdown-Notizsystem nutze man LLMs nicht richtig (51:30), und der Verweis auf Studien zum fehlerhaften menschlichen Gedächtnis (52:45) bleiben ohne Quelle. Die 99,99 % sind eine Pointe, keine Zahl.
- **Web-Memory-Vergleich.** Die Kritik, man wisse nicht, was im Speicher von Web-Chatbots steht (03:48), ist eine Einschätzung des Sprechers, kein getesteter Vergleich.
