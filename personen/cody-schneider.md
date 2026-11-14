# Cody Schneider

Cody Schneider zeigt, wie man autonome KI-Agenten im B2B-Performance-Marketing aufsetzt: von der Dateninfrastruktur über Anzeigenproduktion in hohem Volumen bis zur Auswertung, welche Motive wirklich Umsatz bringen.

Stand: 2026-11-14 · 1 Quelle

Verkauft: eine Plattform für genau diese Agenten-Workflows im Marketing ([AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)). Im Video wird dazu der Graft-Skill `/static-ads` vorgeführt.

## Kernideen

### 1. Ein Agent ist nur so gut wie seine Daten, Werkzeuge und Rechte
Bevor ein Marketing-Agent sinnvoll arbeitet, braucht er drei Dinge: Zugriff auf Unternehmensdaten, Werkzeuge über APIs und Schreibrechte auf den Werbeplattformen.
> „you need to provide data [...] access to tools [...] access to your ad platforms“

- Drei-Säulen-Modell, 07:30, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md) (Behauptung ohne Beleg)

### 2. Lesen aus dem Warehouse, Schreiben auf die Plattform
Der Agent liest Marketingdaten nie direkt bei Facebook Ads oder Google Ads, sondern nur aus einem eigenen Warehouse. Die Werbe-APIs dienen ausschließlich zum Schreiben.
> „I'm never actually reading the data from Facebook Ads. This is only one directional“

- Pipeline mit Airbyte in ClickHouse, 10:05, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- Gesperrtes Werbekonto nach Tausenden API-Anfragen pro Sekunde, 14:00, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md) (Kundenfall)

### 3. Den Feedback-Loop bis zum Umsatz schließen
Nicht Klick- oder Lead-Kosten zählen, sondern was ein Anzeigenmotiv an Kundenwert einbringt. Dafür werden Werbedaten mit Zahlungsdaten verknüpft und auch die Generierungs-Prompts selbst gespeichert und ausgewertet.
- Lifetime Value je Anzeigenmotiv über Verknüpfung mit dem Zahlungsanbieter, 12:20, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- Jeden Prompt als JSON-Blob mit Performancedaten verknüpfen, 48:30, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)

### 4. Volumen schlägt Handarbeit
Agenten machen Anzeigen so billig, dass statt einzelner Motive ganze Kohorten getestet werden können. Prüf- und Produktionsaufgaben, die für Menschen unmöglich schnell wären, übernimmt das Modell.
> „getting a human to audit 5,000 search terms in 20 seconds is impossible.“

- 5.000 Suchbegriffe in etwa 20 Sekunden auf Kaufabsicht prüfen, 18:40, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- Etwa 5 US-Dollar pro KI-UGC-Video statt 500 US-Dollar und mehr, 39:00, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- Von 10 auf 300 Anzeigen pro Monat für Metas Andromeda, 47:30, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md) (Kundenfall)

### 5. Generative Modelle nie raten lassen
Wer einem Modell zu wenig Vorgaben gibt, bekommt Erfundenes und zahlt dafür. Deshalb immer konkrete Vorlagen mitgeben: fertige Tonspur, Referenzbild, echtes Foto, und für Bearbeitungen ein Modell, das das Original erhält.
> „If I just send the script straight to Seedance, it's going to give me just like whatever it invents at that moment.“

- Skript, MP3 und Referenzbild gleichzeitig an Seedance, 32:00, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- Echtes Creator-Foto als Vorlage gegen den Plastik-Look, 36:50, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- ChatGPT Image 2.5 für gezielte Änderungen, 46:00, [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)

## Methoden und Abläufe

### Daten-Pipeline für Marketing-Agenten
1. Daten aus Facebook Ads, Google Analytics, HubSpot und PostHog per Airbyte in ein Warehouse wie ClickHouse laden.
2. Den Agenten nur dort lesen lassen.
3. Werbe-APIs nur für Schreibvorgänge freigeben.
4. Werbedaten mit dem Zahlungsanbieter verknüpfen, um den Lifetime Value je Motiv zu sehen.

Voraussetzung: technische Ressourcen für eine Pipeline und eine durchgehende Datenkette von Anzeige bis Zahlung. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 10:05 und 12:20

### Suchbegriff-Audit bei Google Ads
Ein LLM prüft große Mengen Suchbegriffe auf Kaufabsicht, bevor Budget auf unpassende Landingpages fließt. Sinnvoll bei Suchkampagnen mit großem Begriffsvolumen. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 18:40

### Static Ads in fester Reihenfolge
1. Markenstil von der Website auslesen.
2. Facebook-Werbebibliothek durchsuchen.
3. Schmerzpunkte auf Reddit recherchieren.
4. Fünf Konzepte vorschlagen.
5. Grafiken generieren und per API in ein neues Anzeigen-Set laden.

Gezeigt mit dem Graft-Skill `/static-ads` für Meta. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 23:50

### KI-UGC-Video produzieren
1. Skript schreiben, mit einem Voice-Clone als MP3 vertonen.
2. Tonspur Wort für Wort transkribieren, falsch ausgesprochene Markennamen über die Zeitstempel finden und nur diese Sequenz ersetzen.
3. Avatar aus einem echten Creator-Foto ableiten, nur Hintergrund, Alter oder Ethnie variieren.
4. Skript, MP3 und hochauflösendes Referenzbild gleichzeitig an das Videomodell (Seedance) übergeben.
5. In 480p rendern und mit FFmpeg hochskalieren, mit leichtem Weichzeichner.

[AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 32:00 bis 36:50

### UGC mit echten Menschen skalieren
Der Agent schickt Skripte über die APIs von Tribe oder SideShift an menschliche UGC-Creator. Ein Creator-Manager bleibt als Freigabestufe dazwischen.
> „We pay them like $40 a video as an example“

[AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 40:00

### Compliance-Schleife in regulierten Branchen
Ein Agent mit Bildmodell prüft jede erzeugte Grafik gegen Compliance-Regeln und korrigiert sie in zwei bis drei rekursiven Durchläufen vor der Freigabe. Genannt für Finanzdienstleister. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 43:50 (Kundenfall)

### Kohorten-Testing für Meta Andromeda
Anzeigen nicht einzeln, sondern in Kohorten zu 30 ausspielen und das Volumen stark erhöhen. Jeden Generierungs-Prompt als JSON-Blob speichern und mit der Performance verknüpfen, um zu sehen, welche Parameter wirken.
> „I can store that JSON blob in a database.“

[AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 47:30 und 48:30

## Formulierungen und Formate

**Hook-Muster: Problem, dann Mechanismus.** Vom Agenten erzeugt für ein Ideen-Tool (B2B-Software, Static Ad):
> „stop guessing which idea to build. Every idea is scored on demand, pain, and timing.“

[AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 26:50

**Hook-Muster: konkretes Alltagsproblem der Zielgruppe benennen.** Vom Agenten erzeugt für einen Code-Editor:
> „finally understand the code nobody wrote down.“

[AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 42:00

**„One directional“** als Kurzformel für das Prinzip, Werbeplattformen nur zu beschreiben und nie auszulesen. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 14:00

## Zahlen, die sie nennt

| Zahl | Kontext | Quelle |
|---|---|---|
| 5.000 Suchbegriffe in ca. 20 Sekunden | LLM-Audit auf Kaufabsicht bei Google Ads | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 18:40 |
| ca. 14 US-Dollar | ein 1080p-Render bei Seedance; deshalb Render in 480p plus Hochskalierung | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 34:00 |
| ca. 4,75 US-Dollar, künftig ca. 3 US-Dollar | eine KI-UGC-Videoanzeige im eigenen Setup | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 39:00 |
| 500 US-Dollar und mehr | geschätzte Kosten derselben Anzeige mit Creator, Cutter und Designer | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 39:00 |
| ca. 40 US-Dollar | Pauschale pro Video an menschliche UGC-Creator über Tribe oder SideShift | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 40:00 |
| 2 bis 3 Durchläufe | rekursive Compliance-Korrektur pro Grafik | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 43:50 |
| 10 auf 300 Anzeigen pro Monat, Kohorten zu 30 | Skalierung für Meta Andromeda | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 47:30 |
| 2 Demos zu je ca. 50 statt ca. 150 US-Dollar | eine Kohorte bei einem B2B-SaaS-Kunden | [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 47:30 |

## Wo Vorsicht geboten ist

- **Interessenkonflikt.** Cody Schneider vertreibt eine Plattform für genau diese Workflows. Die Aussage, KI-Avatare performten in Meta-Ads teils besser als echte Menschen, ist im Video nicht durch A/B-Daten belegt. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md)
- **Kostenvergleich unvollständig.** Die rund 5 US-Dollar pro Video enthalten weder Abos noch Engineering-Aufwand für Pipeline und Agenten. Der Vergleichswert von 500 US-Dollar ist eine Schätzung. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 39:00
- **Einzelfall statt Studie.** Das Ergebnis mit Demos zu 50 statt 150 US-Dollar stammt aus einer Kohorte bei einem Kunden, ohne Angaben zu Laufzeit und Budget. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 47:30
- **Drei-Säulen-Modell ohne Beleg.** Die Voraussetzungen für Agenten werden als gesetzt präsentiert, nicht hergeleitet. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 07:30
- **Rechte und Kennzeichnung.** Avatare aus echten Creator-Fotos abzuleiten wirft Fragen zu Bildrechten und Kennzeichnungspflicht von KI-Werbung auf, die die Quelle nicht behandelt. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 36:50
- **Compliance-Agent.** Ob die automatische Prüfschleife eine fachliche oder juristische Prüfung in regulierten Branchen ersetzen kann, bleibt offen. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 43:50
- **Ratenlimits und Sperren.** Agenten mit direktem Lesezugriff auf Werbe-APIs können Konten sperren lassen. Wer kein Warehouse oder keinen Cache hat, sollte Agenten dort nicht lesen lassen. [AI Agents too good at marketing](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md), 14:00
- **Werkzeugstand.** Genannte Modelle und Preise (Seedance, ChatGPT Image 2.5) ändern sich schnell und spiegeln den Stand November 2026.

## Alle Quellen

- 2026-11-14 · [AI Agents are too good at marketing now](../quellen/2026/11/2026-11-14-ai-agents-are-too-good-at-marketing-now.md) · Learnings L-20261114-017 bis L-20261114-035
