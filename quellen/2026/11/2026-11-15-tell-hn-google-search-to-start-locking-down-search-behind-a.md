# Hinweis an HN: Google Search beginnt, die Suche hinter eine Login-Wand zu legen

> **Quelle:** [Tell HN: Google Search to start locking down search behind a login wall](https://news.ycombinator.com/item?id=50491617) · Anonymer Original-Poster auf Hacker News, Gegenstand ist Google · Diskussion · 2026-11-15
> **Sprecher verkauft:** nichts, Gegenstand ist Google Search (laut Kommentar mit Werbung und KI-Antworten) · **Zielmarkt der Aussagen:** Endnutzer (Consumer), keine B2B-Quelle · **Beweislage:** eine einzelne, nicht reproduzierte Beobachtung plus Anekdoten aus dem Thread

## Worum es geht
Ein Nutzer berichtet, dass Google auf manchen geteilten ISP-Adressen (CGNAT) die gesamte Ergebnisseite erst nach Anmeldung zeigt, statt wie bisher nur CAPTCHAs auszuspielen. Die Diskussion fragt, ob das neu ist, woran es liegt und wohin man ausweicht. Für B2B Go-to-Market ist das nur indirekt relevant: für alle, die KI-Agenten oder Automatisierungen auf öffentliche Websuche stützen.

## Was man anwenden kann
1. **Abgemeldete Suche nicht als stabile Datenquelle einplanen.** Der Original-Post beschreibt eine Stufenfolge: erst viele CAPTCHAs bei jeder neuen privaten Sitzung, dann auf einem Teil der Adressen eine Login-Aufforderung vor der Ergebnisseite. Wer Agenten oder Skripte baut, die Google-Ergebnisse ohne Konto abrufen, sollte mit Ausfällen dieser Art rechnen. Belegt ist das nur als Einzelbeobachtung auf CGNAT-Adressen, nicht als allgemeine Google-Politik.
2. **Ausgangsadresse als Störfaktor testen.** Betroffen waren laut Post geteilte ISP-Adressen ohne VPN. Auf manchen VPN-Adressen, auch beim kostenlosen VPN von Firefox, kam weder Login noch CAPTCHA. Ein Kommentar widerspricht und hält VPN-Ausgänge seit langem für besonders verdächtig. Prüfen lässt sich das nur im eigenen Setup: dieselbe Abfrage über verschiedene Netze laufen lassen, bevor man ein Werkzeug darauf baut.
3. **IPv6 als Spur prüfen.** Ein Kommentar fragt, ob das CGNAT-Netz kein IPv6 bietet. Die Frage zielt darauf, dass die Reputation geteilter IPv4-Adressen die Hürde auslösen könnte. Beantwortet wurde das im Thread nicht. Relevant nur, wenn der eigene Anschluss IPv6 anbietet.
4. **Für Agenten eine Such-API statt Scraping nutzen.** Ein Kommentator lässt die eigenen KI-Agenten Kagi über die API verwenden und berichtet, sie fänden damit deutlich mehr als ohne. Das ist ein Erfahrungsbericht ohne Kosten, ohne Benchmark und ohne Vergleich zu anderen Such-APIs. Kagi ist laut Thread ein Bezahldienst.
5. **Alte Browser als Ursache ausschließen.** Ein Kommentator mit der letzten Chrome-Version für Windows 7 sieht im privaten Modus täglich CAPTCHAs, Cloudflares Bestätigungsbutton verschwindet, DigitalOcean lädt nicht, die ChatGPT-Weboberfläche fiel kurzzeitig aus. Wer Bot-Abwehr beobachtet, sollte zuerst den Browser-Stand prüfen. Auch das ist eine Einzelanekdote.
6. **Login-Pflicht als Plattformtrend einordnen.** Genannt werden YouTube („Sign in to confirm you're not a bot“) sowie laut einem Kommentar X, Instagram und Reddit. Für Recherche-Workflows heißt das: Quellen, die heute ohne Konto lesbar sind, können es morgen nicht mehr sein. Ein Kommentar nennt ResearchGate, wo Paper nach derselben Meldung nicht mehr zugänglich seien. Eine Prüfung dieser Aufzählung gibt es nicht.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 41 | Punkte des Beitrags auf Hacker News | Plattformangabe |
| 28 | Kommentare zum Beitrag insgesamt | Plattformangabe |
| 12 | davon im ausgewerteten Material enthalten | Erfassung, Rest unbekannt |
| 3 | konkurrierende Ursachenhypothesen im Thread | alle ohne Beleg |

## Grenzen und Widerspruch
- **Der Titel überzieht.** Ein Kommentator bittet, den Titel als Frage zu formulieren. Der Post selbst endet mit „Has anyone encountered that?“. Belegt ist eine persönliche Beobachtung an einem Tag, keine Google-Strategie.
- **Keine Bestätigung von Google**, keine Ankündigung, keine Stellungnahme.
- **Keine Rahmendaten:** kein Land, kein ISP, kein Browser, keine Häufigkeit, keine Reproduktion. Offen bleibt auch, ob ein Login die Seite dauerhaft freischaltet.
- **Ursachen unbelegt:** Residential-Proxy-Botnetze (Original-Post), eine Flut von KI-Scrapern und Agenten (mehrere Kommentare), ein Growth-Team nach dem Vorbild sozialer Netzwerke (hackermailman). Für keine Erklärung gibt es Daten.
- **„Nicht neu“:** LorenPechtel hält das Misstrauen gegenüber fragwürdigen Adressen für altbekannt, weil alles, was ein Scraper sein könnte, als solcher gelte.
- **Wechselempfehlungen ohne Begründung:** DuckDuckGo, Brave Search und Kagi werden als Alternativen genannt, ohne Vergleich. Ein Kommentar sucht Videos inzwischen auf TikTok statt YouTube, mit der Einschränkung, dass man sie in drei Teilen ansehen müsse.
- **Gegenkritik:** musicale meint, die Suche sei längst hinter KI-Antworten und Werbung versteckt. ggm sieht ein selbst verursachtes Problem, weil dieselben Konzerne Suche und KI-Systeme betreiben.
- **Zugänglichkeit:** Nutzer an geteilten oder öffentlichen Rechnern und Menschen ohne Smartphone (eine Kontoerstellung bei YouTube scheiterte daran) sind laut Thread benachteiligt. Zahlen dazu fehlen.
- **Relevanz:** Für B2B-Vertrieb und Marketing liefert die Quelle keine Taktik. Brauchbar ist sie als Warnsignal für Agenten mit Websuche.
