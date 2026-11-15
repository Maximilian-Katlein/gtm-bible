# Mirage: Vision-Modell für Bildverständnis und strukturierte Extraktion (Cactus-Compute/mirage)

> **Quelle:** [Mirage (Cactus-Compute/mirage)](https://huggingface.co/Cactus-Compute/mirage) · Cactus Compute · Model Card · 2026-11-14
> **Sprecher verkauft:** Open-Weight-Vision-Modell Mirage (Apache-2.0) mit eigener Engine und dem Python-Paket cactus-compute · **Zielmarkt der Aussagen:** Entwickler, die Bildverständnis und strukturierte Extraktion einbauen, in der Card nicht näher eingegrenzt · **Beweislage:** ausschließlich Herstellerangaben, keine Benchmarks, keine Modellgröße.

## Worum es geht
Die Card stellt Mirage vor, ein Bild-zu-Text-Modell von Cactus Compute, das laut Hersteller Bilder beschreibt, Objekte erkennt, Text liest und Inhalte strukturiert extrahiert. Sie beantwortet vor allem die Frage, wie man das Modell mit wenigen Zeilen Python startet. Für eine Auswahlentscheidung im B2B-Einsatz, etwa für Dokumentenextraktion oder souveräne On-Premise-Setups, liefert sie fast keine prüfbaren Daten. Der Eintrag zeigt deshalb vor allem, was man vor einem Einsatz selbst klären muss.

## Was man anwenden kann
1. **Schnelltest in drei Zeilen.** Installation mit `pip install -U cactus-compute`, dann `import cactus` und `cactus.Mirage().describe("photo.png")`. Das liefert eine Bildbeschreibung. Gezeigt ist nur diese eine Methode, also nur der Fall Szenenbeschreibung.
2. **Fähigkeitsliste als Testplan nutzen, nicht als Zusage.** Die Tags nennen acht Aufgaben, darunter Objekterkennung, Zero-Shot-Klassifikation, Segmentierung, Visual Question Answering und Document Question Answering. Die Übersichtsgrafik ergänzt OCR, räumliche Beziehungen und „decisions“, ohne zu erklären, was Letzteres bedeutet. Alles davon ist Selbstzuordnung. Wer eine dieser Aufgaben braucht, baut zuerst einen eigenen Testsatz mit echten Bildern oder Dokumenten und misst.
3. **Deutsch prüfen, bevor man darauf baut.** Deklariert sind Englisch, Deutsch, Französisch, Spanisch, Italienisch, Niederländisch und Polnisch. Offen bleibt, ob das für Prompts, Ausgabetext oder die Texterkennung im Bild gilt. Für deutsche Rechnungen, Lieferscheine oder Datenblätter heißt das: Umlaute, Zahlenformate und Fachbegriffe gezielt testen.
4. **Extraktions-API außerhalb der Card nachlesen.** Wie man Detektion, Segmentierung, OCR oder eine JSON-Ausgabe nach Schema aufruft, steht nicht in der Card. Die verlinkte Python-API-Doku liegt unter einem Pfad namens needle-python-docs, wird also offenbar mit einem anderen Cactus-Modell geteilt. Für den B2B-Kernfall strukturierte Extraktion ist das der erste Lesepunkt.
5. **Download beim ersten Aufruf einplanen.** Engine und Weights werden beim ersten Gebrauch automatisch geladen und gecacht. Cache-Ort, Downloadgröße und Offline-Betrieb sind nicht beschrieben. In abgeschotteten oder souveränen Umgebungen müssen Engine und Weights vorab bezogen und der Betrieb ohne Netz selbst verifiziert werden.
6. **Runtime-Bindung vor Stack-Entscheidung klären.** Dokumentiert ist nur der Weg über cactus-compute. Das Repo enthält mirage.cact, mirage.safetensors und die Modellkonfiguration. Was .cact ist, erklärt die Card nicht, der Name deutet auf ein Cactus-eigenes Format hin (Annahme). Ein Laden über Transformers, vLLM oder Ollama ist nicht gezeigt. Wer einen bestehenden Serving-Stack hat, prüft die Kompatibilität selbst.
7. **Lizenz an zwei Stellen prüfen.** Das Metadatenfeld sagt Apache-2.0, was kommerzielle Nutzung grundsätzlich erlaubt. Die Card selbst äußert sich nicht zu kommerziellem Einsatz oder EU. Runtime-Binaries und Plattformliste liegen in einem separaten Repo (Cactus-Compute/cactus), Quellcode auf GitHub unter cactus-compute/cactus. Lizenztext im Modell-Repo und Lizenz der Runtime getrennt lesen.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 2026-11-05 | Anlagedatum des Repos laut Hub-Metadaten (19:01 UTC) | Hub-Metadaten |
| 7 | Deklarierte Sprachen, inklusive Deutsch | Herstellerangabe |
| 8 | Deklarierte Aufgaben laut Tags | Herstellerangabe |
| 254 bzw. 255 | Likes auf Hugging Face, je nach Abrufzeitpunkt | Hub-Metadaten |
| 18.959 | Downloads laut Hub-Metadaten | Hub-Metadaten, kann automatisierte Abrufe enthalten |
| keine | Parameterzahl und Datentyp, das safetensors-Feld ist leer | fehlt |

## Wortlaute
- „A vision model for image understanding and structured extraction.“ Die gesamte Produktbeschreibung der Card, ein Satz ohne Beleg.
- „pip install -U cactus-compute“ Der einzige dokumentierte Installationsweg.
- „print(cactus.Mirage().describe("photo.png"))“ Das einzige Codebeispiel, es deckt nur Bildbeschreibung ab.
- „The package downloads and caches the engine and weights on first use.“ Der Hinweis, der für Air-Gap- und Sovereign-Setups entscheidend ist.

## Grenzen und Widerspruch
- **Keine Benchmarks.** Weder Benchmarkname noch Vergleichsmodell noch Evaluationsmethode. Die Fähigkeitsliste ist damit Behauptung ohne Beleg.
- **Keine Eckdaten.** Es fehlen Parameterzahl, Architektur, Basismodell, Trainingsdaten, Bildauflösung und Token-Budget pro Bild.
- **Kein Betriebsprofil.** Hardwarebedarf (RAM, VRAM, CPU, GPU, NPU), Quantisierungen, Latenz und Durchsatz sind nicht angegeben. Kosten und Machbarkeit auf eigener Infrastruktur lassen sich aus der Card nicht abschätzen.
- **Keine Herkunfts- und EU-Angaben.** Zu Datenherkunft, Versionshistorie oder Vorgängermodell sagt die Card nichts. Für Sovereign-AI-Anforderungen reicht das nicht als Grundlage.
- **Hub-Zahlen sind kein Qualitätssignal.** Likes und Downloads zeigen Aufmerksamkeit kurz nach Veröffentlichung, nicht Eignung. Die Likes weichen zwischen zwei Abrufen um eins ab.
- **Material unvollständig.** Blog, Playground und API-Doku auf cactuscompute.com sind verlinkt, waren aber nicht Teil der ausgewerteten Quelle. Dort stehen vermutlich Beispiele zu Extraktion und Detektion.
