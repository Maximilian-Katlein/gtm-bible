# ccore/Qwen3.5-4B-GLB-3D-Coder: ein 4B-Modell, das Low-Poly-Spielassets als Three.js-Code erzeugt

> **Quelle:** [ccore/Qwen3.5-4B-GLB-3D-Coder](https://huggingface.co/ccore/Qwen3.5-4B-GLB-3D-Coder) · ccore (CCORE, Einzelentwickler auf Hugging Face) · Model Card · 2026-11-15
> **Sprecher verkauft:** nichts, Gewichte und Datensatz sind kostenlos, Finanzierung über Spenden (Ko-fi, Krypto) · **Zielmarkt der Aussagen:** Spieleentwickler und 3D-Asset-Ersteller (Godot, Three.js, GLB-Editoren), eher Indie und Hobby als B2B · **Beweislage:** Herstellerangaben und ausgewählte Bildbeispiele, keine veröffentlichten Messwerte

## Worum es geht
Die Karte beschreibt ein Feintuning von Qwen/Qwen3.5-4B, das aus einer englischen Textanfrage eine vollständige HTML-Seite mit Three.js-Code schreibt. Die Seite zeigt das 3D-Asset im Browser und exportiert es per Button als GLB-Datei für Godot oder einen anderen Editor. Relevant ist das für alle, die prüfen wollen, wie weit ein kleines, lokal lauffähiges Open-Weight-Modell eine Spezialaufgabe übernehmen kann, wenn der Ausgabeweg über Code statt über ein 3D-Format läuft.

## Was man anwenden kann
1. **Umweg über Code statt direktem 3D-Format.** Das Modell erzeugt kein Mesh, sondern eine eigenständige Three.js-Seite mit Vorschau und Export-GLB-Button. Ablauf: HTML als .html speichern, im Browser öffnen, Szene prüfen, GLB exportieren, im Zieleditor importieren. Das Muster ist übertragbar: Ein Code-Modell liefert ein ausführbares Artefakt, dessen Ergebnis der Mensch sichtbar prüfen kann.

2. **Ausgabelimit aufheben.** Trainiert wurde mit Beispielen bis 72K Token, Antworten liegen im Schnitt bei etwa 20K Token. Ein Limit von 8K Ausgabetoken bricht laut Karte die Generierung im Denken oder vor dem Ende des HTML ab. Empfohlen ist unbegrenzte Ausgabe (-1, wo die Laufzeit das erlaubt). Kontext- und Speichergrenzen der Laufzeit gelten trotzdem weiter. Wichtig vor allem bei Chat-Oberflächen mit festem Standardlimit.

3. **Thinking anlassen, ohne Budget.** Reasoning soll aktiv bleiben, ohne Effort-Limit und ohne eigenes Thinking-Token-Budget. Ergebnisse mit abgeschaltetem oder gekürztem Thinking hat ccore nach eigener Aussage nicht geprüft.

4. **Sampling wie in der Evaluation.** Temperature 0,8, Top K 40, Top P 0,95, Min P 0,0, Repeat Penalty 1,0. Mit diesen Werten, Thinking an und der Q8_0-Quantisierung lief die dokumentierte Evaluation.

5. **Quantisierung wählen.** Es gibt Q4_K_M (kompakt) und Q8_0 (Grundlage der Evaluation) als GGUF sowie das Original-Checkpoint in Safetensors (fünf Shards, etwa 17,49 GB, Text FP32, Vision BF16). Den Vision-Projektor (mmproj, 644 MiB, unverändert vom Basismodell) braucht nur, wer Bilder als Eingabe nutzt. Dateigrößen der GGUFs und Hardwarebedarf nennt die Karte nicht.

6. **System-Prompt übernehmen.** Der empfohlene System-Prompt legt Godot und GLB als Ziel fest, verlangt Low-Poly-Qualität, ausschließlich Three.js und eine einzige HTML-Datei mit funktionierendem Export-Button. Animation nur, wenn das Asset sie braucht.

7. **Briefings in fester Reihenfolge.** Kurze Ideen funktionieren laut Karte. Bei detaillierten Anfragen zuerst das Hauptobjekt nennen, dann Komponenten, Farben, Materialien, Platzierung und Bewegung. Rahmenvorgaben wie „schlichte Präsentation, keine Umgebung, statisch“ stehen am Ende. Prompts auf Englisch, deutsche Anfragen sind nicht getestet.

8. **Animation ausdrücklich verlangen und im Export prüfen.** Bewegung kommt nur, wenn sie im Prompt steht, etwa ein Holztor mit Öffnungsanimation. Danach kontrollieren, ob die Animation in der GLB tatsächlich enthalten ist. Beim gezeigten Mikroskop wurde der Export nachträglich angepasst, damit die Revolver-Animation erhalten blieb.

9. **Im Zieleditor abnehmen, nicht im Browser.** Materialien, Licht und Animationen können im Editor anders aussehen als in der Browser-Vorschau. Manche Anfragen brauchen einen zweiten Versuch oder eine kleine Code-Korrektur. Erfolgsraten nennt die Karte nicht.

10. **Alte Downloads ersetzen.** Wer vor dem 5. November 2026 geladen hat, soll die Dateien löschen und neu laden, etwa in LM Studio. Die GGUF-Dateinamen sind gleich geblieben, alte Gewichte werden sonst unbemerkt weiterverwendet. Eine Versionsnummer oder einen Commit-Hash gibt die Karte nicht an, nur „latest uploaded checkpoint“. Für reproduzierbare Setups den Commit im Repository selbst festhalten.

11. **Modell plus Harness für ganze Spiele.** Das Showcase RIFTWARD: Guardians of the Ancient ist eine Browser-Arena mit Assets aus dem Modell. Zusammenbau, Gameplay, Oberfläche, Effekte und Tests übernahm ein Orchestrierungs- und Validierungs-Harness. Das Spiel läuft ohne Modellinferenz. Der Space ccore/RIFTWARD enthält eine agent-starter-prompt.txt, die beschreibt, wie man einen Coding-Agenten an eine lokale Modell-API anbindet.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 4.539.265.536 | Parameter laut Safetensors-Metadaten (F32 4.205.751.296, BF16 333.514.240), als „4B“ bezeichnet | Herstellerangabe |
| ca. 17,49 GB | Original-Checkpoint, fünf Shards | Herstellerangabe |
| 644 MiB | optionaler Vision-Projektor | Herstellerangabe |
| 3.918 | getestete und gerenderte Trainingsbeispiele mit validierten GLB-Exporten | Herstellerangabe |
| 40 | Domänen im Trainingsdatensatz | Herstellerangabe |
| 25 | Kategorien in der Prompt-Tabelle der Karte | Herstellerangabe |
| bis 72K Token | Länge der längsten Trainingsbeispiele | Herstellerangabe |
| ca. 20K Token | durchschnittliche Antwortlänge | Herstellerangabe |
| 8K Token | Ausgabelimit, das laut Karte zu Abbrüchen führt | Herstellerangabe |
| 0,8 / 40 / 0,95 / 0,0 / 1,0 | Temperature, Top K, Top P, Min P, Repeat Penalty | Herstellerangabe |
| 4 | Bildbeispiele im Vergleich mit DeepSeek V4.1 Flash 1017 | Herstellerangabe, keine Metrik |
| 428 Likes, 54.494 Downloads | Plattformzähler zum Stand der Metadaten | Plattformdaten, kein Qualitätsbeleg |
| 100.000 | geplante Beispiele für künftige kleine Modelle, Aufwand laut ccore etwa das 20-Fache | Behauptung ohne Beleg |

## Wortlaute
- „Create game assets for the Godot editor, which uses GLB files. Create whatever the user requests as a good-quality low-poly asset using only Three.js in one complete standalone HTML file.“ Kern des empfohlenen System-Prompts: Ziel, Qualität, Technik und Ausgabeform in zwei Sätzen.
- „Create a frozen goblin watch camp.“ Beispiel für einen Kurzprompt, der laut Karte nicht im Trainingsdatensatz vorkam.
- „Create a wooden gate with an opening animation.“ Beispiel aus der Prompt-Tabelle für ausdrücklich angeforderte Animation.
- „Use a plain presentation without surrounding cave walls or extra scenery. Keep everything static.“ Rahmenvorgabe am Ende eines langen Briefings.

## Grenzen und Widerspruch
- **Keine Messwerte.** Die Karte spricht von einer „recorded evaluation“, veröffentlicht aber weder Metriken noch Benchmark noch Ergebnistabelle. Der Vergleich mit DeepSeek V4.1 Flash 1017 (hohes Reasoning) besteht aus vier vom Autor ausgewählten Bildern, ohne Prompt-Anzahl, Fehlerquote oder Auswahlkriterium.
- **Showcase nicht gleich Modellleistung.** RIFTWARD entstand mit Harness, dessen Anteil nicht beziffert ist. Das Mikroskop-Beispiel wurde von Hand nachgebessert. Die Community-Demo von Naoki Kishida (3D-RPG, kishida.github.io/webdemos/rpg-3d-glb) nutzt die frühere Preview-Version, nicht den aktuellen Checkpoint.
- **Technische Lücken.** Kontextlänge, Architekturdetails, Trainingsmethode, Rechenaufwand, VRAM-Bedarf, GGUF-Größen und Geschwindigkeit fehlen. Unklar bleibt auch, was sich gegenüber Preview und Basismodell verbessert hat.
- **Datensatz.** ccore/ThreeJS-3D-GLB-Assets ist öffentlich, aber Entstehung (manuell oder synthetisch, durch welche Modelle) und Lizenz der Beispiele sind nicht beschrieben.
- **Herkunft und Souveränität.** Die Karte nennt das Modell „independently developed“, technisch ist es ein Feintuning von Qwen/Qwen3.5-4B. Für Compliance zählt damit die Herkunft der Basisgewichte, zu deren Trainingsdaten die Karte nichts sagt. Lizenz ist Apache 2.0, bei Weiterverteilung Lizenz- und Attributionshinweise beibehalten. EU-spezifische Angaben fehlen.
- **Externe Abhängigkeit.** Die erzeugte Seite kann Three.js und Add-ons per CDN laden. Für Offline- oder Air-Gap-Betrieb müssen die Bibliotheken selbst lokal bereitgestellt werden, dazu sagt die Karte nichts.
- **Pflege.** Eine Einzelperson finanziert und pflegt das Projekt, ohne Support- oder SLA-Angaben. Für Produktivbetrieb ist das ein Abhängigkeitsrisiko.
- **Datumsabweichung.** Metadaten nennen createdAt 2026-11-01, die Karte den Release am 5. November 2026, ohne Erklärung.
- **Zielgruppe.** Belege stammen aus Spiele- und Hobbykontext. Für B2B-Einsatz, etwa Produktvisualisierung, gibt es in der Quelle keine Beispiele.
