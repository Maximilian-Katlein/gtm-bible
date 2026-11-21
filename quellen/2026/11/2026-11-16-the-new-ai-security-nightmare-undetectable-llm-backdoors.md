# Das neue KI-Sicherheitsproblem: unerkennbare Hintertüren in LLMs

> **Quelle:** [The New AI Security Nightmare: Undetectable LLM Backdoors](https://www.youtube.com/watch?v=rloMMrPNDPU) · Carl, Internet of Bugs · Video · 2026-11-16
> **Sprecher verkauft:** Patreon-Abonnements, Substack-Essays; das Video enthält ein bezahltes Sponsoring-Segment für Serp API · **Zielmarkt der Aussagen:** Enterprise (09:40) · **Beweislage:** stützt sich auf eingeblendete arXiv-Papers, die im Video nicht technisch nachvollzogen werden.

## Worum es geht
Wie gefährlich sind Hintertüren, die per Post-Training in ein Sprachmodell eingebaut werden, und was kann ein Team dagegen tun, wenn man sie nicht erkennen kann? Das Video richtet sich an Entwickler und Verantwortliche, die KI-Agenten mit Zugriff auf Code, Dateien und Werkzeuge betreiben, besonders bei Modellen aus fremder Hand.

## Was man anwenden kann
1. **Bedrohungsmodell anpassen: Das Modell selbst ist Teil der Lieferkette.** Laut Carl lässt sich bedingte Codeausführung in ein Modell hineintrainieren. Es verhält sich fast immer normal und handelt nur bei einem bestimmten Auslöser bösartig (00:59). Wer Modellgewichte von Dritten bezieht, sollte sie deshalb wie eine Software-Abhängigkeit behandeln. Als Rahmen blendet Carl die NIST-Vorgaben zur Software-Lieferkette nach Executive Order 14028 ein (07:26).

2. **Sicheres Dateiformat ist notwendig, aber nicht ausreichend.** Bis etwa 2020 wurden Modellgewichte im Python-Pickle-Format verteilt, das beim Laden beliebigen Code ausführen kann. Um 2022 kam das Format SafeTensors auf (05:16). Prüfen: Lädt Ihre Pipeline noch Pickle-Dateien? Die Pointe des Videos: SafeTensors schließt diese Lücke, schützt aber nicht vor einer Hintertür, die in den Gewichten selbst steckt.

3. **Agenten nach dem Prinzip der minimalen Rechte einrichten.** Ein Agent bekommt nur die Informationen, Werkzeuge und Berechtigungen, die er für seine Aufgabe zwingend braucht (08:11). Praktisch heißt das: kein pauschaler Dateisystemzugriff, keine Geheimnisse im Arbeitsverzeichnis, kein offener Netzwerkzugang, wenn die Aufgabe ihn nicht verlangt.

4. **Alle Agentenaktionen überwachen und blockieren können.** Carl fordert, jede Aktion eines Agenten zu protokollieren und unbefugte Vorgänge zu stoppen (08:31). Konkreter Prüffall aus dem Video: Ein Agent versucht, die .env-Datei an einen externen Server zu senden. Wird das nicht erkannt und verhindert, ist das Monitoring unzureichend. Als Beispiel für einen Ansatz zur Agentenabwehr blendet Carl Ciscos Project Quarry ein (08:34).

5. **Geheimnisse nicht in .env-Dateien ablegen.** Das Angriffsbeispiel zielt genau auf diese Datei (06:22). Carl verweist auf ein eigenes älteres Video, das .env-Dateien grundsätzlich kritisiert (08:52). Wer Agenten im Repository arbeiten lässt, sollte Zugangsdaten aus dem für den Agenten lesbaren Bereich entfernen.

6. **Ausgaben mit Modellen verschiedener Anbieter gegenprüfen.** Mehrere LLMs von unabhängigen Herstellern sollen sich gegenseitig kontrollieren. Zwei Instanzen desselben Anbieters reichen laut Carl nicht (08:58). Kosten und Latenz dieses Ansatzes nennt das Video nicht.

7. **Rechercheablauf über Zitationsnetz (Sponsoring-Segment).** Carl extrahiert die Quellen eines Papers, sucht per Serp API weitere Arbeiten, die dieselben Quellen zitieren, und lädt die Funde in Google NotebookLM, um nur gegen diese Texte Fragen zu stellen (03:40, 04:10). Ziel ist, Auswahlverzerrung bei der Recherche zu verringern. Serp API bietet laut Video auch einen Open-Source-MCP-Server; Carl lässt Modelle Tool-Aufrufe aber lieber als ausführbaren Code schreiben (04:40). Dieser Teil ist bezahlte Werbung.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| bis ca. 2020 | Verteilung von Modellgewichten im Pickle-Format | Aussage des Sprechers, ohne Beleg (05:16) |
| ca. 2022 | Aufkommen des SafeTensors-Formats | Aussage des Sprechers, „something like 2022“ (05:16) |
| 2017 | frühes Paper zu Backdoors durch Data Poisoning (Chen et al.) | eingeblendet (00:50) |
| Oktober 2024 | Paper zur Persistenz von Backdoors im Agenten-Post-Training (Zhao et al.) | eingeblendet (00:46) |
| 253 | kostenlose Search Credits bei Serp API, ohne Kreditkarte | Herstellerangabe im Sponsoring (05:00) |
| seit Ende der 1980er | Berufserfahrung des Sprechers | Selbstauskunft (01:28) |

## Wortlaute
- „someone can train conditional arbitrary code execution into a model so that it behaves perfectly normally virtually all the time“ (00:59). Kernthese des Videos.
- „that back door didn't seem to be detectable and it persisted through later retraining.“ (06:40). Begründung, warum Nachtraining nicht als Schutz taugt.
- „Two different versions of chat GPT can't police each other and the same goes for two instances of Claude.“ (08:58). Regel für die Kreuzprüfung: verschiedene Anbieter.

## Grenzen und Widerspruch
- Die Kernaussagen zur Unerkennbarkeit und Persistenz (06:40) stützen sich auf eingeblendete Papers. Das Video erklärt weder Versuchsaufbau noch Erfolgsraten noch, unter welchen Bedingungen die Persistenz nach SFT oder DPO gemessen wurde. Wer das als Entscheidungsgrundlage nutzt, muss die Papers selbst lesen.
- Das .env-Beispiel (06:22) stammt laut Video aus einer Studie; welcher genau, wird nicht eindeutig zugeordnet.
- Die Studien zu KI-generiertem Code (00:18, 00:24) werden nur gezeigt, nicht ausgewertet.
- Die Gegenmaßnahmen sind bekannte Sicherheitsgrundlagen. Carl sagt selbst: Für Organisationen mit wertvollen Systemen ist das Problem ein Albtraum, für alle anderen bedeutet es vor allem, Grundregeln konsequent umzusetzen (09:40).
- Für die Multi-Anbieter-Kreuzprüfung fehlen Kosten, Latenz und Belege zur Wirksamkeit.
- Der Rechercheablauf mit Serp API und NotebookLM ist Teil eines bezahlten Sponsorings mit Affiliate-QR-Code. Die Bewertung des Werkzeugs ist entsprechend zu lesen.
