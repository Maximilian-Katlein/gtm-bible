# Carl

Carl erklärt Sicherheitsrisiken beim Bauen mit KI-Agenten und Sprachmodellen und übersetzt sie in konkrete Schutzmaßnahmen für Teams, die Agenten produktiv einsetzen.

Stand: 2026-11-16 · 1 Quelle

Verkauft: Keine eigenen Produkte, Kurse oder Firmen in den bisherigen Quellen genannt. Im ausgewerteten Video gibt es ein bezahltes Sponsoring für Serp API.

## Kernideen

### 1. Modellgewichte gehören ins Bedrohungsmodell der Software-Lieferkette

Per Post-Training lässt sich bedingte Codeausführung in ein LLM einbauen. Das Modell verhält sich fast immer normal und handelt nur bei einem bestimmten Auslöser bösartig. Wer fremd bezogene Modelle oder Gewichte einsetzt, muss sie deshalb wie jede andere Abhängigkeit aus der Lieferkette prüfen. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 00:59)

> someone can train conditional arbitrary code execution into a model so that it behaves perfectly normally virtually all the time

Laut einem im Video zitierten Paper war eine solche Hintertür vor dem Auslösen nicht erkennbar und überstand späteres Nachtraining. Eigenes Fine-Tuning eines fremden Modells gilt damit nicht als Bereinigung. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 06:40)

> that back door didn't seem to be detectable and it persisted through later retraining.

Sichere Dateiformate lösen das Problem nicht: Das Pickle-Format erlaubt beim Laden beliebige Codeausführung, SafeTensors kam um 2022 als sichere Alternative auf. SafeTensors schützt aber nicht vor Hintertüren, die in den Gewichten selbst trainiert sind. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 05:16)

Als Ordnungsrahmen nennt Carl Executive Order 14028 Section 4 und die NIST Software Supply Chain Security Guidance; Modelle lassen sich in diese Prüfprozesse einordnen. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 07:26)

### 2. Weil Hintertüren nicht erkennbar sind, zählt die Schadensbegrenzung

Da sich ein kompromittiertes Modell vorab nicht zuverlässig entdecken lässt, setzt Carl auf Maßnahmen rund um das Modell: minimale Rechte, lückenloses Monitoring, keine Geheimnisse im Arbeitsbereich und gegenseitige Kontrolle durch unabhängige Anbieter (Details unter „Methoden und Abläufe“). ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 08:11 bis 08:58)

### 3. Die Bedrohung ist real, aber ungleich verteilt

LLM-Hintertüren sind vor allem für Organisationen mit wertvollen Systemen und komplexer Agenten-Infrastruktur ein ernstes Problem. Für alle anderen bedeuten sie in erster Linie, bekannte Sicherheitsgrundlagen konsequent umzusetzen. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 09:40)

> people who have lots of really expensive things to protect are going to find it to be a nightmare.

## Methoden und Abläufe

### Agenten absichern

1. **Minimale Rechte.** Agenten erhalten nur die Informationen, Werkzeuge und Berechtigungen, die für ihre Aufgabe zwingend nötig sind. Das begrenzt den Schaden, falls ein Modell eine Hintertür enthält. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 08:11)

   > only allowing your LLMs or agents to have access to the information, tools and permissions that they absolutely must have

2. **Alles protokollieren, Unbefugtes blockieren.** Sämtliche Aktionen von Agenten werden geloggt, unbefugte Vorgänge aktiv gestoppt. Prüffall: Ein Versuch, die .env-Datei nach außen zu senden, muss erkannt und blockiert werden. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 08:31)

3. **Keine Geheimnisse in .env-Dateien im Arbeitsbereich.** Genau diese Datei war im gezeigten Angriffsbeispiel das Ziel. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 08:52)

4. **Gegenseitige Prüfung durch unabhängige Anbieter.** Ausgaben werden von LLMs verschiedener Anbieter kontrolliert. Zwei Instanzen desselben Anbieters gelten nicht als unabhängige Kontrolle. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 08:58)

   > Two different versions of chat GPT can't police each other and the same goes for two instances of Claude.

