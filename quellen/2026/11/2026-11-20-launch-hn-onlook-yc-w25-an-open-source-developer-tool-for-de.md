# Launch HN: Onlook (YC W25), ein Open-Source-Entwicklerwerkzeug für Designer

> **Quelle:** [Launch HN: Onlook (YC W25) – An open-source developer tool for designers](https://github.com/onlook-dev/onlook/) · Onlook-Team (GitHub-README) und Hacker-News-Kommentierende, Onlook (YC W25) · Diskussion ([HN-Thread](https://news.ycombinator.com/item?id=50562320)) · 2026-11-20
> **Sprecher verkauft:** kostenlose Open-Source-Desktop-App (Electron) zum visuellen Bearbeiten echter Web-Apps, die Pricing-Seite deutet zusätzlich ein Bezahlmodell an · **Zielmarkt der Aussagen:** Designer, Visual Engineers und Frontend-Teams, die mit echtem Code statt Mockups arbeiten · **Beweislage:** Produktaussagen sind Herstellerangaben aus dem README, die Einwände sind Einzelstimmen, Antworten der Gründer fehlen.

## Worum es geht
Wie können Designer an der laufenden, echten App arbeiten, statt Mockups zu bauen, die später jemand nachprogrammiert? Onlook beantwortet das mit einer lokalen Canvas, auf der die App läuft, und einem fremden Coding-Agenten (Claude Code oder ChatGPT/Codex), der die Dateien ändert. Die HN-Diskussion zeigt, welche Fragen Entwickler und Designer bei so einem Werkzeug zuerst stellen.

## Was man anwenden kann
1. **Bring your own agent als Produktprinzip.** Onlook liefert kein eigenes Modell. Nutzer verbinden ihr bestehendes Claude-Code- oder ChatGPT/Codex-Abo, Modellkosten und Limits laufen über dieses Abo. Weitere Kontexte kommen über MCP-Konnektoren dazu. Wer ein ähnliches Werkzeug baut, spart so Inferenzkosten, muss dieses Prinzip aber prominent erklären (siehe Punkt 7).
2. **Am echten Repo arbeiten statt am Mockup.** Onlook öffnet ein beliebiges lokales Git-Repository und startet dessen eigenen Dev-Server über node-pty. Änderungen erscheinen per Reload, Git protokolliert alles. Bedingung: Das Projekt muss lokal über einen Dev-Server laufen. Eine Liste getesteter Frameworks gibt es nicht.
3. **Arbeitskopie per Worktree absichern.** Laut README arbeitet der Agent in einer Worktree-Kopie, der ursprüngliche Projektordner bleibt unberührt. Parallele Projekte laufen als Tabs, mehrere Design-Aufgaben parallel über Repos und Seiten. Das Muster lässt sich auf jedes Agent-Setup übertragen, das auf fremden Code losgelassen wird.
4. **Ablauf in sechs Schritten.** Repo öffnen oder importieren, Dev-Server startet, App erscheint in Frames auf der Canvas (Mobile, Tablet, Desktop nebeneinander), Wunsch im Chat formulieren, verbundener Agent editiert die Dateien, Export als HTML, PNG, JPEG oder PDF. Für gezielte Änderungen ein Element doppelklicken und den Inline-Chat nutzen, oder Frames als Kontext für Folgeprompts anklicken.
5. **Teilen über Artifacts.** Frame auswählen, den Agenten bitten, daraus ein „Artifact“ zu machen, dann über den Export-Button oben rechts als HTML/CSS oder PNG exportieren und in Slack oder E-Mail einfügen. Artifacts dienen auch als schnelle HTML-Skizzen außerhalb des Repos.
6. **Vor Einsatz Telemetrie und Plattform prüfen.** Produkt-Analytics sind im offiziellen Download standardmäßig an, der Source-Build fragt vorher. Abschalten in den Einstellungen oder mit `STUDIO_TELEMETRY=0` beim Ausführen oder Bauen. Offiziell gibt es nur macOS (Apple Silicon, Intel x64). Windows steht auf Warteliste, für Linux gibt es kein Artefakt. Teams mit Souveränitätsanforderungen sollten den Source-Build nutzen, der laut README ohne Onlook-Account, Cloud-Keys und `.env`-Datei auskommt.
7. **Die erste Kauffrage im README beantworten.** Ein Kommentator suchte zuerst, ob Onlook mit dem eigenen Claude-Code- oder Codex-Abo läuft, und fand es nicht. Ein anderer fragte trotzdem, ob nur die Claude-Code-API unterstützt wird. Für GTM bei Entwicklerwerkzeugen heißt das: Kostenmodell und unterstützte Agenten in den ersten Zeilen nennen, Pricing in die Navigation statt in den Footer.
8. **Lizenz beim Fork sauber trennen.** Code steht unter Apache 2.0, Icons (Central Icons von Iconists), Brand-Marken, DMG-Grafik und Sounds sind ausgenommen. Wer forkt und vertreibt, muss diese laut ASSETS.md ersetzen. Interne Nutzung des Quellcodes ist davon nicht betroffen.
9. **Repo für Agenten dokumentieren.** Das Repository enthält AGENTS.md, CLAUDE.md, CODING.md, ANTIPATTERNS.md, GLOSSARY.md und WRITING.md sowie Tooling wie gitleaks, knip, oxlint, Playwright. Das ist eine brauchbare Vorlage für Projekte, die überwiegend mit Coding-Agenten entwickelt werden.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 27,4k Stars, 2,2k Forks, 121 Watcher | GitHub-Repository zum Erfassungszeitpunkt | eigene Daten, kein Nutzungsnachweis |
| 1.645 Commits | main-Branch | eigene Daten |
| 87 Punkte, 68 Kommentare | HN-Beitrag | eigene Daten |
| 6 Schritte | beschriebener Arbeitsablauf | Herstellerangabe |

## Wortlaute
Textquelle ohne Zeitstempel.
- „We don't ship our own model. Connect the Claude Code or ChatGPT/Codex account you already have“ (README). Klare Formulierung des Bring-your-own-agent-Prinzips.
- „what you design is your actual product, not a mockup“ (README). Kernversprechen gegen klassische Design-Tools.
- „An open-source alternative to Figma, V0, Replit Agent, Base 44, Webflow, etc.“ (README). Wettbewerbsrahmung ohne Vergleichsdaten.
- „Did you agent also recommend this copy??? Fire it! :)“ (threecheese). Reaktion auf die Superlativ-Beschreibungszeile des Repos, ein Beispiel dafür, wie unbelegte Superlative bei Entwicklern ankommen.

