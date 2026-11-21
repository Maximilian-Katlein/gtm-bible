# Ich habe eine Privatstunde zu Claude Cowork und Claude Code bekommen

> **Quelle:** [I got a private lesson on Claude Cowork & Claude Code](https://www.youtube.com/watch?v=DW4a1Cm8nG4) · Boris (Entwicklung von Claude Code, Anthropic) im Gespräch mit Greg Isenberg (Startup Ideas Podcast) · Video · 2026-11-19
> **Sprecher verkauft:** Claude Cowork, Claude Code, Claude Agent SDK und Claude Opus 4.5, alles Produkte von Anthropic, vorgestellt von deren Entwickler · **Zielmarkt der Aussagen:** unklar, Einzelanwender und Teams, Entwickler und Nicht-Techniker, kein Segment benannt · **Beweislage:** Herstellerdemo und Anekdoten, keine Messdaten, Kosten oder Vergleichstests.

## Worum es geht
Wie setzt man Claude Cowork und Claude Code im Arbeitsalltag so ein, dass sie Routinearbeit wirklich abnehmen? Der erste Teil zeigt Cowork für Nicht-Techniker per Live-Demo, der zweite geht die Claude-Code-Arbeitsweise von Boris anhand eines viral gegangenen X-Posts durch. Die Aufnahme stammt von Januar 2026. Produktstände, Plattformen und Modellempfehlungen sind vor der Übernahme zu prüfen.

## Was man anwenden kann
1. **Mit einem freigegebenen Ordner anfangen.** Cowork sieht standardmäßig keine Dateien, jeder Ordner wird einzeln freigegeben (06:06). Boris empfiehlt als Einstieg genau das: einen Ordner einbinden und eine Aufräumaufgabe stellen, etwa Belege nach Datum umbenennen (06:16, 07:22). In der Demo prüft Boris das Ergebnis danach von Hand im Ordner. Stand Januar 2026 nur auf macOS.

2. **Rückfragen als Teil des Ablaufs einplanen.** Fehlt eine Information, fragt das Modell nach, statt zu raten. Boris nennt das „reverse elicitation“ (08:00). In der Demo fehlte auf einem Beleg das Datum, Cowork hielt an und fragte, wie damit umzugehen sei (07:45). Wer Aufgaben anstößt, muss also erreichbar bleiben oder Sonderfälle vorab im Prompt regeln.

3. **Browserzugriff pro Seite freigeben.** Für Browseraufgaben braucht Cowork einen Chromium-Browser und die Chrome-Erweiterung (07:04, 23:20). Jede Seite fragt um Erlaubnis: „always allow for the site“, „allow once“ oder „deny“ (11:00). Boris wählt „always allow“ nur für die Demo. Für den Alltag ist „allow once“ die vorsichtigere Wahl, zumal Prompt Injection laut Boris ein reales und nicht vollständig gelöstes Risiko ist (09:59).

4. **Mühsame Routinen auflisten und abgeben.** Greg schlägt ein Audit vor: Welche Aufgaben fallen an, wie wird mit Dateien, Internet und Versand gearbeitet, wo liegt Produktivitätspotenzial (14:47). Boris’ eigenes Beispiel: Eine Team-Tabelle mit Wochen- oder Monatsplanung prüfen lassen und jeden Engineer mit leerer Spalte per Slack anschreiben, einige Male pro Woche (18:55). Voraussetzung ist eine Slack-Anbindung und eine gemeinsame Statustabelle.

5. **Parallel arbeiten statt zuschauen.** Computer Use ist langsam, das räumt Boris ein (11:15). Die Antwort darauf: weitere Aufgaben starten, während eine läuft, zwischen ihnen wechseln und Rückfragen beantworten (14:43, 17:33). Der Zeitgewinn entsteht nur, wenn sich Aufgaben tatsächlich parallelisieren lassen. Einzelaufgaben erledigt man selbst laut Boris oft schneller.

6. **Cowork nicht vorab überkonfigurieren.** Cowork plus Chrome-Erweiterung reiche weitgehend (23:20). Eigene Skills, also wiederholbare Anleitungen für ein Format oder Tool, lohnen sich erst, wenn Cowork in einer bestimmten Software schwach ist, etwa AutoCAD oder Salesforce (21:19, 23:31). Für Excel liefert Anthropic einen Skill mit. Wie man einen Skill schreibt, zeigt das Video nicht.

7. **In Claude Code mit Plan Mode starten.** Die meisten Sessions von Boris beginnen im Plan Mode. Man geht mit Claude hin und her, bis der Plan stimmt, und wechselt dann auf „auto accept edits“. Laut Boris klappt der Pull Request dann meist in einem Durchgang (37:55). Boris knüpft das ausdrücklich an Opus 4.5, frühere Modelle hätten Pläne weniger zuverlässig umgesetzt (30:48).

8. **Sessions staffeln.** Ablauf laut Tipp 1: Task in Tab 1 starten, während Claude plant zu Tab 2 wechseln und dort einen Plan anfordern, dann Tab 3, danach zurück zu Tab 1 und den Plan prüfen (30:48). Jeder Terminal-Tab hat bei Boris einen eigenen Git Checkout, Worktrees nutzt Boris bewusst nicht (33:01). Dazu laufen fünf bis zehn Sessions im Web, einige werden morgens per iOS-App gestartet (31:54, 32:49).

9. **Eine gemeinsame CLAUDE.md im Repo pflegen.** Das Claude-Code-Team checkt eine CLAUDE.md in Git ein. Macht Claude etwas falsch, kommt eine Zeile dazu, das ganze Team ergänzt mehrmals pro Woche (34:42). Es gibt kein Pflichtformat, es ist eine Textdatei (35:02). Bei schlechten Ergebnissen ist sie die erste Stelle zum Nachbessern (33:38).

10. **Review-Wissen per @claude festhalten.** Nach Installation der Claude Code GitHub Action per Slash-Command im Terminal (genauer Befehl im Untertitel unklar) kann man @claude in PRs und Issues erwähnen. Claude pusht Änderungen zurück auf den Branch (36:05). Boris nutzt das mehrmals täglich, um die CLAUDE.md im Rahmen von Kollegen-PRs zu ergänzen (35:22). Dahinter steht eine ältere Methode aus der Zeit bei Meta: Review-Kommentare in einer Tabelle zählen und ab etwa fünf bis zehn Wiederholungen eine Lint-Regel schreiben (36:58).

11. **Claude die eigene Arbeit prüfen lassen.** Der wichtigste Hebel laut Tipp 13: Claude braucht einen Weg, die Ausgabe zu verifizieren, etwa Tests ausführen, Server starten, Ergebnis im Browser oder Simulator ansehen (39:14). Beim App-Bau nutzt Boris dafür die Chrome-Erweiterung. Zusammen mit Modellwahl und CLAUDE.md nennt Boris das die drei Dinge, die fast immer helfen (38:52).

12. **Modellwahl nach Gesamtkosten statt Tokenpreis.** Boris nutzt Opus 4.5 mit Thinking für alles und behauptet, das größere Modell brauche weniger Steuerung und weniger Tokens und sei deshalb oft schneller und günstiger als ein kleineres (34:10). Belege fehlen. Prüfbar ist der Gedanke trotzdem: Kosten und Dauer pro erledigter Aufgabe messen, nicht pro Token. Das genannte Modell ist zum Erfassungszeitpunkt vermutlich überholt.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 99 Prozent | Anteil der Menschen, die man mit Cowork-Kenntnis „übertreffen“ könne (00:03) | Behauptung ohne Beleg, Host |
| Hälfte | Anteil des GTM-Teams (Sales) bei Anthropic, das Claude Code wöchentlich nutzt (20:08) | Behauptung ohne Beleg, interne Angabe ohne Messmethode |
| fast alle, täglich | Designer, PMs und Data Scientists bei Anthropic (20:08) | Behauptung ohne Beleg |
| ein Mehrfaches | Wachstum von Cowork in Woche 1 gegenüber Claude Code in dessen Woche 1 (24:13) | Herstellerangabe ohne Absolutwerte |
| 100 Prozent | Anteil des eigenen Codes, den Claude Code in den letzten zwei Monaten schrieb (25:35) | Anekdote |
| 200 bis 300 | PRs pro Monat bei Boris, Untertitel unklar („two 300“) (25:35) | Anekdote, Zahl unsicher |
| 5 bis 10 | parallele Web-Sessions zusätzlich zu lokalen Sessions (31:54) | Anekdote |
| etwa die Hälfte | Anteil des Codes, den Boris vom Handy aus anstößt (32:49) | Anekdote, Schätzung |
| ca. 99.000 | Bookmarks auf Boris’ X-Post mit 13 Tipps (29:22) | Angabe des Hosts |
| 5 bis 10 | Wiederholungen eines Review-Kommentars, ab denen Boris bei Meta eine Lint-Regel schrieb (36:58) | Anekdote |

## Wortlaute
- „I have a receipts folder. Can you rename the files to match the dates on the receipts?“ (06:16) Einstiegsprompt für Dateiarbeit nach Ordnerfreigabe.
- „can you open Gmail and send the sheet to Amy?“ (16:00) Browseraufgabe mit Versand. In der Demo meldet Cowork einen gespeicherten Entwurf, der Versand selbst ist nicht zu sehen.
- „any column that's not filled out, just message the engineer on Slack“ (18:55) Wiederkehrende Statusnachfrage im Team.
- „Anytime we see Claude do something incorrectly, we add it to the MD so Claude knows not to do it next time.“ (34:42) Pflegeregel für die gemeinsame CLAUDE.md.
- „If [Claude] can verify its own output, the result is going to be way way better.“ (39:14) Leitsatz für Verifikation, Untertitel-Fehler korrigiert.

## Grenzen und Widerspruch
- **Verkaufssituation:** Der Entwickler demonstriert die eigenen Produkte. Alle Leistungsaussagen (bessere Ergebnisse, günstigeres Opus, schnelleres Wachstum) kommen ohne Messdaten, Vergleichstests oder Kosten pro Aufgabe.
- **Keine Preise:** Abo-Stufen, Nutzungslimits und Tokenkosten von Cowork fehlen vollständig.
- **Kaum GTM-Substanz:** Außer Slack-Nachfrage, Belege umbenennen und einem Mail-Entwurf gibt es keine ausgearbeiteten Vertriebs- oder Marketingprozesse, keine Zeitersparnis in Zahlen, keine Kundenfälle. Die GTM-Nutzungszahl betrifft Anthropic selbst, ein Unternehmen mit maximaler KI-Affinität.
- **Datenschutz und Souveränität fehlen:** Datenresidenz, EU-Betrieb, Unternehmenskontrolle und die Frage, welche Inhalte aus lokalen Dateien und Browsersitzungen bei Anthropic landen, werden nicht behandelt. Cowork läuft nur auf Anthropic-Modellen, offene oder souveräne Alternativen kommen nicht vor.
- **Sicherheit bleibt abstrakt:** Virtuelle Maschine, Löschschutz und Prompt-Injection-Schutz werden genannt, nicht gezeigt. Den Injection-Schutz nennt Boris selbst „not perfect“ (09:59).
- **Demo mit Fehlern:** Computer Use ist langsam, beim Einfügen ins Google Sheet landeten Daten in falschen Spalten, Cowork korrigierte nach (12:42).
- **Ungelöst laut Boris:** ereignisgesteuerte Automatisierung („jedes Mal wenn X, tu Y“) gibt es in Cowork noch nicht (20:58).
- **Veraltet:** Stand Januar 2026. „Nur macOS“, Opus 4.5 als Empfehlung und der Funktionsumfang sind im November 2026 vermutlich überholt.
- **Unvollständig:** Von den 13 Tipps werden nur 1 bis 6 und 13 besprochen, der Inhalt der gezeigten CLAUDE.md wird nicht vorgelesen. Der Untertitel enthält Fehler bei Namen, Befehlen und Zahlen.
- **Prognosen ohne Gewicht:** Gregs Erwartung vertikaler Cowork-Varianten (27:38) kommentiert Boris mit „keine Ahnung“. Auch die Planung auf Wochenbasis wegen exponentieller Modellverbesserung (25:56) ist eine Haltung, kein Befund.