*Entwicklung über Zeit: Carl verweist im Video auf ein eigenes älteres Video, in dem .env-Dateien schon grundsätzlich kritisiert werden. Dieses Video ist noch nicht als Quelle erfasst; die Kritik ist also älter als das Backdoor-Argument und wird hier nur neu begründet.*

### Recherche über Quellenkorpus

1. **Zitationsnetz abgehen.** Quellen eines Papers extrahieren, per Suche weitere Arbeiten finden, die dieselben Quellen zitieren, und so Auswahlverzerrung verringern. Im Video mit Serp API umgesetzt. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 03:40)
2. **Fragen gegen einen festen Bestand stellen.** Die gesammelten Fachartikel in Google NotebookLM laden, damit Antworten nur aus diesem Korpus kommen und nicht aus dem allgemeinen Modellwissen. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 04:10)

*Hinweis: Die Werkzeugempfehlung für Serp API stammt aus einem bezahlten Sponsoring-Segment.*

### Werkzeuganbindung: Code statt MCP

Carl lässt Modelle Tool-Aufrufe lieber als ausführbaren Code schreiben, statt sie über MCP anzubinden. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 04:40)

## Formulierungen und Formate

- **Konkretes Angriffsbeispiel als Anker.** Carl macht das abstrakte Risiko an einem greifbaren Szenario fest: Eine bestimmte Zeichenkette in einem Code-Kommentar löst aus, dass das Modell die .env-Datei an eine externe URL hochlädt. Dasselbe Szenario dient später als Prüffall für das Monitoring. ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 06:22)

  > It would upload the .env file to a remote URL.

- **Drastische, eingängige Handlungsanweisungen.** ([Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 08:31)

  > monitor the hell out of everything that your agents do

- **Bedrohung einordnen statt dramatisieren.** Auf die Warnung folgt eine Abstufung, für wen sie wirklich gilt (siehe Kernidee 3).

## Zahlen, die sie nennt

| Zahl | Kontext | Quelle |
|---|---|---|
| um 2022 | SafeTensors kommt als sichere Alternative zu Pickle auf | [Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 05:16 |
| 14028, Section 4 | US Executive Order als Rahmen für Lieferkettensicherheit | [Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 07:26 |
| 253 | kostenlose Search Credits bei Serp API ohne Kreditkarte (Herstellerangabe im Sponsoring) | [Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md), 04:40 |

## Wo Vorsicht geboten ist

- **Keine Belege im Video.** Alle Kernaussagen zu Hintertüren sind als Behauptung ohne Beleg erfasst. Das zitierte Paper wird erwähnt, seine Studiendetails werden aber nicht dargelegt. Vor einer Übernahme in eigene Sicherheitskonzepte sollte das Original geprüft werden.
- **Kosten der Mehr-Anbieter-Kontrolle offen.** Wie teuer und wie langsam die gegenseitige Prüfung durch mehrere LLM-Anbieter wird, bleibt im Video unbeantwortet. Der Ansatz passt vor allem zu kritischen Workflows mit entsprechendem Budget.
- **Sponsoring.** Die Recherche-Methode wird mit Serp API vorgeführt, und Serp API bezahlt das Segment. Die Methode selbst funktioniert auch mit anderen Suchwerkzeugen.
- **US-Fokus beim Regelwerk.** Executive Order 14028 und NIST sind vor allem für Organisationen mit US-Bezug verbindlich; für den deutschsprachigen Raum nennt Carl keinen entsprechenden Rahmen.
- **Relevanz abhängig von der Größe.** Carl selbst stuft das Risiko für Organisationen ohne wertvolle Systeme deutlich niedriger ein. Wer klein ist, sollte zuerst die Grundlagen umsetzen statt aufwendige Spezialabwehr.

## Alle Quellen

- [The New AI Security Nightmare: Undetectable LLM Backdoors](../quellen/2026/11/2026-11-16-the-new-ai-security-nightmare-undetectable-llm-backdoors.md) (2026-11-16)