## Grenzen und Widerspruch
- **Keine Gründer-Antworten im Material.** Fragen zur Abgrenzung von pen.dev, Paper, Figma, Claude Code Design und Codex bleiben offen. Joshearle1 gestaltet schon fast alles direkt in Codex und will ein konkretes Beispiel, wo Onlook nach dem ersten Entwurf besser ist.
- **Geschäftsmodell unklar.** README nennt den Editor kostenlos, eine Pricing-Seite existiert. Wie Onlook Umsatz macht, wenn die Agenten über fremde Abos laufen, beantwortet das Material nicht.
- **Local-first mit Abstrichen.** Telemetrie ist im Download standardmäßig an. dvsk berichtet von unklarem Account-Zwang im Onboarding und von hängenden Bildschirmen oder der Meldung „Can't verify the user is human“ bei der E-Mail-Registrierung (macOS 27.2.1). Die Aussage „kein Account“ gilt laut README nur für den Source-Build.
- **Keine offenen Modelle.** Genannt sind nur Claude Code und ChatGPT/Codex. thiagoperes würde Onlook vor allem mit offenen Modellen nutzen, um Abo-Limits zu schonen. Für Open-Weight- oder souveräne Setups ist das eine Lücke.
- **Variantenkombination ungelöst.** HetengAaronLi fragt, wie man Navigation aus Version 3, Layout aus Version 7 und Interaktionen aus Version 9 zusammenführt. Über Worktrees ist das ein Code-Integrationsproblem.
- **Gleichförmige KI-Designs.** husseinhb sieht Layer- und z-index-Fehler heute als selten, das Hauptproblem sei fehlende Kreativität, weil KI-Designs gleich aussehen. Ob Onlook daran etwas ändert, bleibt offen.
- **Figma-Bestand.** farukparhat hat Kunden, die bei Figma bleiben, und fragt nach dem Unterschied zu Figmas neuen Funktionen.
- **Keine Qualitätsmessung.** Es gibt keine Nutzerzahlen, Kundenfälle oder Messwerte zur Qualität der Agent-Ergebnisse. Positive Kommentare loben Demo und Open Source, ohne Ergebnisse zu nennen.
