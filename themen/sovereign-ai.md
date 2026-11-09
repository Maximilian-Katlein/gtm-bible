# Sovereign AI

Diese Seite sammelt, was Unternehmen beachten müssen, wenn sie KI-Modelle unabhängig von einzelnen Anbietern, Regionen und Vertragsbedingungen betreiben wollen. Sie fasst Belege zu Verfügbarkeit, Hardwarebedarf beim Selbst-Hosting und Prüfpflichten für offene Modelle zusammen.

Stand: 2026-11-09 · 2 Quellen · 3 Learnings

## Zahlen und Richtwerte

### Hardwarebedarf beim Selbst-Hosting

- **Kimi K3.1 Pro braucht mehrere Server.** Rechnerisch belegen allein die Gewichte rund 2,84 TB, der KV-Cache kommt noch dazu. Ein Server mit 8 GPUs zu je 141 GB hat zusammen etwa 1,1 TB und reicht deshalb nicht. Ohne API muss das Modell über mehrere Knoten verteilt laufen. In den Safetensors-Metadaten steht: „"total": 2780110363392“. *Bedingung:* Die Zahl ist eine eigene Ableitung aus den Metadaten des Original-Checkpoints und gilt für den souveränen Betrieb ohne API. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)

## Warnungen und Fehler

### Verfügbarkeit nach Region und Vertrag

- **Die Region oder der Vertrag kann ein Modell ausschließen, auch wenn es fachlich gut ist.** Goldman Sachs nahm Claude im April in Hongkong von seiner internen Plattform, JPMorgan folgte im Juni. ChatGPT und Gemini blieben bei Goldman in Hongkong verfügbar. Laut einem Anthropic-Sprecher war Claude „had never been officially supported in Hong Kong“. *Bedingung:* Das betrifft multinationale Unternehmen mit Standorten außerhalb der Regionen, die ein Anbieter offiziell unterstützt. *Beleglage:* Die Quelle stellt das nur als Behauptung dar und belegt es nicht. [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)

### Lücken in Model Cards

- **Bei Kimi K3.1 Pro bleibt vieles offen, das man für den Betrieb selbst klären muss.** Die Card nennt keine unterstützten Sprachen und sagt nichts zur Qualität auf Deutsch. Sie nennt auch keine Inferenz-Engine und keine Hardwareanforderungen. Angegeben ist nur „library_name: transformers“. Das Modell bringt außerdem eigenen Code mit (custom_code), der vor dem Einsatz geprüft werden muss. Wer das Modell souverän in Europa betreiben will, muss Sprache, Laufzeitumgebung und Code-Prüfung selbst klären. *Bedingung:* Das gilt für Selbst-Hosting in abgeschotteten oder regulierten Umgebungen. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)

## Offene Fragen

- **Mit welcher Genauigkeit wurden die 2,84 TB gerechnet?** Der Wert in den Metadaten (2.780.110.363.392) ist vermutlich die Zahl der Parameter. Wie viel Speicher die Gewichte brauchen, hängt von den angenommenen Datentypen ab. Mit quantisierten Gewichten kann der Bedarf deutlich anders ausfallen. Das Learning ist als Herstellerangabe eingestuft, die Rechnung selbst ist aber eine eigene Ableitung. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Wie gut ist Kimi K3.1 Pro auf Deutsch?** Die Card sagt dazu nichts, eigene Tests stehen noch aus. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Wurde Claude ganz entfernt oder nur Claude Code, und in welchem Jahr?** Der Titel der Quelle spricht von Claude Code, das Learning von Claude. Die Monate April und Juni stehen ohne Jahr. [Goldman zieht Claude Code zurück](../quellen/2026/11/2026-11-09-goldman-sachs-is-pulling-claude-code-from-its-bankers-and-tr.md)
