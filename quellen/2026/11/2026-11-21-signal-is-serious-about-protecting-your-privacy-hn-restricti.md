# Signal nimmt den Schutz deiner Privatsphäre ernst

> **Quelle:** [Signal is Serious About Protecting Your Privacy](https://signal.org/blog/protecting-your-privacy/) · Meredith Whittaker, Signal Technology Foundation (Diskussion: Hacker-News-Kommentatoren, 512 Punkte) · Artikel mit Diskussion · 2026-11-21
> **Sprecher verkauft:** Signal, kostenloser Open-Source-Messenger mit Ende-zu-Ende-Verschlüsselung, getragen von einer gemeinnützigen US-Stiftung (501(c)(3)) · **Zielmarkt der Aussagen:** Privatnutzer mit hohem Datenschutzbedarf; Appell an Apple, Google und Microsoft · **Beweislage:** Positionspapier mit eigenen Maßnahmen, aber ohne veröffentlichte Messdaten oder Forensik-Ergebnisse.

## Worum es geht
Wie kann eine App Vertraulichkeit garantieren, wenn das Betriebssystem selbst KI-Agenten mitbringt, die den Bildschirm lesen? Signal beschreibt seine Gegenmaßnahmen auf iOS, Android und macOS, nennt deren Lücken und stellt zwei Forderungen an die Betriebssystemhersteller. Relevant ist das für alle, die Apps mit Vertraulichkeitsversprechen bauen oder Sovereign-AI-Argumente prüfen.

## Was man anwenden kann
1. **Bildschirmerfassung plattformspezifisch sperren.** Signal verhindert auf iOS 27 Screenshots in der App. Auf Android wird die Erfassung blockiert, sobald ein KI-Assistent den Signal-Bildschirm lesen will. Dasselbe Muster nutzte Signal im Vorjahr gegen Microsoft Recall auf Windows 11, das dort standardmäßig aktiv war.
2. **Auf Android gezielt erkennen statt pauschal sperren.** Signal Android schaltet die Einstellung „Screen security“ automatisch ein, wenn KI-Zugriff erkannt wird. Grund: Bei vielen Herstellern lässt sich ein Screenshot-Versuch nicht zuverlässig erkennen, wenn Screenshots schon gesperrt sind, und Nutzer wären von stumm scheiternden Screenshots verwirrt. Die Erkennungsmethode nennt Signal nicht. Die Abdeckung ist außerhalb der Pixel-Distribution unvollständig.
3. **Opt-out für Nutzer mit klarer Warnung.** Wer Screenshots braucht, kann den Schutz in den Signal-Einstellungen abschalten. Signal weist darauf hin, dass dann eigene und fremde Inhalte für KI-Agenten zugänglich werden können und die Datenschutzgarantien entfallen.
4. **macOS: Nutzereinstellung statt App-Schutz.** Auf macOS lassen sich Screenshots laut Signal nicht zuverlässig blockieren. Gründe: keine klar dokumentierten APIs, Lösungen nur für Streaming und DRM-Inhalte, Schutz gegen Dauer-Bildschirmaufnahme greift nicht bei Screenshots. Empfehlung für macOS 27: Signal unter Systemeinstellungen > Siri bei „Excluded Apps“ eintragen.
5. **Bedrohungsmodell auf alle Gesprächsteilnehmer ausweiten.** Sobald ein OS-Agent Bildschirmdaten erfasst hat, liegen sie in einer lokalen Datenbank oder auf einem Server des Agenten, außerhalb der App-Kontrolle. Ein Kommentator ergänzt: Auch ohne eigene KI-App kann das Gerät des Kontakts den Chat weitergeben.
6. **Weitere Zugriffswege mitdenken.** Screenshot-Sperren decken nicht ab, wenn Agenten Inhalte über das Dateisystem, Benachrichtigungen, APIs oder andere OS-Frameworks lesen. Drittanbieter-Agenten wie Metas Muse nutzen dafür Bedienungshilfen-Rechte, die Nutzer beim Setup erteilen. Eine Lösung dagegen hat Signal noch nicht.
7. **Forderungen als Prüfliste für eigene Plattformanforderungen.** Erstens ein einfacher, dokumentierter Opt-out für Entwickler, der Screen Reading, Dateisystem, Benachrichtigungen, APIs und Frameworks umfasst, ohne den Kernnutzen der App zu beschädigen. Zweitens bessere Dokumentation und technische Spezifikation, wie die Agenten Daten abgreifen und verarbeiten.
8. **Confidential Computing nicht als Endlösung verkaufen.** Signal hält solche Ansätze für unvollständig, weil weiterhin der Anbieter bestimmt, wie viel Privatsphäre bleibt. Wer Cloud-KI mit „vertraulicher Verarbeitung“ bewirbt, sollte diesen Einwand kennen.
9. **Alternative Gestaltung: Opt-in durch Nutzer.** Ein Kommentator schlägt eine eigene OS-Berechtigung für KI-Agenten vor, analog zu Standort oder Fotos, die eine App im passenden Moment anfordert, etwa beim Tippen auf „Ask AI“. Das ist das Gegenmodell zu Signals Entwickler-Opt-out und wirkt nur, solange das Betriebssystem die Berechtigung durchsetzt.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| über ein Jahrzehnt | Dauer, seit Signals Garantie auf Open-Source-Code und formal verifiziertem Protokoll beruht | Herstellerangabe |
| alle paar Sekunden | Intervall, in dem Microsoft Recall den Bildschirm erfasst und per OCR durchsuchbar macht | Behauptung ohne Beleg im Artikel |
| 3 | große Konsumenten-Betriebssysteme (Android, iOS/macOS, Windows), die laut Signal die Lebensbedingungen aller Apps bestimmen | Herstellerangabe |
| über 300 MB, 1 GB RAM | Größe und Speicherbedarf von Signal Desktop laut Kommentator, themenfremd | Behauptung ohne Beleg |

## Grenzen und Widerspruch
- **Keine Messdaten.** Signal hat nach eigener Aussage monatelang forensisch auf Android und iOS untersucht, veröffentlicht die Ergebnisse aber nicht. Ein Kommentator fordert sie als offenes, gemeinsam gepflegtes Dokument, damit kleinere App-Teams profitieren.
- **Speicherung durch OS-Agenten ist nicht belegt.** Welche Daten Gemini Intelligence, Siri AI Onscreen Awareness oder Muse tatsächlich speichern und wohin sie fließen, bleibt offen. Der Artikel formuliert das als Möglichkeit.
- **Keine Herstellerstimmen.** Apple, Google, Microsoft und Meta kommen nicht zu Wort. Signal ist nur „vorsichtig optimistisch“, dass Google und Apple reagieren, ohne Zusagen, Zeitplan oder APIs zu nennen.
- **Komfort gegen Schutz.** Ein Kommentator will Familienchats ausdrücklich von Siri und Spotlight indexieren lassen und fordert eine Einstellung statt Bevormundung. Ob der Opt-out solche Funktionen selektiv erlaubt, sagt der Artikel nicht.
- **App-Schutz reicht nicht.** Ein Kommentator hält Screenshot-Sperren langfristig für wirkungslos und fordert, Nutzern Systeme wie GrapheneOS oder Linux zu empfehlen. Das gilt nur für Nutzer, die ihr Betriebssystem frei wählen können.
- **Vertrauen in US-Anbieter.** Ein Kommentator verweist auf den CLOUD Act und spekuliert, nach eigener Aussage konspirativ, über Signal als Honeypot. Belege fehlen. Als Alternative nennt der Kommentator föderierte Dienste wie Matrix im kleinen Kreis mit einer technisch versierten Person.
- **Überschrift als Werbefloskel.** Zwei Kommentatoren kritisieren den Titel, weil jeder Anbieter Datenschutz für sich beansprucht. Die Kritik betrifft die Formulierung, nicht die Maßnahmen.
- **Geringe GTM-Relevanz.** Für Vertrieb oder Marketing gibt die Quelle kaum Taktiken her. Nutzbar ist sie als Argumentationsgrundlage für Sovereign AI und für App-Entwickler mit Vertraulichkeitsanforderungen.
