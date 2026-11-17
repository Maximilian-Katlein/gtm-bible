# Cursor AI Tutorial für Einsteiger

> **Quelle:** [Cursor AI tutorial for beginners](https://www.youtube.com/watch?v=gqUQbjsYZLQ) · Greg Isenberg & Mike, Late Checkout / Independent · Video · 2026-11-17
> **Sprecher verkauft:** Startup Idea Bank, Beteiligung an boringmarketing.com, Community · **Zielmarkt der Aussagen:** Indie Hacker, Gründer, Creator, Kleinbetriebe · **Beweislage:** Praxiserfahrung eines Entwicklers mit Live-Demos, keine Messungen oder Vergleiche.

## Worum es geht
Wie bekommt man mit dem AI-Code-Editor Cursor brauchbare Software statt Code-Chaos? Mike, ein Full-Stack-Entwickler, zeigt einen Ablauf aus Vorplanung, visuellem Prototyp, Projektregeln und eingebundener Dokumentation. Zielgruppe sind Gründer und Nicht-Entwickler, die eigene Produkte bauen wollen. Für B2B-Teams mit bestehender Codebasis, Review-Prozessen oder Compliance-Vorgaben sagt das Video nichts.

## Was man anwenden kann
1. **Erst planen, dann Cursor öffnen.** Mike rät davon ab, direkt im Composer Code anzufordern (02:30). Vorher wird die Oberfläche skizziert: auf dem iPad, in Figma, Paint oder auf Papier (02:50). Er nennt das „measure twice, cut once“ (03:30). Gilt laut Mike für Software, die real genutzt werden soll. Bei Nebenprojekten darf man ohne Plan experimentieren (18:30).

2. **Skizze in v0 zu einem Prototyp machen.** Das Wireframe als Screenshot in v0 von Vercel ziehen und die Seite beschreiben lassen (08:40). v0 nutzt die UI-Bibliothek shadcn/ui, daher entstehen saubere Buttons, Footer und Testimonial-Bereiche per Prompt (07:50). Mike empfiehlt mindestens 10 bis 15 Prompt-Runden in v0, bis das Design der Vorstellung nahekommt (10:30). Danach den generierten Code kopieren und in Cursor einfügen, damit Cursor auf einer Basis aufbaut (08:14).

3. **Projektregeln in `.cursorrules` hinterlegen.** Auf cursor.directory gibt es kopierbare Regel-Prompts je Framework, für Next.js zeigt die Suche sechs Vorlagen (11:45). Den Text in eine Datei `.cursorrules` im Wurzelverzeichnis des Projekts einfügen (12:40, Demo 13:00). Zweck: Das Modell soll keine veraltete Syntax ziehen (12:15).

4. **Regeln für seltene Tech-Stacks selbst erzeugen.** Fehlt der eigene Stack, ein bis zwei vorhandene Beispiele kopieren und Claude oder ChatGPT bitten, ein gleich knappes Gegenstück für die eigenen Technologien zu schreiben (14:30, Prompt 15:00). Im Demo für React und Python lieferte die AI Prinzipien und Versionsangaben, etwa React 18 (15:40). Mit Nachsätzen wie „JavaScript statt TypeScript“ wird nachgeschärft (16:30). Die Versionsangaben solltest du gegen die offizielle Doku prüfen.

5. **Offizielle Dokumentation in Cursor einbinden.** Im Composer über @ den Punkt Docs wählen, „Add new doc“ klicken, URL einfügen und benennen, etwa „nextjs docs“ (20:30, 20:50). Mike zeigt dasselbe mit der Supabase-Dokumentation (22:40). Bei Fehlermeldungen die Doku im Prompt taggen, damit Cursor mit aktuellem Stand debuggt (23:10). Begründung: Die Docs seien die verlässlichste Quelle (19:40).

6. **Bei festgefahrenen Bugs das Werkzeug wechseln.** Kommt Cursor nicht weiter, den Fehler samt Code in die Web-Oberfläche von Claude, v0 oder ChatGPT kopieren (26:15). Dazu gehören auch die Lösungsversuche, die Cursor schon erfolglos probiert hat (27:20). Mike berichtet, dass das bei ihm oft hilft, obwohl in Cursor ebenfalls Claude läuft. Einen Grund nennt Mike nicht.

7. **Bestehenden Code erklären lassen.** In Cursor öffnet Cmd + Shift + L den Chat. Prompt: Code für Anfänger erklären, mit Ablauf und Logik (30:30). Unverständliche Stellen aus der Antwort, etwa die Direktive „use client“ in Next.js, erneut einfügen und nachfragen (31:40). Kommentare direkt in den Code schreiben lassen geht ebenfalls (35:10). Mike bewertet das Erklären von vorhandenem Code als stärkste Anwendung (29:20).

8. **Funktionierenden Code als Vorlage wiederverwenden.** Wenn etwas auf einer Seite läuft, den Code kopieren und die AI bitten, dasselbe für eine andere Seite zu tun, mit genauer Beschreibung der Abweichung (35:30).

9. **Mit Starter-Kit statt bei null beginnen.** Für vollwertige Apps rät Mike zu Vorlagen mit fertiger Authentifizierung, Stripe-Zahlung und Datenbankanbindung (36:30). Mike bietet ein eigenes kostenloses Next.js-Template auf GitHub an, nennt im Video aber keinen Repository-Namen (38:00). In einem anderen Video entstand damit laut den Sprechern eine Social-Media-App in rund 90 Minuten (39:15).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 10 bis 15 | Mindestanzahl Prompt-Runden in v0 vor dem Wechsel zu Cursor | Anekdote, Faustregel von Mike |
| 6 | Next.js-Vorlagen auf cursor.directory zum Zeitpunkt der Aufnahme | Live gezeigt |
| 1 Woche | Zeit, in der Mike als erfahrener Webentwickler Mobile-Entwicklung gelernt haben will (34:30) | Anekdote, Selbstauskunft |
| 90 Minuten | Bau einer Social-Media-App mit dem Starter-Template in einem anderen Video (39:15) | Anekdote, nicht in diesem Video gezeigt |
| 30 Tage, 100 % | Sprint mit Geld-zurück-Garantie bei boringmarketing.com (25:20) | Werbung für Gregs eigene Beteiligung |
| 30+ | Startup-Ideen in Gregs Idea Bank (06:20) | Werbung, Validierung nicht erklärt |

## Wortlaute
- „You are an expert in TypeScript, Node.js, Next.js, App router, React, Shadcn UI, Radix UI and Tailwind.“ (12:00) Einstieg des Next.js-Regelprompts von cursor.directory: Rolle plus exakter Stack.
- „I am building a web application using React and Python, I want to write a nice prompt for my AI similar to the one below. Please be just as concise.“ (15:00) Meta-Prompt, um eigene `.cursorrules` aus einem Beispiel abzuleiten.
- „Explain this code to me like a beginner. I want to know the flow, logic, and overall how things work.“ (30:30) Erklär-Prompt für fremden oder eigenen Code.
- „This works for this page. Can we do the same thing for this page? but and then explain exactly what you want done.“ (35:30) Muster, um funktionierenden Code mit Abweichung zu übertragen.
- „give whatever AI model you're going to, the bug that you experienced, the solutions that it tried to give and didn't work.“ (27:20) Übergabe eines Bugs an ein anderes Modell.

## Grenzen und Widerspruch
- Alle Empfehlungen beruhen auf der Erfahrung eines einzelnen Entwicklers. Es gibt keine Vergleiche, keine Fehlerquoten, keine Zeitmessungen.
- Die Lernzeit von einer Woche gilt höchstens für Menschen mit Webentwicklungs-Erfahrung. Für Nicht-Entwickler ist sie nicht belegt.
- Höflichkeit gegenüber der AI („please and thank you“, 09:05) soll bessere Ergebnisse bringen. Das ist persönliches Empfinden.
- Warum Claude im Browser einen Bug löst, an dem Claude in Cursor scheitert, bleibt offen. Mögliche Ursachen wie andere System-Prompts oder anderer Kontext werden nicht genannt.
- Die Werbeblöcke für boringmarketing.com und die Startup Idea Bank stammen von Greg in eigener Sache. Kundendaten oder Methodik fehlen.
- Menüpfade, Tastenkürzel und das Dateiformat `.cursorrules` entsprechen dem Stand der Aufnahme. Vor der Anwendung in der aktuellen Cursor-Dokumentation prüfen.
- Themen wie Tests, Sicherheit, Code-Review, Datenschutz oder Betrieb kommen nicht vor. Für Produktivsoftware im Unternehmen reicht der gezeigte Ablauf allein nicht.
