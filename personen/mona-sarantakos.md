# Mona Sarantakos

Mona Sarantakos war nach eigener Aussage eine von vier Produktmanagerinnen und Produktmanagern hinter Metas Consumer-Agenten Muse. Man hört ihr zu, um zu lernen, wie man einen Agenten mit Zugriff auf persönliche Daten in kleinem Team baut, absichert, mit Evals prüft und Nutzer zur Aktivierung bringt.

Stand: 2026-11-17 · 1 Quelle

Verkauft: In den bisherigen Quellen keine eigenen Kurse, Firmen oder Communities. Sie spricht als Teil des Muse-Teams und damit im Interesse von Metas Produkt Muse.

*Hinweis zur Einordnung: Alle bisherigen Learnings stammen aus einem einzigen Gespräch über ein B2C-Produkt eines Großkonzerns. Die Übertragung auf B2B Go-to-Market ist eine eigene Ableitung und nicht von ihr belegt.*

## Kernideen

### 1. Vertrauen ist Launch-Voraussetzung, nicht Nachbesserung

Ein Agent mit Zugriff auf Mail, Kalender oder Browser darf erst raus, wenn die neuen Risiken geschlossen sind. Wer zu früh startet und Fehler produziert, verliert Nutzer dauerhaft. Sicherheit zieht sich deshalb durch Phasenplan, Evals und Architektur.

> „trust is a must... if we launch too early and we have a bunch of issues, people will not trust this agent.“ (12:40)

Belege:
- Browser-Werkzeuge erzeugen neue Sicherheitsrisiken, die vor dem Launch geschlossen sein müssen. Frühe Vertrauensverluste führen dazu, dass Nutzer nicht zurückkommen. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (12:40)
- Die zweite Entwicklungsphase widmete sich ausdrücklich Verlässlichkeit, Sicherheit und Infrastruktur-Skalierung. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (10:20)
- Safety (Prompt Injection, Schaden) ist eine der vier Eval-Kategorien. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (43:00)
- Eine separate Sicherheitskomponente (Sentinel) läuft außerhalb des Haupt-Agenten als Backstop. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (19:10)
- Diskretion zwischen mehreren Agenten musste nach einem Vorfall im Multiplayer-Test eigens geprüft werden. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (59:00)

### 2. Der Agent gehört dem Nutzer und dient seinen Zielen

Ein persönlicher Agent soll sich wie Eigentum des Nutzers anfühlen, auf dessen Ziele hinarbeiten und ihm Arbeit abnehmen. Muss der Nutzer ihn ständig beaufsichtigen, ist der Nutzen weg.

> „the last thing you want to talk to is a corporate logo“ (26:20)

Belege:
- Eine Woche vor Launch fiel das Konzernlogo zugunsten eines persönlichen Avatars. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (26:20)
- Mark Zuckerberg lenkte den Fokus von Aufgabenerledigung auf das Erreichen von Nutzerzielen. Daraus entstanden ein Goals Tab und proaktive Funktionen (Dreaming, Studying), in denen der Agent über Prioritäten des Nutzers nachdenkt. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (21:10)
- Wer einen Agenten ständig kontrollieren und mit Daten nachfüttern muss, verliert die Zeitersparnis. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (82:15)

### 3. Lauffähige Prototypen statt Slides

Entscheidungen fallen am funktionierenden Produkt, nicht in Präsentationen. Das kleine Kernteam zeigte der Führung Prototypen direkt auf dem Smartphone und iterierte im 24-Stunden-Takt.

> „We didn't do formal reviews, right? Like I didn't make any slides.“ (16:40)

Belege:
- Keine formellen Reviews, keine Slides, Prototypen im 24-Stunden-Zyklus direkt vor der Führung. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (16:40)
- Schon die erste Phase, die Produktdefinition, lief über Prototypen auf virtuellen Maschinen. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (10:20)
- Das Team blieb klein: etwa 10 Personen zum Start, später unter 100, nur 4 PMs. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (75:10)

### 4. Qualität entsteht durch eigene Evals und gestaffelte Freigabe

Öffentliche Benchmarks reichen für Agenten mit persönlichem Kontext nicht. Muse wurde über eine eigene, breite Eval-Sammlung, automatisch erzeugte Testdaten und schrittweise wachsende Testgruppen freigegeben.

