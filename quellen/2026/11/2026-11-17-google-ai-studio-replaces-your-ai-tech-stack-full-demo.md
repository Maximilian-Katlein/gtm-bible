# Google AI Studio ersetzt deinen KI-Tech-Stack (komplette Demo)

> **Quelle:** [Google AI studio replaces your AI tech stack (full demo)](https://www.youtube.com/watch?v=6h9y1rLem4c) · Logan Kilpatrick (Lead PM Google AI Studio), Greg Isenberg (Host, Startup Ideas Podcast) · Video · 2026-11-17
> **Sprecher verkauft:** Logan Kilpatrick: Gemini-Modelle und Gemini API, Einstieg über das kostenlose AI Studio, später ein bezahlter Produktionspfad. Greg Isenberg: Mitgliedschaft Startup Empire. · **Zielmarkt der Aussagen:** unklar, Entwickler und angehende Gründer, kein definierter B2B-Käufer · **Beweislage:** Produktdemo des Herstellers, Ergebnisse kaum geprüft, keine Preise und keine Vergleiche.

## Worum es geht
Was kann man im kostenlosen Google AI Studio mit Gemini ausprobieren, ohne eigenen Tech-Stack aufzubauen? Der Produktverantwortliche von Google zeigt lange Videoeingaben, ein Reasoning-Modell, Objekterkennung, Function Calling und einen Echtzeit-Assistenten mit Bildschirmfreigabe. Die Folge richtet sich an Entwickler und Gründer, die Prototypen bauen wollen. Sie ist eine Herstellerdemo, kein Test.

## Was man anwenden kann
1. **Lange Videos direkt als Eingabe testen.** Im Eingabefeld über das Plus-Symbol unten rechts „Sample Media“ wählen und ein Video einfügen. Gezeigt wird ein 30-Minuten-Rundgang durch ein Naturkundemuseum mit der Bitte, alle Exponate aufzulisten (03:49). AI Studio zeigt dafür rund 531.000 Tokens an (04:53). Das Ergebnis wird nicht geprüft. Logan Kilpatrick sagt selbst, jemand müsse kontrollieren, ob das Modell halluziniert (05:45).

2. **Kostenloses Reasoning-Modell in Cursor nutzen.** In AI Studio „Get API key“ klicken, neuen Key erzeugen, in Cursor über die Funktion für eigene API-Keys eintragen (12:44). Laut Logan Kilpatrick gilt das für alle Gemini-Modelle. Rate Limits im Free Tier werden nicht genannt, also vor ernsthafter Nutzung selbst prüfen.

3. **Modellwahl nach Kosten und Limits.** 2.0 Flash ist etwas leistungsfähiger und etwas teurer als Flash Lite. Flash Lite hat höhere Rate Limits und schafft viele Kernaufgaben ebenso (07:34). Das Pro-Modell war zum Aufnahmezeitpunkt experimentell. Konkrete Preise fehlen, die Modellstände sind veraltet.

4. **Thoughts als Gliederung lesen, Lücken nachfordern.** Das Reasoning-Modell zeigt in AI Studio vor der Antwort seinen Plan: Struktur, Tech-Stack, Landingpage mit CTA, MVP mit Login und Dashboard (10:48). Über die API sind diese Gedanken laut Logan Kilpatrick nicht sichtbar (10:16). Fehlende Teile wie HTML und CSS fordert man per Folgeprompt nach (11:55). Ein Lauf dauerte 23 Sekunden (12:15). Der Code wurde nicht ausgeführt.

5. **Bounding Boxes für Objekterkennung.** Die Starter-App „Spatial Understanding“ fragt nach Positionen von Objekten und erhält 2D-Koordinaten, die als Overlay erscheinen (14:02). Genannte Anwendungen: Möbel im Raumfoto erkennen und per Bildsuche passende Produkte finden (B2C E-Commerce, nur Idee), Flächenauslastung im Lager oder Parkhaus aus Fotos oder Videofeeds (15:56). Die Lagerfirmen bleiben anonym, Ergebnisse fehlen.

6. **Function Calling als Produktidee.** Eine Starter-App verbindet Gemini mit der Google Maps API (18:18). Logan Kilpatricks These: Mehrere bestehende Produkte mit KI in der Mitte kombiniert ergeben neue Geschäfte bei deutlich weniger Aufwand als klassisches SaaS (19:09). Der Code der Starter-Apps liegt laut Demo auf GitHub, erreichbar oben rechts in AI Studio (19:38). Repository-Name und Lizenz werden nicht genannt.

7. **Echtzeit-Assistent mit Bildschirmfreigabe prototypen.** In AI Studio links „Stream Realtime“ öffnen, Bildschirm teilen und sprechen (28:01). Im Beispiel liest das Modell Fehlermeldungen vom Bildschirm und erkennt einen Platzhalter statt des echten API-Keys (21:42). Rechts lassen sich Function Calls, Code Execution in einer Python-Umgebung und Grounding über Websuche zuschalten (25:32). Diese Tools wurden live nicht genutzt.

8. **Gemma als offene Alternative im selben Werkzeug.** Neben Gemini lässt sich Gemma in AI Studio testen (07:17). Wer Selbsthosting oder Souveränität braucht, muss Lizenz und Modellgrößen anderswo klären, die Folge sagt dazu nichts.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 531.000 Tokens | 30-Minuten-Video in AI Studio (04:53), Zahl im Transkript leicht unsicher | in der Demo angezeigt |
| 23 Sekunden | Laufzeit einer Reasoning-Antwort, ein Lauf (12:15) | in der Demo angezeigt |
| 3 | Anzahl Starter-Apps, zwei davon gezeigt (13:26) | in der Demo angezeigt |
| rund 1,5 Mrd. Tokens | kostenloses API-Kontingent über mehrere Modelle, Zeitraum unklar (28:49) | Herstellerangabe |
| 1,5 bis 3 Mal schneller | Produktivität mit KI-Partner, der den Bildschirm sieht (24:52) | Schätzung des Hosts ohne Messung |
| 1 bis 20 Mio. USD Jahresumsatz | automatisierbare Service-Geschäfte (17:14) | Behauptung ohne Beleg |
| 80 bis 95 Prozent | „Reifegrad“ von Tools, rhetorisch (26:33) | nicht gemessen |

## Wortlaute
- „Take me somewhere in ancient history.“ (18:18) Prompt der Maps-Starter-App. Zeigt, wie knapp ein Prompt sein kann, wenn die Anwendung per Function Calling den Kontext liefert.
- „somebody should go and validate that all these things really exist and the model's not hallucinating“ (05:45) Der Hersteller selbst benennt die Prüfpflicht bei Extraktion aus langen Medien.
- „you don't have to have humans do that anymore“ (16:52) Greg Isenbergs Kernthese zu Agenturen und Beratungen als Startup-Feld.

## Grenzen und Widerspruch
- **Herstellerdemo.** Logan Kilpatrick verantwortet das Produkt. Greg Isenberg betont, nicht bezahlt worden zu sein (02:05), und bewirbt eigene Mitgliedschaften (06:14). Kritische Fragen zu Lock-in, Datenschutz oder Grenzen werden nicht gestellt.
- **Keine Preise, keine Limits.** Weder Rate Limits im Free Tier noch der Zeitraum der 1,5 Mrd. Tokens noch die Konditionen des bezahlten Produktionspfads werden genannt.
- **Datenschutz und Souveränität fehlen.** Ob Eingaben im Free Tier zum Training genutzt werden und wo Daten verarbeitet werden, bleibt offen. Bildschirmfreigabe an ein Cloud-Modell ist für europäische B2B-Umgebungen ohne Klärung dieser Punkte nicht einsetzbar.
- **Ergebnisse ungeprüft.** Museumsliste nicht validiert, generierter Code nicht ausgeführt, Prompt laut Sprecher unoptimiert und Antwort teils unvollständig.
- **Live-Demo gestellt.** Das Debugging betrifft triviale Fehler. Logan Kilpatrick räumt einen holprigen Gesprächsrhythmus ein, das Modell springt zu eifrig ein (22:40). Feinsteuerung ist nur angekündigt.
- **Alleinstellung unbelegt.** Die Aussage, andere Modelle könnten das nicht (01:30), wird mit keinem Vergleich gestützt.
- **Geschäftsideen ohne Substanz.** Directories, Möbel-Shop, Satellitenbilder, Service-Automatisierung: keine Marktdaten, keine Preise, kein Vertriebsweg. Logan Kilpatrick nennt die Beispiele selbst zufällig.
- **Gemma unklar.** „Open Source“ wird behauptet, offene Gewichte, Lizenz und Größen bleiben unerwähnt.
- **Momentaufnahme.** Modellnamen und UI-Verhalten gelten für den Aufnahmezeitpunkt und sind heute nicht mehr aktuell.
