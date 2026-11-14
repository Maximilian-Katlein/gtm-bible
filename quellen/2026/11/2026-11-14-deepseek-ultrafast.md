# DeepSeek Ultrafast: Inferenz-Engine für DeepSeek-V4.1-Flash auf Blackwell-GPUs

> **Quelle:** [DeepSeek Ultrafast](https://github.com/basetenlabs/deepseek-ultrafast) · Baseten (GitHub-Organisation basetenlabs) · Repository-README mit Hacker-News-Diskussion · 2026-11-14
> **Sprecher verkauft:** KI-Inferenzplattform, DeepSeek-V4.1-Flash-Fast über die Baseten Model APIs · **Zielmarkt der Aussagen:** Betreiber von Blackwell-GPU-Clustern, Inferenzanbieter für offene Modelle, Entwickler von Coding-Agents und Harnesses · **Beweislage:** alle Messwerte sind Herstellerangaben von einem einzigen Prompt, ohne Vergleich mit anderen Engines.

## Worum es geht
Wie schnell lässt sich ein offenes Modell wie DeepSeek-V4.1-Flash auf aktueller Rechenzentrums-Hardware ausliefern, und wie betreibt man es über mehrere Server, ohne Prompts neu zu berechnen? Das Repository liefert eine in Rust geschriebene Engine mit Bauanleitung, Benchmark-Skript und einem Ansatz für KV-Cache-Sharing per RDMA. Relevant ist das für Teams mit 4 bis 8 Blackwell-GPUs und für alle, die Inferenzanbieter für offene Modelle bewerten.

## Was man anwenden kann
1. **Hardware vor allem anderen prüfen.** Die Engine läuft nur auf 4x GB300 (sm_103a), 4 oder 8x B300 (sm_103a) oder 4 oder 8x B200 (sm_100a). Dazu kommen das CUDA 13 Toolkit, die Modellgewichte im Ordner `models/` und eine Redis-Instanz. Kleinere oder ältere GPUs werden nicht unterstützt. Wer diese Hardware nicht hat, kann das Projekt nur über die gehostete Variante bei Baseten nutzen.

2. **Bauen in drei Schritten.** Auf Debian oder Ubuntu die Systempakete installieren, darunter `libibverbs-dev` und `librdmacm-dev` für den RDMA-Stack sowie `redis-server`. Dann `rustup` ohne Standard-Toolchain installieren, die Toolchain aus `rust-toolchain.toml` nachziehen und mit `cargo build --release` die Binaries `run` und `serve` bauen. Die Zielarchitektur wird über `DSUF_SM` gesetzt. Für B200 ist das `sm_100a`, ein eigenes Beispiel dafür zeigt das README nicht.

3. **Server starten und Bereitschaft prüfen.** Redis lokal ohne Persistenz starten (`--save ''`, `--appendonly no`), danach `serve` mit `DSUF_REDIS_URL`, `--ckpt models`, der GPU-Liste und `--port 8000`. Auf einer 8-GPU-Maschine alle acht GPUs angeben. Bereit ist der Server, wenn `localhost:8000/readyz` den Status 200 liefert, laut Hersteller nach etwa 20 Sekunden. RDMA-Ports erkennt der Server selbst.

4. **Bestehende Clients ohne Umbau anbinden.** Der Server spricht eine OpenAI-kompatible API unter `/v1/chat/completions`. Im Beispiel wird das DeepSeek-Harness `dsh` per `npx` mit `DEEPSEEK_BASE_URL=http://localhost:8000` und `DEEPSEEK_API_KEY=none` angesprochen. Lokal wird kein API-Key geprüft. Vor einem Betrieb außerhalb eines geschützten Netzes muss also eine eigene Authentifizierung davor.

5. **Benchmark-Zahlen richtig lesen.** Das Skript teilt die `completion_tokens` durch die Zeit zwischen erstem Inhalts-Token und Streamende. Die Zeit bis zum ersten Token ist darin nicht enthalten und wird separat ausgegeben. Gemessen wird ausschließlich mit einem Tetris-Prompt bei deaktiviertem Thinking, also stark vorhersagbarer Code-Ausgabe. Wer die Engine bewertet, sollte eigene Prompts aus dem tatsächlichen Einsatz messen, weil die Acceptance Length bei weniger vorhersagbarem Text vermutlich sinkt.

6. **Herstellerzahlen selbst nachrechnen.** Tokens pro Sekunde ergeben sich aus Acceptance Length geteilt durch Schrittzeit. 5,6 Tokens pro 2,71 ms ergeben etwa 2.066 Tokens/s und passen zur 8x-B300-Spalte. Für 4x GB300 ergibt dieselbe Rechnung etwa 1.697 statt der tabellierten 1.740, die Tabellenwerte sind offenbar Mittelwerte aus Läufen mit abweichender Acceptance Length. Diese Prüfung lohnt sich bei jeder Speculative-Decoding-Angabe.

7. **Doppelte GPU-Zahl nicht mit doppeltem Tempo verwechseln.** Der Wechsel von 4x GB300 auf 8x B300 bringt laut Tabelle rund 18 Prozent mehr Decode-Tempo und rund 12 Prozent mehr Prefill. Der Vergleich ist unsauber, weil sich auch der GPU-Typ ändert. Für eine Kostenrechnung heißt das: Die zusätzlichen vier GPUs kaufen vor allem geringere Latenz, nicht proportional mehr Durchsatz pro Anfrage.

8. **Mehrere Server ohne Sticky Sessions betreiben.** Jeder Server hält die KV-Caches der zuletzt geführten Konversationen im Host-Speicher. Landet ein Folge-Turn auf einem anderen Server, holt dieser den Cache per RDMA direkt vom Besitzer, statt den Prompt neu zu berechnen. Redis führt Buch, welcher Server welchen Cache besitzt. Damit entfällt prefix-aware Routing, ein einfacher Load Balancer genügt. Ein Beispiel liegt unter `deploy/kubernetes.yaml`. Voraussetzung sind RDMA-fähige Netzwerkkarten zwischen den Servern.

9. **Coding-Agents mit offenem Referenzcode für Low-Level-Optimierung einsetzen.** Baseten gibt an, die Kernels von Coding-Agents optimiert zu haben, die währenddessen den Quellcode von FlashInfer und SGLang lesen konnten. Übertragbar ist das Muster: dem Agenten eine ausgereifte Open-Source-Implementierung als Kontext geben. Wie viel die Agents beigetragen haben, ist nicht beziffert.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 1.740 Tokens/s | Decode, 4x GB300 (TP4), Tetris-Prompt, Thinking aus | Herstellerangabe |
| 2.060 Tokens/s | Decode, 8x B300 (TP8), gleicher Prompt | Herstellerangabe |
| 1.700 bis 1.770 / 1.980 bis 2.170 Tokens/s | Streuung der Reproduktionsläufe auf 4x GB300 / 8x B300 | Herstellerangabe |
| 3,30 ms / 2,71 ms | Zeit pro Decode-Schritt, 4x GB300 / 8x B300 | Herstellerangabe |
| 3,24 bis 3,37 ms / 2,69 bis 2,74 ms | Streuung der Schrittzeit über 30 Läufe | Herstellerangabe |
| 5,6 Tokens/Schritt | Mittlere Acceptance Length, beide Varianten | Herstellerangabe |
| 5,1 bis 6,1 / 5,3 bis 6,1 Tokens/Schritt | Streuung der Acceptance Length über 30 Läufe | Herstellerangabe |
| 13,2 s (76.000 Tokens/s) | Prefill von 1.000.000 Tokens, 4x GB300 | Herstellerangabe |
| 11,7 s (85.000 Tokens/s) | Prefill von 1.000.000 Tokens, 8x B300 | Herstellerangabe |
| ca. 20 s | Zeit bis `/readyz` den Status 200 liefert | Herstellerangabe |
| 0,04 s | Zeit bis zum ersten Token in der Beispielausgabe | Herstellerangabe |
| ca. 18 % / 12 % | Zuwachs Decode / Prefill von TP4 auf TP8 | eigene Rechnung aus Herstellerzahlen |
| 4 Commits, 166 Stars, 4 Forks | Reife des Repositorys beim Abruf | Stand beim Abruf |
| 2.400 TPS | in der Diskussion genannte Marke, Herkunft unklar | Behauptung ohne Beleg |

## Wortlaute
- „implement the tetris game. output HTML code directly - no explanation.“ (README, Messmethode). Der einzige Benchmark-Prompt, zugleich das Demo-Szenario im Video. Er erzeugt lange, gut vorhersagbare Code-Ausgabe, was die Acceptance Length begünstigt.
- „The kernels were optimized by coding agents that could read the source of FlashInfer and SGLang while they worked.“ (README). Steht für das Muster, Agents mit offenem Referenzcode an Performance-Arbeit zu setzen.
- „Thanks to DeepSeek's extreme KV cache compression, the transfers are very fast and can be done on every request.“ (README). Die zentrale Begründung für das Multi-Server-Design, ohne Messwert.

## Grenzen und Widerspruch
- **Ein Prompt, kein Vergleich.** Alle Decode-Werte stammen vom Tetris-Prompt mit deaktiviertem Thinking. Unklar ist, ob Einzelanfragen oder Last mit Batching gemessen wurden. Es fehlen Vergleiche mit SGLang, vLLM oder anderen Anbietern, Kosten pro Token und eine Qualitätsmessung gegenüber dem Standardmodell.
- **Technik teils unbenannt.** Quantisierung und Rechenpräzision sowie der konkrete Draft-Mechanismus hinter der Acceptance Length nennt das README nicht.
- **KV-Transfer ohne Messwerte.** Latenz der RDMA-Transfers, Cache-Größe pro Konversation und Verdrängungsregeln im Host-Speicher fehlen. Die Aussage, Transfers seien bei jeder Anfrage möglich, ist eine Behauptung und gilt ausdrücklich für DeepSeeks komprimiertes KV-Format, nicht automatisch für andere Modelle.
- **Modell- und Lizenzfragen offen.** Parameterzahl, Architektur, Trainingsdaten und Modelllizenz von DeepSeek-V4.1-Flash werden nicht genannt. Der Lizenztyp des Repositorys war im Auszug nicht lesbar. Für einen Einsatz in der EU oder mit kommerzieller Nutzung muss beides separat geprüft werden.
- **Gehostete Variante unklar.** Ob DeepSeek-V4.1-Flash-Fast auf den Baseten Model APIs exakt diese Engine nutzt, steht nicht im README. Preise und Rate Limits fehlen.
- **Sehr junges Projekt.** 4 Commits zum Abrufzeitpunkt. Produktionsreife ist nicht belegt.
- **Diskussion dünn.** Drei Kommentare mit wenig technischem Gehalt. Ein Nutzer sieht den Hauptnutzen bei interaktiver Arbeit mit kurzen Rückkopplungsschleifen statt bei Agents, die eine Aufgabe in einem Durchgang lösen. Ein anderer weist spöttisch auf die Hardware-Hürde hin: 8x B300 hat praktisch niemand privat. Ein dritter wirft ironisch Missbrauchsrisiken auf (Vorschlag einer „abliterated“ Version) und nennt 2.400 TPS als Marke, die im README nicht vorkommt. Gegenbelege zu den Benchmarks gibt es nicht.