Belege:
- Über 100 Evals in vier Kategorien, weil öffentliche Benchmarks für diesen Agententyp nicht ausreichten. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (43:00)
- Agentenschwärme erzeugen synthetische Multi-Turn-Daten und speisen Berichte in die Evals. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (38:20)
- Die dritte Phase war Qualitäts-Gating mit schrittweise wachsenden Testgruppen. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (10:20)

### 5. Aktivierung ist nach dem Launch das eigentliche Problem

Ein offenes Eingabefeld überfordert. Nutzer brauchen konkrete Startpunkte, Erklärungen passend zu ihrer Kohorte und Geschichten anderer Nutzer. Was tatsächlich genutzt wird, weicht von den Erwartungen des Teams ab, deshalb braucht es einen direkten Feedback-Kanal.

> „The most effective lever out there is word of mouth.“ (47:30)

Belege:
- Ideas Tab mit Starter-Paketen gegen die Hürde des leeren Prompts. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (49:00)
- Gestaffeltes Onboarding, weil frühe Kohorten andere Erklärungen brauchen als spätere Massennutzer. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (50:40)
- Mundpropaganda über konkrete Anwendungsfälle als wirksamster Aktivierungshebel. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (47:30)
- Einkaufen wurde überraschend ein Top-Anwendungsfall, Heimautomatisierung blieb trotz hoher Erwartung schwach. Der Agent verteilt Käufe auf mehrere spezialisierte Shops statt auf einen Händler. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (32:05)
- Feedback geht per Sprache oder Text an den eigenen Agenten, der einen strukturierten Bericht ans Team schickt. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (85:20)

## Methoden und Abläufe

### Drei-Phasen-Modell für einen Agenten-Launch

> „There were sort of three phases of the work that we did.“ (10:20)

1. **Produktdefinition:** Prototypen auf virtuellen Maschinen.
2. **Verlässlichkeit, Sicherheit, Infrastruktur-Skalierung.**
3. **Qualitäts-Gating:** Freigabe an schrittweise wachsende Testgruppen.

Gilt laut Quelle für agentische Produkte mit Zugriff auf persönliche Daten. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

### Eval-Taxonomie in vier Kategorien

| Kategorie | Was geprüft wird |
|---|---|
| Safety | Prompt Injection, Schaden |
| Capabilities | Browser-Nutzung, Aufgabenerledigung |
| Behavioral | Persönlichkeit, Rückfragen |
| Use Cases | konkrete Anwendungsfälle |

Über 100 Evals insgesamt, für Agenten mit Handlungsvollmacht und privatem Kontext. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (43:00)

### Agentenschwärme für Analyse und Testdaten

Schwärme analysieren das Ökosystem, erzeugen synthetische Multi-Turn-Daten und liefern Berichte für die Evals. Bei unklaren Fehlern prüft ein Schwarm, ob ein Einzelfall oder ein systematischer Bug vorliegt. Setzt Ressourcen für eigene Agenten-Infrastruktur voraus. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (38:20)

### Separate Sicherheitsinstanz als Backstop

Neben dem Haupt-Agenten läuft eine eigene Sicherheitskomponente (Sentinel). Relevant für Agenten mit Zugriff auf Mail, Kalender oder Browser. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (19:10)

### Handgeschriebene Prompts und Spezifikationen

System-Prompt, Verhaltensspezifikation und Prompt-Verteilungen werden verbindlich ohne KI-Hilfe von Hand geschrieben.

> „Our system prompt has to be handwritten.“ (45:15)

[Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

### Diskretion in Multi-Agenten-Szenarien testen

In einem frühen Multiplayer-Test gaben zwei vernetzte Agenten im Gruppenchat einen Arzttermin ihres Nutzers preis und gerieten in Streit. Seitdem gilt: Agenten, die mit Gruppen oder anderen Agenten kommunizieren, brauchen eigene Diskretionstests.

> „We learned about discretion the hard way“ (59:00)

[Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

### Aktivierung gestalten

- **Ideas Tab:** vorgefertigte Starter-Pakete (z. B. Cron-Jobs, Dashboards), die der Nutzer mit „Let's do it“ startet. Ohne Hilfe fragen viele Erstnutzer nur nach dem Wetter. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (49:00)
- **Gestaffeltes Onboarding:** Erklärungen je nach Kohorte, vom Early Adopter bis zum Massenmarkt. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (50:40)

### Feedback-Schleife über den Agenten selbst

Nutzer sagen ihrem Agenten per Sprache oder Text, was nicht passt. Der Agent schickt einen strukturierten Bericht ans Team. Ergänzend lief ab März ein kontinuierliches externes UXR-Panel. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (85:20)

### Ziele statt Aufgaben

Nach Zuckerbergs Kurskorrektur bekam Muse einen Goals Tab und proaktive Funktionen (Dreaming, Studying), in denen der Agent über die Prioritäten des Nutzers nachdenkt, statt nur Aufträge abzuarbeiten. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (21:10)

## Formulierungen und Formate

> „people freeze on the first prompt“ (49:00)

Ihr Bild für die Aktivierungshürde bei offenen Eingabefeldern. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

> „at the point where I'm babysitting an agent, I might as well do it myself“ (82:15)

„Babysitting“ als Maßstab, ab wann ein Agent seinen Nutzen verliert. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

> „we had sort of gotten lost in like the task part“ (21:10)

Selbstkritische Beschreibung der Phase vor dem Schwenk zu Nutzerzielen. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

> „you just tell your Muse and we get it.“ (85:20)

Feedback als Gespräch mit dem eigenen Agenten statt als Formular. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

> „Home automation, which we thought was going to be huge, just wasn't as big.“ (32:05)

Offenes Eingeständnis, dass die eigenen Annahmen über Anwendungsfälle falsch lagen. [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

> „we have to have tiered onboarding.“ (50:40)

[Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)

## Zahlen, die sie nennt

| Zahl | Kontext | Quelle |
|---|---|---|
| 3 Phasen | Entwicklung von Muse: Definition, Absicherung, Qualitäts-Gating | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (10:20) |
| über 100 Evals in 4 Kategorien | Safety, Capabilities, Behavioral, Use Cases | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (43:00) |
| 24 Stunden | Iterationszyklus der Prototypen | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (16:40) |
| ca. 10 Personen | Teamgröße zum Start | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (75:10) |
| unter 100 Personen | spätere Teamgröße | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (75:10) |
| 4 PMs | Produktmanagement für Muse | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (75:10) |
| 7 Monate | Idee bis Launch, Angabe des Hosts mit Verweis auf Presseberichte | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (75:10) |
| 1 Woche vor Launch | Entscheidung gegen das Konzernlogo | [Meta’s Muse](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md) (26:20) |

## Wo Vorsicht geboten ist

- **Nur eine Quelle.** Alle Kernideen beruhen auf einem einzigen Gespräch. Ob sie diese Ideen wiederholt vertritt, ist noch offen.
- **B2C und Konzernmaßstab.** Muse ist ein Consumer-Produkt von Meta. Agentenschwärme, über 100 eigene Evals und direkter Draht zu Zuckerberg sind für die meisten B2B-Teams nicht vorhanden. Die Übertragbarkeit auf B2B Go-to-Market ist nicht belegt.
- **Behauptungen ohne Beleg.** Dass frühe Vertrauensverluste Nutzer dauerhaft vertreiben (12:40), dass Mundpropaganda der wirksamste Aktivierungshebel ist (47:30) und dass Babysitting die Zeitersparnis aufhebt (82:15), wird nicht mit Zahlen gestützt.
- **Handgeschriebene Prompts ohne Messung.** Dass handgeschriebene System-Prompts besser wirken, wird nicht belegt. Es ist eine Teamregel, kein Ergebnis (45:15).
- **Sentinel bleibt eine Blackbox.** Die Architektur der Sicherheitskomponente wird nicht offengelegt, die Methode ist also nur als Prinzip nachbaubar (19:10).
- **Anekdoten.** Logo-Entscheidung (26:20), Multiplayer-Vorfall (59:00) und Zuckerbergs Kurskorrektur (21:10) sind Einzelgeschichten.
- **Fremde Zahlen und Titel.** Die 7 Monate nennt der Host, nicht sie. Die Einordnung als „most successful consumer product this year“ stammt aus dem Episodentitel und ist nicht geprüft.
- **Interessenlage.** Sie spricht als Teil des Muse-Teams über ihr eigenes Produkt.

## Alle Quellen

- 2026-11-17: [Meta’s Muse: Inside the launch of the most successful consumer product this year](../quellen/2026/11/2026-11-17-meta-s-muse-inside-the-launch-of-the-most-successful-consume.md)
