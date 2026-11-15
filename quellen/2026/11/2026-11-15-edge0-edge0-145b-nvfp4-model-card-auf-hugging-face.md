# Edge0-145B-NVFP4: ein 145B-Agentenmodell auf einer Consumer-GPU

> **Quelle:** [Edge0/Edge0-145B-NVFP4 (Model Card auf Hugging Face)](https://huggingface.co/Edge0/Edge0-145B-NVFP4) · Edge0, Edge0 · Model Card · 2026-11-15
> **Sprecher verkauft:** das Open-Weight-MoE-Modell Edge0-145B (Builds NVFP4 und Q3_K) und die eigene lokale Inferenz-Engine Edge0 (edge0-strata, edge0-infer, Edge0 Chat) · **Zielmarkt der Aussagen:** Entwickler und Teams, die ein großes Agenten- und Coding-Modell lokal auf einer Consumer-GPU betreiben wollen · **Beweislage:** ausschließlich Herstellerangaben, Benchmarks größtenteils nur als Grafik, keine unabhängige Prüfung.

## Worum es geht
Die Karte beantwortet eine Frage: Kann man ein Modell mit 145 Mrd. Parametern auf einer einzelnen 24-GB-Grafikkarte für Agenten- und Coding-Aufgaben betreiben, und mit welcher Hardware und welchen Einstellungen? Sie richtet sich an Entwickler und Teams, die lokal und ohne Cloud-API arbeiten wollen. Der Trick ist nicht, dass 145B in 24 GB VRAM passen. Der Trick ist, dass nur rund 10 Mrd. Parameter pro Token rechnen und der Rest aus dem Hauptspeicher oder von der SSD nachgeladen wird.

## Was man anwenden kann
1. **Hardware realistisch planen.** Für die ausgewiesenen Vollwerte braucht man eine 24-GB-GPU plus freien Host-RAM: rund 31 GiB beim Q3_K Build, rund 38 GiB bei NVFP4. Gemessen wurden 23,14 GiB VRAM plus 31,28 GiB RAM (Q3_K) bzw. 23,25 GiB VRAM plus 38,27 GiB RAM (NVFP4) auf einer RTX 5090 D 24 GB mit aktivierter Residency. Wer weniger RAM hat, landet im SSD-Modus.

2. **Build nach Hardware wählen, nicht nach Gefühl.** Auf der RTX 5090 D ist Q3_K in allen vier Messungen schneller als NVFP4 (Agent Decode 121,2 gegen 98,3 tok/s) und rund 17 Prozent kleiner (40,81 gegen 47,79 GiB). Auf der RTX Spark N1X 60 GiB ist es umgekehrt: NVFP4 liegt dort im Agent Decode rund 25 Prozent vorn. Auf dem Mac (Metal) läuft nur Q3_K, NVFP4 ist CUDA-only. Einen Qualitätsunterschied zwischen den Builds weist die Karte nicht aus.

3. **Prefill-Latenz vor dem Kauf durchrechnen.** Für Agentenschleifen mit langem Kontext zählt die Wartezeit vor dem ersten Token. Aus den 16K-Prefill-Werten ergeben sich rund 5 s auf der RTX 5090 D (NVFP4), 17 bis 18 s auf der Spark N1X (NVFP4), rund 20 s auf dem M2 Ultra (Q3_K) und 48 bis 49 s im Budget-Betrieb mit 16 GiB VRAM und 20 GiB RAM (eigene Rechnung). Werte über 16K bis 256K fehlen ganz.

4. **Budget-Betrieb kostet vor allem Prefill.** Mit 16 GiB VRAM und 20 GiB RAM (Q3_K) bleibt der Decode bei rund 37 Prozent des Vollbetriebs (44,9 tok/s Agent Decode), der Prefill fällt auf rund 9 bis 11 Prozent (eigene Rechnung). Für kurze Chats tragbar, für Agenten mit großen Kontexten kaum.

5. **Kleinere Maschine nachstellen, bevor man sie kauft.** Edge0 hat den Budget-Betrieb auf derselben 5090 D simuliert: VRAM per `--vram-reserve-mib 8192` gedeckelt, Systemspeicher per cgroup mit `MemoryMax=20G` und ohne Swap. Dasselbe Vorgehen eignet sich, um eigene Zielkonfigurationen vorab zu testen.

6. **Low-Memory-Einstellungen richtig verstehen.** `--resident-budget-gib 20 --expert-profile expert-profile.bin` begrenzt den Expertencache im Host-RAM auf 20 GiB und lädt den Rest bei Bedarf von der SSD (`--mmap-experts` ist enthalten). Pflicht ist ein statisches Expertenprofil, wie man es erzeugt, steht nicht in der Karte. Wichtig: Der Schalter begrenzt nicht den Gesamtverbrauch des Prozesses. Wer hart auf 20 GiB planen muss, braucht zusätzlich eine cgroup-Grenze.

7. **Lokal betreiben und bestehende Clients anbinden.** Nach dem Bauen von edge0-strata und edge0-infer startet `edge0-infer serve --model /pfad/zu/Edge0-145B-NVFP4` einen Server auf 127.0.0.1:8000 mit OpenAI- und Anthropic-kompatiblen Endpunkten (Modellname edge0_145b). Bestehende Tools lassen sich per Basis-URL umstellen, Daten verlassen die Maschine nicht. Unterstützt: NVIDIA mit CUDA 13 unter Linux oder Windows (x64, ARM64) und Apple Silicon über Metal.

8. **Typische Startfehler vermeiden.** An edge0-infer genau einen Modellordner übergeben, nicht den Elternordner mit mehreren Modellen, und die Ordnerstruktur nicht verändern: Die Engine erkennt das Modell über `model_name` in der model.json. Der Beispielpfad `build/cpu/bin/edge0-infer` passt nicht offensichtlich zu den beschriebenen CUDA-Builds, vor dem Nachbauen prüfen.

9. **Lizenz vor jedem produktiven Einsatz lesen.** Die Lizenz heißt edge0-community-model-1.0 und ist keine Standardlizenz wie Apache 2.0 oder MIT. Der Text liegt nicht im Material, ebenso wenig die Lizenz des Qwen-Basismodells. Kommerzielle Nutzung und Weitergabe sind deshalb aus der Karte heraus nicht beurteilbar.

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 145 Mrd. / 10,12 Mrd. | Gesamtparameter / aktive Parameter pro Token | Herstellerangabe |
| 48 Layer, 512 Experten, 10 + 1 aktiv | Architektur pro Layer, 10 geroutete plus 1 Shared Expert | Herstellerangabe |
| 84,6 Mrd. | Expert Pool bei Latent-Breite 1792 (rechnerisch plausibel) | Herstellerangabe, eigene Nachrechnung |
| 51,2 Mrd. | n-Gram-Embedding-Tabelle (PLE) in fp8, memory-mapped, rund 35 Prozent des Modells | Herstellerangabe |
| 1,26 Mrd. | MTP-Draft-Head für Speculative Decoding | Herstellerangabe |
| 256K / 32K | Kontextlänge / davon resident im KV-Cache (int8) | Herstellerangabe |
| 40,81 / 47,79 GiB | Gewichtsgröße Q3_K / NVFP4 | Herstellerangabe |
| 98,3 / 79,6 tok/s | Agent / Chat Decode, RTX 5090 D, NVFP4 | Herstellerangabe |
| 121,2 / 99,7 tok/s | Agent / Chat Decode, RTX 5090 D, Q3_K | Herstellerangabe |
| 91,7 / 69,9 tok/s | Agent / Chat Decode, RTX 4090, Q3_K | Herstellerangabe |
| 46,0 / 36,7 tok/s | Agent Decode, RTX Spark N1X, NVFP4 / Q3_K | Herstellerangabe |
| 57,0 / 60,9 tok/s | Agent / Chat Decode, Apple M2 Ultra, Q3_K | Herstellerangabe |
| 44,9 tok/s | Agent Decode, 16 GiB VRAM + 20 GiB RAM, Q3_K | Herstellerangabe |
| 3.165,7 tok/s | 16K Prefill, RTX 5090 D, NVFP4 | Herstellerangabe |
| 86,5 | Terminal-Bench 2.1, Einheit und Vergleich nur in der Grafik | Herstellerangabe |
| 263 bis 264 Likes, 33.819 Downloads | Plattformzähler zum Abrufzeitpunkt, kein Qualitätsbeleg | Plattformzähler |

## Wortlaute
- „A 145B agent, running on one consumer GPU.“ (Model Card, ohne Zeitstempel) Das zentrale Versprechen, das nur mit viel Host-RAM oder schneller SSD gilt.
- „the engine keeps a few thousand of them on the card and streams the rest from host memory“ (Model Card, ohne Zeitstempel) Das Prinzip dahinter: Kosten hängen an den residenten Experten, nicht an der Modellgröße.
- „--resident-budget-gib 20 --expert-profile expert-profile.bin“ (Model Card, ohne Zeitstempel) Die empfohlenen Low-Memory-Argumente.
- „This flag does not set a total-process RAM limit.“ (Model Card, ohne Zeitstempel) Die Warnung, die man beim RAM-Budget leicht überliest.

## Grenzen und Widerspruch
- **Herkunft widersprüchlich.** Die Karte wirbt mit „trained natively at 4 bits“, die Tags führen das Modell als quantisierte Ableitung von Qwen/Qwen3.8-Flash-Next. Wie beides zusammenpasst, ist nicht erklärt. Trainingsdaten, Methode, Sprachen und Knowledge Cutoff fehlen.
- **Benchmarks nicht prüfbar.** Außer 86,5 auf Terminal-Bench 2.1 stehen alle Scores (DeepSWE 1.1, HLE, GPQA-Diamond, IFBench, AA-LCR) und die fünf Vergleichsmodelle nur in einer SVG-Grafik. Kein Vergleich mit dem Qwen-Basismodell, keine Qualität pro Build.
- **Messaufbau lückenhaft.** Host-RAM, Bandbreite, CPU und SSD-Typ der Testmaschinen fehlen. Chat und Agent Decode sind nicht definiert, der Gewinn durch Speculative Decoding ist nicht ausgewiesen.
- **Größen passen nicht offensichtlich zusammen.** Allein die PLE-Tabelle wäre in fp8 rund 47,7 GiB groß, fast die gesamte NVFP4-Größe. Ob sie in den Gewichtsgrößen enthalten ist, bleibt offen.
- **Hardwarefragen offen.** Ob NVFP4 eine Blackwell-GPU voraussetzt, ist unklar; für die RTX 4090 gibt es keine NVFP4-Zeile.
- **Nur eigene Engine dokumentiert.** Die Tags nennen gguf, beschrieben ist aber nur edge0-infer. Ob llama.cpp, vLLM oder Transformers funktionieren, muss man selbst prüfen.
- **Demo-Video ohne Belege.** Das rund zweiminütige Video zeigt Coding, Videoproduktion, 3D-Szenen und PCB-Design, ohne Angabe zu Build, Hardware, Prompts oder Erfolgsquote.
- **Material abgeschnitten.** Der Abschnitt zum RAM-Budget endet mitten im Satz, weitere Troubleshooting-Hinweise fehlen.
- **Familie unerklärt.** Es gibt eine 120B-Reihe in beiden Builds; was sie unterscheidet, steht nicht in der Karte.
