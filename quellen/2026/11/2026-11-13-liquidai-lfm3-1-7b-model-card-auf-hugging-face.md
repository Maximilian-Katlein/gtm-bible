# LiquidAI/LFM3-1.7B: Model Card auf Hugging Face

> **Quelle:** [LiquidAI/LFM3-1.7B (Model Card auf Hugging Face)](https://huggingface.co/LiquidAI/LFM3-1.7B) · Liquid AI · Model Card · 2026-11-13
> **Sprecher verkauft:** Open-Weight-Textmodell mit 1,73 Mrd. Parametern für lokale Agenten, Tool Calling, strukturierte Ausgaben und Fine-Tuning, unter der LFM Open License v1.0 · **Zielmarkt der Aussagen:** Entwickler von Edge-, On-Device- und lokalen Agenten sowie spezialisierten Anwendungen · **Beweislage:** ausschließlich Herstellerangaben, Benchmark-Bedingungen nicht offengelegt, Tabelle im Material unvollständig.

## Worum es geht
Kann ein Modell mit 1,7 Mrd. Parametern agentische Aufgaben übernehmen, für die bisher Modelle mit etwa 9 Mrd. Parametern nötig waren? Die Card richtet sich an Teams, die Agenten lokal, auf Laptops, Smartphones oder eigener Hardware betreiben wollen. Sie liefert dafür Setup-Details, Sampling-Werte und ein Muster für große Tool-Kataloge.

## Was man anwenden kann
1. **Einsatzgrenze vorab festlegen.** Liquid AI rät selbst von agentischem Coding und komplexem mehrstufigem Reasoning ab und begründet das mit der Modellgröße. Sinnvolle Felder laut Card: lokale Agenten, Tool Calling, strukturierte Ausgaben, domänenspezifisches Fine-Tuning. Für wissenslastige Aufgaben Retrieval oder Suche anbinden, statt auf das Parameterwissen zu setzen.
2. **Zwei Sampling-Profile trennen.** Für Chat, Tool Use, Agenten und Coding: temperature=0.1, top_k=50, repetition_penalty=1.1. Für Mathe und STEM: temperature=1.0, top_p=0.95, top_k=20. Das STEM-Profil nicht für Agenten übernehmen, die niedrige Temperatur passt zu deterministischem Tool Calling.
3. **Passenden Checkpoint wählen.** GPU-Server: BF16 mit vLLM, SGLang oder Transformers; FP8 und NVFP4 sind in der Card nur mit SGLang verlinkt. Lokal und Edge: GGUF für llama.cpp, Ollama, LM Studio; MLX 4-bit für Apple Silicon; ONNX für ONNX Runtime; OpenVINO int4 für Intel-Hardware. Bei 4-bit nennt der Hersteller etwa 1 GB Speicherbedarf.
4. **trust_remote_code bewusst freigeben.** Mit Transformers ist trust_remote_code=True nötig, dabei wird Modellcode aus dem Repo beim Laden ausgeführt. In abgesicherten oder souveränen Umgebungen den Repo-Code vorher prüfen.
5. **Tool-Call-Parser auf XML auslegen.** Das Modell gibt Aufrufe als XML aus, nicht als JSON. Ablauf: Schemas über tools=... an apply_chat_template übergeben, Aufruf ausführen, den Assistant-Aufruf als tool_calls-Eintrag anhängen, dann das Ergebnis als tool-Nachricht.
6. **Drei Stolpersteine beim Tool Calling vermeiden.** function.arguments muss ein Python-Mapping sein; OpenAI-kompatible Clients liefern oft JSON-Strings, diese vorher mit json.loads() dekodieren. Tool-Schemas in jedem Folge-Request erneut mitgeben. Content und Reasoning des laufenden Tool-Use-Turns im Verlauf behalten.
7. **Große Tool-Kataloge über Deferred Tools laden.** Mit defer_loading=True bleiben Tool-Definitionen aus dem Prompt, bis die eigene Suchfunktion des Harness die Namen als tool_reference-Teile zurückgibt. Das Template fügt sie dann in <additional_tools> ein. Die volle tools-Liste muss trotzdem bei jedem Request mitgehen. Funktioniert laut Card mit vLLM, SGLang und LFM3-kompatiblen llama.cpp-Builds; bei llama.cpp ein GGUF mit aktuellem Template nutzen oder es per --chat-template-file laden.
8. **Reasoning-Verhalten einplanen.** Reasoning ist standardmäßig an, der Generation-Prompt endet mit offenem <think>-Tag. enable_thinking=False schaltet es ab, laut Hersteller aber unzuverlässig, vor allem bei reasoning-lastigen Aufgaben. Ältere Denkspuren werden aus dem Verlauf entfernt, außer man setzt preserve_thinking=True.
9. **Fine-Tuning mit den Cookbook-Notebooks starten.** Basis für eigenes Training ist LFM3-1.7B-Base. Vier Colab-Notebooks mit TRL: SFT für strukturiertes JSON aus unordentlichen Dokumenten, DPO für Antworten aus abgerufenen Dokumenten oder begründete Ablehnung, GRPO für die richtige Tool-Wahl in einer App mit 108 Tools, CPT für eine neue Sprache (Beispiel Türkisch). Laut Card reicht eine einzelne GPU; Dauer und GPU-Typ fehlen.
10. **Lizenz vor Einsatz lesen.** Die LFM Open License v1.0 ist keine Standardlizenz wie Apache 2.0 oder MIT. Die Card nennt keine Bedingungen zu kommerzieller Nutzung oder EU. Für kommerzielle und Sovereign-AI-Setups den LICENSE-Text im Repo prüfen.

## Zahlen und ihre Herkunft

| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1,73 Mrd. (1.728.801.536) | Gesamtparameter in BF16, keine Angabe zu aktiven Parametern | Herstellerangabe, safetensors-Metadaten |
| 24 Layer: 13 / 5 / 6 | Gated Short Convolutions / Sliding-Window-Attention / Global Attention | Herstellerangabe |
| 256K Tokens | Kontext für Eingabe und Ausgabe zusammen | Herstellerangabe |
| 128.000 | Vokabulargröße | Herstellerangabe |
| 16 | unterstützte Sprachen, Deutsch dabei, keine Benchmarks je Sprache | Herstellerangabe |
| ca. 1 GB | Speicher bei 4-bit-Gewichten; ob Cache bei langem Kontext enthalten ist, bleibt offen | Herstellerangabe |
| 45,60 vs. 35,77 | LiveClaw, LFM3 vs. Qwen3.5 9B | Herstellerangabe |
| 68,64 vs. 66,53 | Claw-Eval General (EN), Durchschnitt | Herstellerangabe |
| 51,40 vs. 51,87 | Claw-Eval pass^3, hier liegt das 9B-Modell vorn | Herstellerangabe |
| 37,00 vs. 38,00 | BrowseComp-Plus, nur OpenClaw-Teilset | Herstellerangabe |
| 38,42 vs. 28,94 | WebArena-Verified | Herstellerangabe |
| 28,20 vs. 28,97 | EnterpriseOps-Gym | Herstellerangabe |
| 41,29 vs. 15,10 | AutomationBench (öffentliche Variante), größter Abstand | Herstellerangabe |
| 71,39 vs. 62,83 | BFCL V4 (Tool Use) | Herstellerangabe |
| 80,36 vs. 76,41 | ToolSandbox; Vorgänger LFM2.5 2.6B erreicht 78,04 | Herstellerangabe |
| 32,57 vs. 42,67 | MCP-Atlas, deutlicher Rückstand | Herstellerangabe |
| 68,01 vs. 69,44 | τ³-bench, Bestwert hat MiniCPM5 2B; Qwen3.5 9B: 67,11 | Herstellerangabe |
| 6 von 11 | Zeilen, in denen LFM3 den Bestwert hat (eigene Auszählung der sichtbaren Tabelle) | abgeleitet aus Herstellerangaben |
| 1.698 Likes, 89.946 Downloads | Plattformwerte zum Abrufzeitpunkt | Plattformdaten, ändern sich laufend |

## Wortlaute
- „You only have one tool right now: search_tools, which searches a catalog of many more tools.“ Empfohlener System-Prompt-Einstieg für das Deferred-Tools-Muster; die Card ergänzt, das Modell solle search_tools aufrufen, wenn kein vorhandenes Tool passt.
- „<tool_call><function=get_weather><parameter=city>Paris</parameter></function></tool_call>“ Beispiel des XML-Formats, das der eigene Parser verarbeiten muss.
- „You are a helpful assistant trained by Liquid AI.“ Standard-System-Prompt im ChatML-Template; wer ihn nicht ersetzt, bekommt diese Rolle.

## Grenzen und Widerspruch
- Die Kernbehauptung „ersetzt 9B“ stützt sich nur auf vom Hersteller gewählte Agent- und Tool-Benchmarks. Gegen Qwen3.5 9B liegt LFM3 klar vorn bei LiveClaw, WebArena-Verified, AutomationBench und BFCL V4, knapp hinten bei pass^3, BrowseComp-Plus und EnterpriseOps-Gym und deutlich hinten bei MCP-Atlas (10,10 Punkte). Wer viele MCP-Server anbinden will, sollte das selbst messen.
- Bei pass^3, der Metrik, die nach Zuverlässigkeit über mehrere Läufe klingt, ist LFM3 nicht Erster. Die Card erklärt die Metrik nicht.
- Benchmark-Bedingungen fehlen: Harness-Version, Anzahl Läufe, Sampling, Thinking an oder aus bei den Vergleichsmodellen. Fett und unterstrichen als Bestwert und Zweitbester ist aus der Formatierung abgeleitet, eine Legende fehlt.
- Die Tabelle ist im Material ab „Agentic coding“ abgeschnitten. Ergebnisse zu Coding, Reasoning, Wissen, Instruktionsbefolgung und Mehrsprachigkeit sind nicht sichtbar.
- Keine Angaben zu Trainingsdaten, Datenherkunft, Sicherheitsevaluation, Halluzinationsraten, Durchsatz, Latenz oder Speicher bei vollem Kontext.
- Deutsch steht auf der Sprachliste, die Qualität auf Deutsch ist nicht belegt.
- Die großen Sprünge gegenüber dem Vorgänger (etwa 3,02 auf 38,42 bei WebArena-Verified) werden nicht erklärt.
- Lizenzbedingungen sind ungeprüft. Es gibt keine Community-Diskussion oder Praxisberichte im Material.
