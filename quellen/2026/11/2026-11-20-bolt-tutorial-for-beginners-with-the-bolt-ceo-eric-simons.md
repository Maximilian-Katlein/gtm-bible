# Bolt-Tutorial für Einsteiger mit Bolt-CEO Eric Simons

> **Quelle:** [Bolt tutorial for beginners with the Bolt CEO Eric Simons](https://www.youtube.com/watch?v=1SfUMQ1yTY8) · Eric Simons (CEO, StackBlitz) im Gespräch mit Greg Isenberg (Host) · Video · 2026-11-20
> **Sprecher verkauft:** Bolt (bolt.new), einen KI-Agenten im Browser, der aus Textprompts Web-Apps baut und über Netlify hostet; genannt wird ein Plan für 50 $ pro Monat. Greg schaltet zwei Werbeblöcke und ist laut eigener Aussage in boring marketing investiert. · **Zielmarkt der Aussagen:** Indie Hacker, Bootstrapped Founder, Nicht-Entwickler; vereinzelt YC-Startups für Landing Pages · **Beweislage:** Live-Demo mit offen gezeigten Fehlern, alle Erfolgszahlen sind Anekdoten oder Behauptungen des Herstellers.

## Worum es geht
Wie baut eine Person ohne Engineering-Hintergrund mit Bolt in unter einer Stunde eine lauffähige Web-App und stellt sie online? Die Demo zeigt ein Produktverzeichnis für Indie Hacker, das zuerst Ranking und Upvotes und danach einen Echtzeit-Chat mit Firebase bekommt. Die Tipps gelten für den Produktstand rund einen Monat nach dem Launch von Bolt (01:38); das Aufnahmedatum wird nicht genannt.

## Was man anwenden kann
1. **Ersten Prompt in zwei Absätzen bauen.** Absatz eins beschreibt Zielgruppe, Zweck und Stimmung, Absatz zwei die konkreten Funktionen (09:24). Eric erwartet, dass Bolt dadurch auch Name, Beschreibungen und CTAs als passende Marketing-Texte erzeugt. In der Demo trifft der Text das Thema, der exakte Prompt ist nicht hörbar.
2. **Den Vibe in einem Satz benennen.** Eric beschreibt das Ziel „fast auf spiritueller Ebene“ und ergänzt erst dann Funktionen (07:07). Für seine eigene Website verlangte er nur Ästhetik und Stimmung eines Software-Entwicklers. Beleg ist eine Anekdote.
3. **Bei Fehlstart neu beginnen statt reparieren.** Liegt die erste Antwort weit daneben, geht Eric zurück zur Startseite und schreibt einen neuen Prompt (09:09). Innerhalb des Chats rollt der Undo-Button auf den letzten Checkpoint zurück (15:18).
4. **Funktionsänderungen in kleine Prompts zerlegen.** Verlangt man viele Dinge auf einmal und eines geht schief, verliert ein Rollback auch die richtigen Teile, und man muss den Code selbst anpassen (15:41). Regel aus der Demo: bei Funktionen nur das absolute Minimum verlangen, testen, dann erweitern (41:42). Design-Wünsche darf man dagegen als Liste in einer Nachricht sammeln (18:40).
5. **Fehlermeldungen in den Chat kopieren.** Bei Kompilier- oder Laufzeitfehlern die Meldung einfügen, Bolt erzeugt die Datei neu; für manche Fehler gibt es einen Button „fix errors“ (11:48). Gezeigter Fall: ein nicht escaptes Anführungszeichen, das Bolt nicht selbst abfing (12:02).
6. **Screenshot als Design-Vorlage.** Einen Screenshot einer Seite anhängen und sagen, Farben und Vibe sollen auf die eigene Seite übertragen werden (19:13, 20:34). In der Demo übernahm Bolt die Farbpalette von Gregs Agentur-Seite und ergänzte Icons.
7. **Backend-Anbieter im Prompt festlegen.** Eric empfiehlt, explizit Firebase oder Supabase zu nennen, weil Authentifizierung, Echtzeit-Speicherung und Synchronisation mit Bolt am besten funktionieren (32:06). Der Chat-Prompt selbst blieb bewusst kurz, nur ergänzt um „Firebase verwenden“ (31:14).
8. **Firebase in fünf Schritten anbinden.** Projekt anlegen, Google Analytics überspringen, unter „Build“ eine Realtime Database im Test-Modus erstellen (35:17). Die Web-Konfiguration findet man erst nach Anlegen einer Web-App unter Project settings, „Your apps“; den Config-Block in die Firebase-Datei in Bolt kopieren, denn Bolt hinterlässt Platzhalter (36:31, 39:09).
9. **Auf den richtigen Datenbanktyp achten.** Nachrichten verschwanden nach dem Neuladen, weil der Code in Firestore schrieb, angelegt war aber die Realtime Database (42:55). Firebase hat zwei Datenbankprodukte; prüfen, welches der generierte Code nutzt.
10. **Deploy mit einem Klick.** „Deploy“ oben rechts baut die App im Browser und lädt sie ohne Anmeldung zu Netlify hoch; danach lässt sich in Netlify eine eigene Domain verknüpfen (24:00, 26:21).
11. **Verzeichnis als Traffic-Einstieg (Gregs These).** Hauptseite mit wenigen Produkten, etwa den fünf des Tages, plus je Produkt eine Detailseite als zusätzliche SEO-Seite (08:01); später Monetarisierung über Affiliate-Deals mit den gelisteten Produkten (08:24). Weder Traffic noch Einnahmen werden belegt.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| ca. 1 Monat | Zeit seit dem Bolt-Launch zur Aufnahme | Herstellerangabe |
| ca. 5 Minuten | Bis zum ersten Verzeichnis mit Karten und Detailseiten | eigene Demo |
| 50 $ pro Monat | Bolt-Plan, den die Viral-Hooks-Gründerin nutzte | Herstellerangabe |
| 3.000 bis 5.000 $, mehrere Monate | Upwork-Angebote für die App Viral Hooks | Kundenfall, mündlich |
| 1,5 bis 2 Wochen | Bauzeit von Viral Hooks mit Bolt | Kundenfall, mündlich |
| „ein Hundertstel der Kosten“, 5 bis 10 mal schneller | Erics Verhältnisrechnung dazu; vergleicht ein Angebot mit einem Monatsabo | Behauptung ohne Beleg |
| ca. 30 Minuten | Marketing-Website eines befreundeten YC-Startups | Anekdote |
| mindestens ein Dutzend | Personen mit erstem Kunden aus Bolt-Projekten | Behauptung ohne Beleg |
| über tausend | Nutzer, die nach der Firebase-Anbindung gefragt hätten | Behauptung ohne Beleg |
| 7 Jahre | Zeit, die StackBlitz an Web-IDEs im Browser baut | Herstellerangabe |

## Wortlaute
- „show in a very obvious way which products are number one number two number three Etc and let the user upvote products“ (14:36). Zweiter Prompt: Ranking und Upvotes in einem klar abgegrenzten Schritt.
- „attached is a beautiful site the colors are amazing very unique maybe you can capture the vibe into a product list site“ (20:34). Prompt zur Screenshot-Vorlage; Wortlaut im Transkript teils unsicher.
- „we want to add a live chat page to this site for Indie hackers to … in real time communicate with one another“ (31:14). Kurz gehaltener Funktionsprompt, danach nur die Anbieterwahl.
- „make it beautiful like use gradients like make it pop“ (18:40). Vage, aber stimmungsbezogene Design-Anweisung, die Bolt laut Eric aufgreift.

## Grenzen und Widerspruch
- **Werbung des Herstellers.** Der CEO zeigt das eigene Produkt. Es gibt keine Messwerte zu Nutzung, Retention oder Kosten pro Projekt in Credits. Der Hundertstel-Vergleich stellt ein Entwickler-Angebot einem Monatsabo gegenüber, Nacharbeit und Folgekosten fehlen.
- **Zielgruppe Creator, nicht B2B-Teams.** Belegt ist der Nutzen nur für Solo-Gründer, Micro-SaaS und Landing Pages. Für große oder alte Codebasen verweist Eric selbst auf Cursor (30:08); StackBlitz baut den Bolt-Code intern mit Cursor (27:15).
- **Sicherheit fehlt in der Demo.** Der Chat läuft im Firebase-Test-Modus ohne Anmeldung; das Login-Popup wurde im Preview blockiert und die Anmeldepflicht entfernt (40:22). Zugriffsregeln, Moderation und Missbrauchsschutz werden nur erwähnt (35:36). Upvotes liegen vermutlich nur im Speicher (17:10).
- **Unbegrenzte Upvotes.** Greg hält sie für ein Lebendigkeitssignal (17:42). Dass das Fake-Zahlen erzeugt und Vertrauen kosten kann, wird nicht diskutiert.
- **Verzeichnis-These unbelegt.** Keine Strategie zum Befüllen mit echten Produkten, keine Rankings, keine Affiliate-Zahlen; die gezeigten Inhalte sind KI-Platzhalter. Das Game-Mechanics-Framework Octalysis wird nur genannt.
- **KI fasst ungefragt Dateien an.** Bolt änderte wiederholt eine types-Datei (16:03) und legte eine .env-Datei an (45:09). File-Locking, Ein-Klick-Anbieter und der Fix für den vergessenen Dev-Server sind Ankündigungen ohne Datum.
- **Latenz.** Eric nennt Anthropic als KI-Anbieter von Bolt und vermutet ohne Insider-Wissen überlastete GPUs als Grund für langsamere Generierung (34:42).
- **Lückenhafte Aufnahme.** Prompts sind beim Tippen nur teilweise hörbar, Bildschirminhalte lagen nicht vor. Was nach dem Firestore-Fehler geändert wurde, bleibt offen.
