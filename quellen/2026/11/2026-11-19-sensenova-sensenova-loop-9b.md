# sensenova/SenseNova-Loop-9B

> **Quelle:** [sensenova/SenseNova-Loop-9B](https://huggingface.co/sensenova/SenseNova-Loop-9B) · sensenova, SenseNova (Hugging-Face-Organisation sensenova) · Model Card · 2026-11-19
> **Sprecher verkauft:** Open-Weight-Modell, multimodal (Bild und Text zu Text), Apache-2.0 · **Zielmarkt der Aussagen:** nicht angegeben · **Beweislage:** nur Hub-Metadaten, die Modellkarte selbst enthält keinen Text.

## Worum es geht
SenseNova-Loop-9B ist ein Open-Weight-Modell mit rund 9,4 Mrd. Parametern. Es nimmt Bild und Text entgegen und gibt Text aus. Die Seite beantwortet nur eine Frage: Was lässt sich aus den Metadaten über Lizenz, Größe, Sprachen und Laufzeit ableiten? Sie richtet sich an Teams, die Open-Weight-Modelle für einen eigenen oder souveränen Betrieb sichten. Für eine Einsatzentscheidung reicht das Material nicht. Es eignet sich nur als Vormerkung.

## Was man anwenden kann
1. **Lizenz vor Nutzung im Repo prüfen.** Das Metadatenfeld nennt Apache-2.0. Diese Lizenz erlaubt grundsätzlich kommerzielle Nutzung, Änderung und Weitergabe und enthält eine Patentlizenz. Die Lizenzdatei im Repository wurde nicht geprüft. Vor dem Einsatz sollte man sie lesen und mit dem Metadatenfeld abgleichen.
2. **Speicherbedarf selbst rechnen.** 9.409.812.208 Parameter liegen in BF16 vor (2 Byte), 3.151.744 in F32 (4 Byte). Daraus ergeben sich rund 18,8 GB (17,5 GiB) allein für die ungequantisierten Gewichte. Eine 24-GB-GPU reicht knapp für die Gewichte. KV-Cache, Aktivierungen und Bildverarbeitung kommen hinzu, daher ist langer Kontext auf so einer Karte unsicher. Die Rechnung ist eine eigene Ableitung, die Karte nennt keine Hardware.
3. **Latenz messen, nicht aus der Größe schätzen.** Die Tags nennen „looped-transformer“. Bei solchen Architekturen werden Schichten in der Regel mehrfach durchlaufen und teilen Gewichte. Trifft das hier zu, sagt die Zahl 9B wenig über den Rechenaufwand pro Token. Durchsatz und Antwortzeit gehören dann in einen eigenen Lasttest auf der Zielhardware. Die Karte bestätigt die Bauweise nicht.
4. **Custom Code abschotten.** Das Repo trägt den Tag custom_code und nutzt transformers mit safetensors. Vermutlich ist trust_remote_code=True nötig, das ist aber aus dem Tag geschlossen, nicht aus einer Anleitung. In souveränen oder abgeschotteten Umgebungen den mitgelieferten Code vorab lesen und auf einen festen Commit pinnen. Ob vLLM, llama.cpp oder GGUF funktionieren, ist offen.
5. **Deutsch selbst evaluieren.** Angegeben sind nur Englisch und Chinesisch. Für deutschsprachige B2B-Aufgaben wie Vertriebstexte oder Dokumentenanalyse mit Bildanteil braucht es einen eigenen Test mit echten Unterlagen. Die Leistung auf Deutsch ist weder positiv noch negativ belegt.
6. **Hub-Resonanz nicht als Qualitätssignal lesen.** Zwei Tage nach Veröffentlichung hat das Repo 329 Likes und 964 Downloads, also knapp drei Downloads pro Like. Das zeigt Aufmerksamkeit bei noch geringer Nutzung. Über Qualität sagt es nichts.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 2026-11-17, 10:16:41 UTC | Anlage des Repositorys | Herstellerangabe (Hub-Metadaten) |
| 9.412.963.952 | Parameter gesamt laut safetensors | Herstellerangabe, unklar ob inklusive Vision-Encoder |
| 9.409.812.208 | Parameter in BF16 | Herstellerangabe |
| 3.151.744 | Parameter in F32, rund 0,03 Prozent | Herstellerangabe |
| ca. 18,8 GB / 17,5 GiB | Speicher der ungequantisierten Gewichte | eigene Rechnung aus Herstellerangaben |
| 329 Likes, 964 Downloads | Resonanz am 2026-11-19 | Hub-Zähler, Momentaufnahme |

## Grenzen und Widerspruch
- Der Text der Modellkarte ist leer. Alles hier stammt aus Metadaten und Tags.
- Keine Benchmarks, kein Vergleichsmodell, kein Vorgänger, keine Angabe, was neu ist.
- Keine Kontextlänge, keine aktiven Parameter, keine Schichtzahl, keine Zahl der Schleifendurchläufe, keine Attention-Variante, keine Angaben zum Vision-Encoder.
- Die Bedeutung des Tags „mhc“ ist aus dem Material nicht ableitbar. Man sollte keine bekannte Technik dahinter annehmen, bevor ein Paper oder Modelltext sie benennt.
- Keine Angaben zu Trainingsdaten, Trainingsumfang oder Sicherheitsbewertung. Für den EU-Einsatz bleibt die Herkunft der Trainingsdaten offen.
- Keine Hardwareanforderungen, keine Quantisierungen, keine Ausführungsanleitung.
- Die Einordnung zu Looped Transformern ist allgemeines Wissen, nicht durch die Karte belegt.
- Für eine belastbare Bewertung braucht es den Karteninhalt oder einen technischen Report.
