# Edge0-145B: Frontier-KI-Fähigkeiten auf dem eigenen Rechner

> **Quelle:** [Edge0-145B: Frontier AI Capabilities on Your Own Computer](https://edge0.ai/blog/introducing-edge0-145b-frontier-ai-capabilities-on-your-own-computer) · edge0 (Unternehmensblog), edge0 · Artikel mit Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50475713) (338 Punkte) · 2026-11-14
> **Sprecher verkauft:** Open-Weights-Modelle Edge0-145B und Edge0-120B, Inferenz-Framework, Deployment-Tools, Edge0 App · **Zielmarkt der Aussagen:** Entwickler und Unternehmen, die große Sprachmodelle lokal betreiben wollen · **Beweislage:** ausschließlich Herstellerangaben aus interner Evaluation, technischer Report steht aus.

## Worum es geht
Kann ein Modell mit 145 Mrd. Parametern auf einem Laptop laufen und bei Agenten- und Coding-Aufgaben mit Cloud-Modellen mithalten? edge0 sagt ja und begründet das mit einer Architektur, die von Anfang an für lokale Ausführung gebaut ist. Relevant ist der Text für Teams, die lokale oder souveräne KI-Infrastruktur planen und Herstellerbehauptungen dazu prüfen müssen.

## Was man anwenden kann
1. **Speicherbedarf statt Parameterzahl prüfen.** Edge0-145B hat 145 Mrd. Parameter, pro Inferenzschritt rechnen nur etwa 10 Mrd. mit (Sparse Experts). Berichtet werden 29 GB Spitzenspeicher, Zielhardware ist ein Laptop mit 48 GB. Bei der Hardwareplanung zählt der gemessene Speicher im konkreten Setup, nicht die Modellgröße im Namen.

2. **Drei Speicherstufen in die Hardwareplanung einrechnen.** Häufig genutzte Experten liegen im GPU-Speicher, eine Expertenbibliothek von etwa 40 GB im Systemspeicher, etwa 48 GB Vokabulardaten auf der SSD. Wer das Modell betreiben will, braucht also genug RAM und eine schnelle SSD, nicht nur GPU-Speicher. Wie das zu „29 GB Spitzenspeicher“ passt, erklärt der Artikel nicht. Vor Anschaffung nachmessen.

3. **Geteilte Matrizen als Architekturhebel verstehen.** Je 64 Experten teilen sich zwei große Matrizen, jeder Experte behält nur einen kleinen eigenen Parametersatz. Die Expertenzahl bleibt gleich, gespeichert und bewegt werden deutlich weniger Gewichte. Das Modell wird von Beginn an so trainiert, lokale Ausführung ist kein nachträgliches Komprimieren eines Cloud-Modells.

4. **CPU mitrechnen lassen und Speculative Decoding nutzen.** Die GPU rechnet gecachte Experten, die CPU parallel den Rest. Speculative Decoding prüft mehrere Kandidaten-Tokens auf einmal und verteilt so die Kosten des Gewichtelesens auf mehr Ausgabe-Tokens. Beides ist ein übertragbares Muster für Modelle, die aus langsamem Speicher geladen werden.

5. **Hardware-Kompatibilität vor dem Test klären.** Der Artikel spricht von einem „kompatiblen Laptop“ wie einem MacBook Pro, ohne Chip oder RAM zu nennen. Ein Kommentator schreibt, das Modell sei als NVFP4 ausgeliefert und laufe vermutlich nur auf Nvidia Blackwell mit CUDA 13, GGUF-Dateien gebe es nicht. Das ist nicht geprüft. Wer Apple Silicon oder AMD nutzt, sollte die Unterstützung durch die Edge0-Engine zuerst verifizieren.

6. **Benchmarks nach Aufgabentyp lesen.** Stark ist Edge0-145B laut Tabelle bei Agenten und Coding (DeepSWE 1.1: 64,6, Terminal-Bench 2.1: 86,52). Bei Wissen und Reasoning liegt es hinter Claude-Opus-4.6 (Max) und Qwen3.8-Flash-Next (HLE 35,4 gegen 40,0 und 35,9). Für die eigene Auswahl zählt der Benchmark, der dem eigenen Einsatz am nächsten kommt.

7. **Den Harness mitbewerten.** Ein Kommentator berichtet, Context Pruning und das Reparieren fehlerhafter Tool-Calls hätten Qwen 27B auf Terminal-Bench 2.1 von 73 auf 85 gehoben. Das liegt nahe am Wert von Edge0-145B. Welchen Harness edge0 nutzt, steht nicht im Artikel. Wer lokale Modelle vergleicht, sollte den Harness konstant halten.

8. **Feste Prüfansicht in Agenten-Schleifen.** In der Blender-Demo rendert das Modell einen 20-Sekunden-Flug entlang eines festen Kamerapfads. Überschneidungen, Verdeckungen und falsche Proportionen werden so sichtbar, das Modell prüft die Renders und korrigiert. Das Muster lässt sich auf andere visuelle Agentenaufgaben übertragen.

9. **Lizenz und Kosten selbst prüfen.** Veröffentlicht werden Gewichte, Framework, Deployment-Tools und eine App. Eine Lizenz nennt der Artikel nicht, ebenso keine Trainingsdaten oder Trainingscode. Für Souveränitätsfragen heißt das: Open Weights, nicht Open Source. Das Kostenargument „keine Token-Gebühren“ gilt nur bei vorhandener Hardware, eine Gesamtkostenrechnung fehlt.

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 145 Mrd. / ca. 10 Mrd. | Parameter gesamt / aktiv pro Inferenzschritt | Herstellerangabe |
| 29 GB (an anderer Stelle 28 GB) | Spitzenspeicher Edge0-145B, Unterschied unerklärt | Herstellerangabe |
| über 1.100 / über 80 Tokens/s | Prefill / Decode auf nicht spezifiziertem Laptop, ca. 120 W | Herstellerangabe |
| ca. 40 GB / ca. 48 GB | Expertenbibliothek im RAM / Vokabulardaten auf SSD | Herstellerangabe |
| 64,6 | DeepSWE 1.1, vor Qwen3.8-Flash-Next 58,7 und DeepSeek-V4-Flash-0731 54,4; kein Claude-Wert | Interne Evaluation |
| 86,52 | Terminal-Bench 2.1, vor Qwen3.8-Flash-Next 83,3, DeepSeek 82,7, Claude 78,2 | Interne Evaluation |
| 90,4 / 35,4 | GPQA-Diamond / HLE, jeweils hinter Claude (91,3 / 40,0) und Qwen3.8-Flash-Next (91,7 / 35,9) | Interne Evaluation |
| 80,6 / 79,3 | IFBench / AA-LCR; bei AA-LCR liegen Edge0-120B, Qwen3.8-27B und Muse Glimmer höher | Interne Evaluation, Fremdwerte aus anderen Quellen |
| 72,8 gegen 71,7 | Mittelwert sechs Benchmarks Edge0-145B gegen Qwen3.8-Flash-Next | Herstellerangabe, Vergleichsspeicher geschätzt |
| 29 GB gegen ca. 70 GB | Speicher Edge0-145B gegen geschätzt Qwen3.8-Flash-Next bei 4 Bit, rund 40 % | Herstellerangabe |
| +53,1 % / +18,5 % | Relativer Vorsprung auf Qwen3.8-27B bei DeepSWE / Terminal-Bench, absolut 22,4 und 13,52 Punkte | Herstellerangabe |
| 37+ Tokens/s bei ca. 2,5 GB | Edge0-35B auf iPhone 18 Pro Max, nicht mit 145B vergleichbar | Herstellerangabe |
| 12.000 bis 18.000 US-Dollar, ein Monat | Manuelle Kosten der Manhattan-Szene in Blender | Behauptung ohne Beleg |
| über 150 US-Dollar | Token-Kosten derselben Aufgabe mit führendem Cloud-Modell | Behauptung ohne Beleg |
| 73 auf 85 | Terminal-Bench 2.1 von Qwen 27B durch Harness-Verbesserungen | Anekdote eines Kommentators |

## Grenzen und Widerspruch
- **Alles ist intern gemessen.** Werte für Edge0, Qwen, DeepSeek und Claude stammen aus edge0s eigener Evaluation. Setup, Hardware und Reproduktionsanleitung sollen erst mit einem technischen Report kommen. Ein Kommentator macht seine Begeisterung davon abhängig, dass Dritte die Zahlen bestätigen.
- **Frontier-Anspruch ist eng gefasst.** Die Überschrift spricht von Konkurrenz zu Frontier-Cloud-Modellen, der Text schränkt auf „specific frontier cloud models“ ein. Einzige Cloud-Referenz ist Claude-Opus-4.6 (Max), und das liegt bei Wissen und Reasoning vorn.
- **Vergleichsbasis ist geschätzt.** Speicherwerte der Vergleichsmodelle sind Schätzungen für Standard-4-Bit-Deployment. Der Vorsprung im Mittelwert auf Qwen3.8-Flash-Next beträgt nur 1,1 Punkte. Die Grafiken haben eine Achse, die nicht bei null beginnt, bzw. eine gemischt logarithmisch-lineare Skala.
- **Hardware unklar.** Laptop-Modell, Chip und RAM sind nicht genannt. Der NVFP4-Einwand widerspricht der MacBook-Aussage, ist aber selbst nur vermutet.
- **Herkunft unklar.** Ein Kommentator fragt, ob das Modell von Qwen3.8-Flash-Next abgeleitet ist. Basismodell und Trainingsdaten nennt der Artikel nicht. Andere Kommentatoren vermissen Angaben zum Unternehmen selbst.
- **Demos ohne Qualitätsurteil.** Video- und Blender-Demos haben keine Berechnungsbasis für Kosten und Zeit. Ein Kommentator bezweifelt, dass Agenten-Ergebnisse in Blender für Menschen weiterbearbeitbar sind, weil Aufräumen die Zeitersparnis auffresse.
- **Material unvollständig.** Der Artikel bricht im Abschnitt zu Spiele-Demos ab. Lizenz, kommerzielle Nutzung, EU-Einschränkungen und unterstützte Sprachen fehlen.
