# Paperclip: KI-Agenten einstellen wie Mitarbeiter (Live-Demo)

> **Quelle:** [Paperclip: Hire AI Agents Like Employees (Live Demo)](https://www.youtube.com/watch?v=C3-4llQYT8o) · Duda (Pseudonym, auftretend als KI-Avatar, Creator von Paperclip) im Gespräch mit Greg Isenberg · Video · 2026-11-19
> **Sprecher verkauft:** Paperclip, einen Open-Source-Orchestrator für KI-Agenten (lokal oder selbst gehostet, gehostete Version angekündigt, laut Duda noch ohne Umsatz) · **Zielmarkt der Aussagen:** Solo-Gründer und kleine Betriebe, teils unklar, Enterprise wird nicht adressiert · **Beweislage:** Produktdemo des Creators, das gezeigte Projekt liefert im Video kein fertiges Ergebnis.

## Worum es geht
Wie steuert man mehrere KI-Coding-Agenten so, dass klar bleibt, wer woran arbeitet, was es kostet und was erledigt ist? Paperclip bildet dafür eine Firma nach: Org-Chart, Rollen, Ziele, Budgets und Aufgaben als Issues. Relevant für Gründer und kleine Teams, die bereits Claude Code, Codex oder ähnliche Agenten parallel einsetzen.

## Was man anwenden kann
1. **Das Ausgangsproblem prüfen.** Duda baute Paperclip, nachdem 20 bis 30 Claude-Code-Fenster parallel liefen. Nach einem Wochenende waren Aufgaben, Ergebnisse und Fortschritt unklar, das Token-Budget aber verbraucht (09:07). Wer dieses Muster kennt, braucht eine Schicht für Zuordnung, Budget und Nachvollziehbarkeit, unabhängig vom Werkzeug.

2. **Vorhandene Agenten einbinden statt neue kaufen.** Paperclip bringt keinen eigenen Agenten mit, sondern orchestriert Cursor, Claude Code, Codex, OpenClaw und über OpenCode jedes Modell auf OpenRouter (03:39, 06:17). Am besten läuft es derzeit lokal mit installiertem Claude Code oder Codex (05:52).

3. **Modelle nach Rolle staffeln.** Der CEO-Agent soll laut Duda ein Frontier-Modell nutzen, für einfachere Aufgaben reicht oft ein günstigeres Modell (06:36). Zeitweise kostenlose OpenRouter-Modelle können einfache Arbeit gratis erledigen, die Verfügbarkeit wechselt aber (06:51).

4. **Startauftrag an das Geschäft anpassen.** Der Standardauftrag an den CEO lautet: Founding Engineer einstellen, Hiring-Plan schreiben, Roadmap in Aufgaben zerlegen, delegieren (07:56). Für reine Marketing- oder Sales-Vorhaben lässt sich der Auftrag ändern. Der Hiring-Plan ist ein editierbares Dokument, das man per Kommentar korrigiert (10:02).

5. **Einstellungen zuerst manuell freigeben.** Standardmäßig landet jede Einstellung eines neuen Agenten in der Inbox zur Freigabe. Erst wenn man dem Verhalten der Agenten vertraut, schaltet man auf automatisches Einstellen um (10:50).

6. **Ein Agent pro Aufgabe, Parallelität bewusst setzen.** Jeder Issue wird nur von einem Agenten gleichzeitig bearbeitet (10:30). Mehr Durchsatz kommt über die Concurrency-Einstellung, etwa vier Engineers parallel (12:31).

7. **Agenten mit schriftlichen Ankern versehen.** Agenten wachen laut Duda auf wie die Hauptfigur aus Memento: fähig, aber ohne Wissen über Rolle und Auftrag (14:24). Abhilfe schaffen Persona-Datei und Heartbeat-Checkliste: Identität abrufen, Tagesplan lesen, eigene Zuweisungen suchen, Arbeit auschecken, in Tasks zerlegen, am Ende Memory extrahieren (14:49). Das Default-Memory ist dateibasiert nach dem PARA-System (13:21).

8. **Instruktionen nach Fehlern nachschärfen.** Systematische Prompt-Evals gibt es noch nicht. Stattdessen trägt man nach jedem unerwünschten Verhalten eine Regel in die Instruktionen ein, etwa: für jede Aufgabe ein Erfolgskriterium definieren und QA prüfen lassen (15:51, 16:04).

9. **Engineer an QA übergeben lassen.** Das einfachste verlässliche Muster: Nach dem Bauen prüft ein QA-Agent, bei Web-Apps per Browser und Screenshot (26:55). Der gezeigte QA-Agent nutzt den Skill „agent browser“, laut Duda schneller als Chrome, weil kein Fenster den Rechner übernimmt (31:19).

10. **Skills per Auftrag vergeben, aber vorher prüfen.** Ein Satz an den CEO wie „hire video editor“ plus Skill-URL legt Rolle und Skill an (20:38). Skills kommen etwa von skills.sh und werden als Referenz eingebunden, Updates lassen sich prüfen (18:42, 20:16). Schadcode in Skills ist laut Duda ungelöst, GitHub-Stars sind kein Sicherheitsnachweis (19:00).

11. **Kontext selbst liefern.** Gute Ergebnisse, etwa bei Remotion-Videos, brauchen viel Kontext und Referenzen. Paperclip organisiert Kontext, schreibt ihn aber nicht (21:41). Konkret: zuerst klären, ob ein Brand Guide existiert, sonst einen Issue dafür anlegen und das Ergebnis prüfen (22:36).

12. **Wiederkehrendes als Routine anlegen.** Eine Routine ist eine Issue-Vorlage mit Trigger, etwa täglich 10:00 Uhr. Jeder Lauf zeigt Tokens, Aktionen und Ergebnis (35:48, 35:59). Vor dem Scharfschalten einmal manuell starten und das Ergebnis zunächst im Issue statt im Zielkanal posten lassen (34:23).

13. **Auf Zielebene steuern.** Duda empfiehlt, als „Board“ mit dem CEO über Ziele wie ein MRR-Ziel zu sprechen statt Einzelaufgaben zu verteilen (11:29). Im eigenen Beispiel greift Duda aber selbst auf Pixel-Ebene ein und räumt das ein (28:55).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 30.000 | GitHub-Stars von Paperclip, keine drei Wochen nach Launch, Stand Ende März 2026 (35:10, 36:52) | Im Repo gezeigt |
| ca. 500 | Offene Pull Requests im Paperclip-Repo (35:10) | Im Repo gezeigt |
| 20 bis 30 | Parallel offene Claude-Code-Fenster vor Paperclip (09:07) | Anekdote |
| 0 Dollar | Angezeigte Monatsausgaben, weil Subscriptions statt API genutzt werden (24:05) | Im Dashboard gezeigt, echte Kosten offen |
| 60.000 / über 100 | Stars und Agenten im Repo „agency agents“ (40:09) | Behauptung ohne Beleg |
| 0 | Umsatz von Paperclip (38:49) | Aussage des Sprechers |
| ca. 30 Minuten | Zeit, bis ein per KI in einem Schritt gebautes Startup auseinanderfällt (26:17) | Behauptung ohne Beleg |
| 2 bis 4 Wochen | Nutzungsdauer, nach der OpenClaw laut Duda unübersichtlich wird (18:08) | Behauptung ohne Beleg |

## Wortlaute
- „you are the CEO, you set the direction for the company, hire founding engineer, write a hiring plan, break the roadmap into concrete tasks, and start delegating work.“ (07:56) Standard-Startauftrag an den CEO-Agenten.
- „make sure you set like, uh, success condition for every task and ask the developer, uh, to have QA review it“ (16:04) Beispiel für eine nachträglich ergänzte Regel.
- „let's plan uh 60-second Remotion video um about Moolah showing the key pitch um that we could share on Twitter.“ (23:04) Planauftrag, der bewusst nur einen Plan und noch kein Video anfordert.
- „we especially uh want to celebrate our community members who contribute.“ (34:23) Kern der täglichen Routine: GitHub-Änderungen der letzten 24 Stunden lesen, Discord-Update schreiben, Contributor hervorheben, am Wochenende ohne Änderungen nichts tun.
- „mentions pill is misaligned with the like uh project mention pill. Fix it, right?“ (27:44) Bug-Issue mit Screenshot, ergänzt um die Anweisung, danach an QA zu übergeben.

## Grenzen und Widerspruch
- **Kein Ergebnis gezeigt.** Die Live-Firma „Moola“ (Finanz-App aus Greg Isenbergs Idea Browser) bleibt bei Plänen und laufenden Issues. Die angekündigte Rückkehr zum Ergebnis findet nicht statt. Das Game-Studio-Beispiel wurde wegen hohen Token-Verbrauchs pausiert, ohne Mengenangabe.
- **Kosten unbekannt.** Die 0-Dollar-Anzeige entsteht nur durch Subscriptions. Zu Tokens pro Aufgabe, Laufzeit oder Fehlerraten gibt es keine Zahlen.
- **Selbst eingeräumte Unsicherheit.** Vorgefertigte Agentenorganisationen sind laut Duda „completely unproven“ (41:06), Evals fehlen, und auch das eigene Team nutzt Paperclip „nicht da, wo ich es haben will“ (32:40).
- **Nutzerbeispiele sind Hörensagen.** Marketingfirma, Security-Review-Firma, Zahnarzt und Dachdecker werden ohne Namen, Zahlen oder Ergebnisse genannt. Der Dachdecker-Fall (Leads über Hagel- und Satellitendaten) ist reine Erkundung (38:04).
- **Sicherheit kaum behandelt.** Skill-Supply-Chain ist ungelöst, die Sicherheitsregel der Persona ist ein Satz. Prompt Injection, Rechtevergabe und Datenschutz fehlen. Für B2B-Einsatz mit Kundendaten ist das eine Lücke.
- **Viele Ankündigungen.** Import/Export, Cloud-Hosting, CEO-Chat, Evals-Tools und Maximizer Mode waren zur Aufnahme nicht verfügbar.
- **Interessenlage.** Produktdemo des Creators, der Gastgeber nutzt das eigene Produkt als Ideenquelle. Kritische Nachfragen zu Kosten und Grenzen fehlen weitgehend.
- **Wenig GTM-Substanz.** Die Marketing-Agenten (Blogger, Content-Stratege) sind nur im Aufbau erwähnt. Zu Open-Weight-Modellen und Datenhoheit gibt es nur den Hinweis auf OpenCode und OpenRouter, nichts zu lokalen Modellen.
- **Zukunftsthese unbelegt.** Dass Orchestrierung auch bei besseren Modellen nötig bleibt, ist Dudas Einschätzung ohne Beleg (45:49).
