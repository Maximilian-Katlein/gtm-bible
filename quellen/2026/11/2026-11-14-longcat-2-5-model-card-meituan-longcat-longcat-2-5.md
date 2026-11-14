# LongCat-2.5 (Modellkarte, meituan-longcat/LongCat-2.5)

> **Quelle:** [LongCat-2.5 (Model Card, meituan-longcat/LongCat-2.5)](https://huggingface.co/meituan-longcat/LongCat-2.5) · Meituan LongCat Team, Meituan · Model Card · 2026-11-14
> **Sprecher verkauft:** Open-Weight-Modell unter MIT-Lizenz auf Hugging Face, dazu die Chat-Website longcat.ai · **Zielmarkt der Aussagen:** Entwickler und Unternehmen mit agentischen Coding- und Agent-Workloads, Deployment nur für NPU-Plattformen dokumentiert · **Beweislage:** ausschließlich Herstellerangaben, Benchmarks teils selbst gemessen, teils zitiert, teils auf hauseigenen Tests.

## Worum es geht
Die Karte stellt ein multimodales Mixture-of-Experts-Modell mit 1,6 Billionen Parametern für lange agentische Aufgaben vor: Codebase-Entwicklung, ganze Projekt-Builds, Design und 3D. Für Betreiber, die ein offenes Spitzenmodell selbst hosten wollen, ist die eigentliche Frage, ob sich Leistung und Effizienz außerhalb des Hardware-Stacks des Herstellers überhaupt abrufen lassen. Die Karte beantwortet das nicht, liefert aber genug Angaben, um es zu prüfen.

## Was man anwenden kann
1. **Speicherbedarf vor jeder Planung rechnen.** Die Safetensors-Metadaten nennen rund 1,778 Billionen BF16-Parameter und 1,23 Milliarden F32-Parameter. Bei 2 Byte je BF16-Parameter ergibt das rund 3,56 TB Gewichte plus etwa 4,9 GB, bevor KV-Cache und Aktivierungen dazukommen. Die Karte nennt selbst keine Hardwareanforderung, die Rechnung ist eine eigene Überschlagsrechnung und gilt für unquantisiertes Laden.
2. **Deployment-Pfad klären, bevor ein Projekt startet.** Dokumentiert ist nur der Betrieb auf NPU-Plattformen über den Branch `longcat-2.5-npu` von SGLang-FluentLLM. Für NVIDIA-GPUs, vLLM, llama.cpp oder GGUF gibt es keine Anleitung. Der Repo-Tag `custom_code` weist auf eigenen Modellcode hin. Wer in der EU auf GPU-Infrastruktur betreibt, muss die Portierung selbst leisten und einplanen.
3. **Thinking-Modus je nach Ziel schalten.** Für beste Leistung `enable_thinking=True` und `save_history_reasoning_content=True` setzen, damit das Reasoning früherer Turns erhalten bleibt. Für Token-Effizienz `enable_thinking=False`. Beide Schalter laufen über `extra_body` mit `chat_template_kwargs` an eine OpenAI-kompatible `chat.completions`-API. Voraussetzung ist ein Server, der Chat-Template-Argumente durchreicht.
4. **Reasoning in der Multi-Turn-Historie nicht verwerfen.** Im Codebeispiel behalten Assistenten-Nachrichten ihr `reasoning_content`, auch solche mit `tool_calls`. Tool-Antworten gehen als `role: "tool"` mit `tool_call_id` zurück, Bilder als `image_url`-Content-Part, Tools im OpenAI-Function-Format. Wer eine bestehende Agent-Pipeline anbindet, die Reasoning-Felder abschneidet, weicht vom empfohlenen Betrieb ab.
5. **Sampling-Werte aus der Evaluation als Startpunkt nehmen.** Standard in allen Ergebnissen ist Thinking an, `temperature=1.0`, `top_p=0.95`. Abweichend nutzte MCP Atlas `temperature=0.7` mit Reasoning Effort „max“, Vision2Web `top_k=50`, SkillsBench `top_k=-1`. Eine eigene Betriebsempfehlung gibt die Karte nicht.
6. **Quantisierungsgewinne nicht als verfügbar voraussetzen.** Die Effizienzzahlen zu W4A4 stammen aus Stresstests auf der NPU-Plattform des Herstellers. Die Metadaten zeigen nur BF16 und F32, ein INT4-Checkpoint ist nicht verlinkt. Der Genauigkeitsverlust ist nicht beziffert. Vor Produktivbetrieb eine eigene Evaluation auf den eigenen Aufgaben fahren.
7. **Lizenz einschließlich Patentfrage prüfen lassen.** MIT ohne Einschränkung nach Branche oder Region, also kein EU-Ausschluss. Ausdrücklich ausgenommen sind Marken und Patente von Meituan. Anders als bei Apache 2.0 fehlt eine ausdrückliche Patentlizenz. Diese Einordnung stammt nicht aus der Karte und gehört vor dem Einsatz in die Rechtsabteilung.
8. **Einsatzfeld nach den Tabellenstärken wählen.** Nach Herstellerangaben am stärksten bei Browsing und Recherche: BrowseComp 91.9, ResearchRubrics 81.0, ALE 38.5, jeweils Höchstwert der Tabelle. Bei Coding liegt Claude-Opus-5 deutlich vorn, etwa NL2Repo 75.3 gegen 60.5. Video (VideoMME 85.2) liegt hinter drei Vergleichsmodellen.
9. **Deutsch und Kontextlänge selbst testen.** Die Karte warnt vor Leistungsschwankungen zwischen Sprachen, nennt aber weder Sprachliste noch mehrsprachigen Benchmark. Eine offizielle maximale Kontextlänge fehlt. Die Evaluation nutzte 256K, 512K und bei DeepSWE 1M, das belegt aber keinen unterstützten Betrieb.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1,6 Billionen gesamt, ca. 48 Mrd. aktiv pro Token | Modellgröße laut Kartentext | Herstellerangabe |
| 1.779.752.648.320 Parameter | Safetensors-Metadaten des Repos, Differenz zum Kartentext unerklärt | Herstellerangabe (Plattformmetadaten) |
| ca. 3,56 TB | Gewichte in BF16, ohne KV-Cache | Eigene Rechnung aus Metadaten |
| +86 % Durchsatz pro Gerät | Long-Sequence-SFT gegenüber DDP-Baseline, eigene Infrastruktur | Herstellerangabe |
| +43,3 % Prefill, +42,77 % Decode, −15,91 % TTFT, −19,72 % TPOT | W4A4 gegen W8A8-MoE-Baseline, Online-Stresstest, Lastprofil unbekannt | Herstellerangabe |
| 1,73× | Grouped-GEMM-Kernels W4A4 gegen W8A8, Mittelwert | Herstellerangabe |
| +92 % Decode-Durchsatz | W4A4KV8 gegen W8A8KV16 | Herstellerangabe |
| Terminal Bench v2.1: 70.8 auf 88.4 | LongCat-2.0 zu 2.5, Claude-Code-Harness, Mittel aus drei Läufen | Herstellerangabe, Eigenmessung |
| DeepSWE: 9.7 auf 64.6 | LongCat-2.0 zu 2.5, mini-swe-agent, 1M | Herstellerangabe, Eigenmessung |
| BrowseComp 91.9 | Eigener Harness mit Verify- und Discard-All-Modul, max. 1.024 Runden | Herstellerangabe |
| MCP Atlas 83.1 | Claude-Opus-5 85.8, Reasoning Effort „max“, Temperatur 0.7 | Herstellerangabe, Vergleichswerte teils zitiert |
| NL2Repo 60.5 | Claude-Opus-5 75.3, Claude-Opus-4.8 69.7 | Herstellerangabe, Vergleichswerte teils zitiert |
| Terminal Bench v4.0 38.5 | Zitierte Vergleichswerte streuen von 12.6 bis 53.9 | Herstellerangabe, Vergleichbarkeit offen |
| LongCat AppDev 73.7, FORTE 83.3, FORTE-MM 72.1 | Vom Hersteller entwickelte Benchmarks | Herstellerangabe, extern nicht prüfbar |
| 257 Likes, 971 Downloads | Plattformzähler zum Abrufzeitpunkt, Repo angelegt 2026-11-04 | Plattformmetadaten |

## Wortlaute
- „Thinking mode on(`enable_thinking=True`), keeping all reasoning content(`save_history_reasoning_content=True`) for better performance.“ Steht für die empfohlene Einstellung, wenn Leistung vor Tokenverbrauch geht.
- „unmarked scores are measured in-house and are indicative only.“ Die Karte relativiert ihre eigenen Messwerte selbst.
- „This license does not grant any rights to use Meituan trademarks or patents.“ Der Satz, an dem die Patentprüfung ansetzt.

## Grenzen und Widerspruch
- **Nur Herstellerangaben.** Es liegt allein die Model Card vor, keine Diskussion, keine unabhängigen Messungen. Tech-Blog und arXiv-Papers waren nicht Teil des Materials.
- **Gemischte Vergleichstabelle.** Mit * markierte Werte sind aus fremden Berichten zitiert, unmarkierte selbst gemessen, mit unterschiedlichen Harnesses (mehrere Claude-Code-Versionen, mini-swe-agent, Codex, eigener Harness). Streuungen und Konfidenzintervalle fehlen. Bei Abständen unter einem Punkt, etwa SpreadsheetBench 2 (34.9 gegen 35.8 und 34.8), ist keine Rangfolge ablesbar.
- **Judge-Modelle aus der Konkurrenz.** Bewertet wird teils per Claude Opus 4.5 (Mehrheit aus drei Urteilen) und gemini-3.6-flash. Das macht Ergebnisse von der Urteilsqualität dieser Modelle abhängig.
- **Effizienz an Hardware gebunden.** Training und Serving sind auf inländische KI-Beschleuniger des Herstellers zugeschnitten, der Chiphersteller wird nicht genannt. Für Sovereign AI in Europa heißt das: Die Gewichte sind offen, die beworbenen Effizienzvorteile hängen an einem Stack, der hier kaum verfügbar ist.
- **Unbelegte Genauigkeit der Quantisierung.** „comparable to the unquantized model“ ohne Zahlen und ohne Benchmarkliste.
- **Fehlende Architekturangaben.** Keine Expertenzahl, keine Attention-Variante, kein Vokabular, keine Bildauflösungslimits. Begriffe wie LSA und die Schutzmaßnahmen gegen Reward Hacking bleiben unerklärt.
- **Keine Angaben zu Trainingsdaten, Datenrechten, Safety-Evaluation oder EU-Regulierung.** Datenschutz und Inhaltssicherheit schiebt die Karte den Betreibern zu.
- **Keine Kosten.** Weder API-Preise noch Latenz auf GPU-Hardware.
- **Downloadzahlen sind wenig aussagekräftig.** Bei mehreren Terabyte Gewichten sagt die Zahl kaum etwas über die tatsächliche Verbreitung.
