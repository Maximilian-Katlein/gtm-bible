# Inkling 2 Mini (Modellkarte, thinkingmachines/Inkling-2-Mini)

> **Quelle:** [Inkling 2 Mini (Model Card, thinkingmachines/Inkling-2-Mini)](https://huggingface.co/thinkingmachines/Inkling-2-Mini) · Thinking Machines Lab, Inc. · Model Card · 2026-11-21
> **Sprecher verkauft:** das Open-Weight-Modell Inkling 2 Mini (Apache 2.0) und die Fine-Tuning-Plattform Tinker mit API-Zugang · **Zielmarkt der Aussagen:** Entwickler von Agenten, Tool-Use-Systemen, Coding-Assistenten, Chatbots und RAG-Systemen · **Beweislage:** ausschließlich Herstellerangaben, Benchmark-Tabelle ohne unabhängige Prüfung und im Material abgeschnitten.

## Worum es geht
Die Karte beantwortet, ob ein kleines Open-Weight-Modell mit rund 5 Mrd. effektiv aktiven Parametern bei Coding-, Agenten- und Tool-Use-Aufgaben mit dichten Modellen der Klasse 27 bis 31 Mrd. mithalten kann und auf einem einzelnen Gerät läuft. Sie richtet sich an Entwickler, die ein Modell lokal betreiben, feintunen oder in eigene Produkte einbauen wollen. Veröffentlicht laut Karte am 20. November 2026.

## Was man anwenden kann
1. **Hardware vor dem Download prüfen.** Der Checkpoint ist laut Karte etwa 20 GB groß, in gemischter NVFP4- und MXFP8-Präzision. Unterstützt sind eine NVIDIA DGX Spark und Apple-Silicon-Geräte (MacBook, Mac mini, Studio) ab 32 GB Speicher. Auf anderen GPUs empfiehlt die Karte 32 GB VRAM oder mehr. Bei 20 GB Gewichten bleibt wenig Platz für KV-Cache, das beworbene Kontextfenster von 1 Mio. Tokens ist auf solchen Geräten realistisch nicht ausschöpfbar, der Speicherbedarf dafür ist nicht beziffert.

2. **Inferenz-Server nach Umgebung wählen.** Genannt werden Hugging Face transformers, vLLM, SGLang, TokenSpeed, NVIDIA Dynamo, Unsloth (auch quantisierte GGUF-Versionen), llama.cpp (GGUF), Llama App sowie Ollama und Exo Labs auf Apple Silicon. Für SGLang, vLLM, TokenSpeed und Unsloth sind eigene Rezepte verlinkt (docs.sglang.io Cookbook, recipes.vllm.ai, lightseek.org, unsloth.ai). Für den Mac liegt Ollama nahe, für Server-Durchsatz vLLM oder SGLang.

3. **Prompt-Format nicht raten.** Chat-Template, Tool-Calling-Format, Thinking-Modus und Sampling-Parameter stehen nicht im vorliegenden Teil der Karte. Sie verweist für die Formatierung auf das PyPI-Paket tml-renderers und das Tinker Cookbook (GitHub thinking-machines-lab/tinker-cookbook). Wer eigene Prompts baut, sollte dort das Format übernehmen, bevor er Qualität beurteilt.

4. **Ohne eigenes Hosting über Tinker testen.** Tinker bietet API-Zugang und Fine-Tuning. Der Tinker Playground erlaubt nur Inferenz, kein Training. Das ist der schnellste Weg, das Modell vor einer Hardware-Entscheidung auszuprobieren, bindet aber an die Plattform des Herstellers.

5. **Post-Training mit offenen Werkzeugen.** Neben Tinker nennt die Karte Miles (miles.radixark.com) und SkyRL (docs.skyrl.ai), beide mit eigenen Seiten für Inkling 2 Mini. Damit ist Fine-Tuning auch außerhalb der Herstellerplattform vorgesehen.

6. **Mit 5,4 Mrd. statt 3,4 Mrd. aktiven Parametern rechnen.** Das Modell hat 24 Layer mit eigenen Gewichten, die mittleren 12 laufen dreimal mit geteilten Gewichten. Das ergibt 48 Layer-Anwendungen pro Token. Pro Durchlauf sind 3,4 Mrd. Parameter aktiv, effektiv 5,4 Mrd. pro Token. Für Latenz- und Kostenschätzungen ist die höhere Zahl die richtige, die Karte selbst nutzt in der Benchmark-Tabelle gerundet 5/26.

7. **Modell nach Aufgabentyp auswählen.** In der Herstellertabelle liegt Inkling bei Coding (DeepSWE, SWEBench Pro, Vibe Code Bench), Tool-Use über MCP (MCP Atlas) und Agentic Search vorn. Bei Knowledge-Work-Benchmarks (AA-Briefcase, GDPVal-AA, AutomationBench-AA, EnterpriseOps-Gym) führt Qwen3.8-27B. Für Agenten mit Tool-Aufrufen spricht die Tabelle für Inkling, für Büro- und Automatisierungsaufgaben nicht eindeutig.

8. **Benchmarks im eigenen Harness nachmessen.** Die Zeilen nutzen unterschiedliche Harnesses (stirrup v0.2.1, mini-swe-agent v2.4.6, pi v0.83.0, openhands, „bash only“, „with compaction“, „Best harness“). Teilweise steht nur Inkling im Label, ob die Wettbewerber gleich gemessen wurden, ist offen. Agentic-Search-Werte entstanden mit Kontext-Compaction. Wer das Modell für einen Agenten einsetzt, sollte mit dem eigenen Agent-Framework und eigenen Aufgaben vergleichen.

9. **Deutsch selbst testen.** Die Karte nennt Englisch und „general multilingual support“ ohne Sprachliste. Kein Benchmark misst natürliche Mehrsprachigkeit, SWEBench Multilingual betrifft Programmiersprachen. Für deutschsprachige Chatbots oder RAG-Systeme ist ein eigener Test mit realen Dokumenten Pflicht.

10. **Lizenz und Acceptable Use Policy zusammen prüfen.** Apache 2.0 erlaubt grundsätzlich kommerzielle Nutzung, Änderung und Weitergabe. Zusätzlich verlinkt die Karte eine Model Acceptable Use Policy von Thinking Machines, deren Inhalt im Material fehlt. Vor Produkteinsatz klären, ob sie zusätzliche Pflichten begründet.

11. **Eingaben im empfohlenen Rahmen halten.** Eingabe sind Text (UTF-8) und Bilder, Ausgabe nur Text. Jede Bilddimension sollte zwischen 40 und 4096 px liegen. Video steht in den Trainingsdaten, ist aber nicht als Eingabe aufgeführt.

12. **Lokaler Betrieb als Souveränitätsoption, mit Lücken.** Offene Gewichte, ein Checkpoint auf Einzelgeräten und Apache 2.0 erlauben Betrieb ohne Cloud-API. Die Karte sagt nichts zu EU-Compliance, KI-Verordnung, Urheberrecht oder Trainingsdatenquellen im Detail. Für regulierte Einsätze fehlen damit Dokumentationsbausteine.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 26,4 Mrd. / 3,4 Mrd. / 5,4 Mrd. | Parameter gesamt / aktiv pro Durchlauf / effektiv aktiv pro Token | Herstellerangabe |
| ca. 1,0 Mrd. | zusätzliche effektiv aktive Parameter je weiterem Schleifendurchlauf | Herstellerangabe |
| 24 Layer, 48 Anwendungen | Gewichts-Layer und Layer-Durchläufe pro Token | Herstellerangabe |
| 8 von 128 | Experten pro Token und MoE-Layer | Herstellerangabe |
| 1 Mio. Tokens | maximales Kontextfenster, ohne Qualitätsmessung | Herstellerangabe |
| ca. 20 GB | Checkpoint, NVFP4 und MXFP8 gemischt | Herstellerangabe, Safetensors-Metadaten ergeben rechnerisch rund 28,3 GB |
| 32 GB | Mindestspeicher Mac, empfohlener VRAM sonst | Herstellerangabe |
| 40 bis 4096 px | empfohlene Bilddimension | Herstellerangabe |
| 20,1 | AA Index v5.0, Gleichstand mit Qwen3.8-27B | Herstellerangabe |
| 48,2 % vs. 42,2 % | DeepSWE v1.1, Inkling vs. Qwen3.8-27B | Herstellerangabe |
| 77,9 % vs. 73,8 % | SWEBench Pro v2 (Hard), Inkling vs. Qwen | Herstellerangabe |
| 79,2 % | SWEBench Verified, Inkling nur mit Bash | Herstellerangabe |
| 77,9 % vs. 64,9 % | Vibe Code Bench v1.1, Inkling vs. Qwen | Herstellerangabe |
| 82,7 % vs. 77,3 % | MCP Atlas (Public), Inkling vs. Qwen | Herstellerangabe |
| 79,0 % vs. 78,9 % | BrowseComp, Inkling (mit Compaction) vs. Nemotron 3.5 Super VL | Herstellerangabe |
| 85,3 % | DeepSearchQA, Inkling mit Compaction | Herstellerangabe |
| 71,6 % vs. 73,0 % | Terminal Bench v2.1, Inkling vs. Qwen (Qwen vorn) | Herstellerangabe |
| 5,6 % | Terminal Bench v4.0, Inkling und Qwen gleichauf | Herstellerangabe |
| 1263 vs. 1391 | AA-Briefcase v1.1, Inkling vs. Qwen (Qwen vorn) | Herstellerangabe |
| 41,8 % vs. 48,2 % | AutomationBench-AA v1.0.6, Inkling vs. Qwen (Qwen vorn) | Herstellerangabe |
| 92,8 % | OmniDocBench v1.6, Inkling | Herstellerangabe, Vergleichswerte abgeschnitten |
| 136 | Downloads zum Zeitpunkt der Erfassung | Hugging-Face-Metadaten |

## Grenzen und Widerspruch
- **Nur Herstellerzahlen.** Alle Leistungswerte stammen aus der eigenen Tabelle. Wer die Wettbewerber gemessen hat und ob in denselben Harnesses, steht nicht da. „AA“ ist nicht ausgeschrieben (vermutlich Artificial Analysis). Muse Glimmer ist nicht näher identifiziert.
- **Auffällige Werte ohne Erklärung.** Gemma 4 31B liegt bei FrontierCode und Terminal Bench v4.0 bei 0,0 %, bei DeepSWE bei 0,3 %. Terminal Bench v2.1 und v4.0 liefern für dasselbe Modell 71,6 % und 5,6 %, die Versionen sind also nicht vergleichbar. Bei Diligence Bench wurde je Modell das beste Harness gewählt, was Ergebnisse begünstigen kann.
- **Knappe Vorsprünge.** BrowseComp: 0,1 Prozentpunkte vor Nemotron. Mehrere Gleichstände mit Qwen3.8-27B. Bei sechs Benchmarks liegt laut eigener Tabelle Qwen vorn.
- **Speicherangabe widersprüchlich.** Die Summe der Safetensors-Einträge ergibt rund 28,3 GB, die Karte nennt etwa 20 GB. Die Ursache ist ungeklärt (eigene Rechnung aus den Metadaten).
- **Material unvollständig.** Die Karte bricht in der Benchmark-Tabelle ab. Abschnitte zu Sicherheit, Einschränkungen, Sampling-Parametern und Zitation fehlen. Kein Vorgänger und kein größeres Modell der Reihe genannt.
- **Keine Betriebsdaten.** Durchsatz, Latenz, Tokens pro Sekunde auf DGX Spark oder Mac, KV-Cache-Bedarf und Mehraufwand der dreifachen Schleife sind nicht angegeben.
- **Trainingsdaten unbestimmt.** Öffentliche, zugekaufte, intern und synthetisch erzeugte Daten, ohne Menge, Stichtag oder Quellenliste.
- **Kaum Praxiserfahrung.** 136 Downloads zum Erfassungszeitpunkt, keine Diskussion im Material.
