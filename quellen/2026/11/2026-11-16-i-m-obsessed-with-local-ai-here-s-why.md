# Ich bin besessen von lokaler KI. Hier ist der Grund

> **Quelle:** [I'm Obsessed With Local AI. Here's Why](https://www.youtube.com/watch?v=UtFo1ZNC2ns) · Greg Isenberg, Late Checkout · Video · 2026-11-16
> **Sprecher verkauft:** B2B-Startup-Strategie, Communitys, KI-Produktberatung · **Zielmarkt der Aussagen:** SMB, nicht-technische Gründer, Nischendienstleister und Bootstrapped-Startups · **Beweislage:** Erfahrungswissen und Einschätzungen des Sprechers ohne Benchmarks, Kundendaten oder Umsatzbelege

## Worum es geht
Wann lohnt es sich, ein offenes Modell auf eigener Hardware statt in der Cloud laufen zu lassen, und wie steigt man ohne Programmierkenntnisse ein? Das Video richtet sich an nicht-technische Gründer und kleine B2B-Teams. Es liefert einen Einstiegspfad mit Werkzeugen, Modellgrößen und Hardwarestufen sowie drei Geschäftsideen samt Markteintritt.

## Was man anwenden kann
1. **Richtige Prüffrage stellen.** Nicht fragen, ob das lokale Modell das stärkste Cloud-Modell schlägt. Sondern: Reicht es für genau diese Aufgabe, und macht die lokale Ausführung das Produkt besser? (02:40)
2. **Einsatzkriterien abhaken.** Lokal lohnt sich laut Sprecher bei sensiblen Kundendaten, Offline-Nutzung, Feldarbeit, niedriger Latenz, Audio-Eingaben und internen Abläufen, die immer wieder laufen. Später ergänzt er Kamera-Kontext, hohe API-Kosten und sicherheitsbewusste Kunden (02:10, 37:05).
3. **Landschaft in vier Bausteinen denken.** Modell (das Gehirn), Warehouse zum Finden (Hugging Face), Software zum Ausführen, Workflow als eigentliches Produkt (03:11). Der Wert liegt im Workflow, nicht im Modell.
4. **Model Card systematisch lesen.** Auf Hugging Face je Modell prüfen: Zweck, Parametergröße, Lizenz, Hardware anderer Nutzer, unterstützte Datentypen (Text, Bild, Audio, Tool-Nutzung, Embeddings) und Quantisierung (04:35).
5. **Werkzeug nach Rolle wählen.** LM Studio für Nicht-Techniker: Desktop-App, Modell suchen, herunterladen, chatten (05:20). Ollama für Entwickler: Terminal plus lokale API (05:40). Darunter liegen llama.cpp als verbreitete Inferenzbasis, MLX für Apple Silicon und Google AI Edge mit LiteRT-LM für mobile Apps (06:00).
6. **Modellgröße an Hardware koppeln.** 2B bis 4B Parameter für Telefone und Edge-Geräte, 12B für normale Laptops, 26B bis 31B für leistungsstarke Workstations (07:10). Quantisierung komprimiert: Q4 läuft leichter, Q8 hält mehr Qualität bei mehr Speicherbedarf (08:40). GGUF ist das gängige Dateiformat auf normalen Rechnern (09:25).
7. **Am ersten Tag nur ein Modell.** Einsteiger starten mit Gemma 4 E4B, lernen den Ablauf und wechseln erst danach zu größeren, kleineren oder spezialisierten Modellen (12:25). Spezialvarianten: Embedding Gemma für Suche, Function Gemma für Funktionsaufrufe, PaliGemma für Bildverstehen, ShieldGemma für Sicherheit (11:30).
8. **RAM bestimmt den Spielraum.** 8 GB: klein anfangen. 16 GB: brauchbare Tests mit E4B. 32 GB: deutlich mehr Raum für komplexe Abläufe. Große Modelle brauchen starke GPUs oder Systeme wie DGX Spark (21:50).
9. **Hybrid für vertrauliche Daten.** Das lokale Modell liest sensible Entwürfe, entfernt oder fasst private Details zusammen. Nur die bereinigte Fassung geht für tieferes Reasoning an ein Cloud-Modell (13:20). Bedingung: Firmen mit Datenschutzanforderungen.
10. **Modellfamilie nach Käufer prüfen.** Llama: großes Ökosystem, Lizenz genau lesen (14:30). Qwen: stark bei Code, Mehrsprachigkeit, langem Kontext. In regulierten Branchen lokale Ausführung offener Gewichte klar vom gehosteten Dienst trennen (14:55). DeepSeek: günstig und stark bei Reasoning und Code, kann aber Einkaufs-, Sicherheits- und geopolitische Bedenken bei Enterprise-Kunden auslösen (15:25). Mistral: europäische Familie, Aufstellung aus offenen und kommerziellen Modellen unübersichtlich (16:35).
11. **Erster Praxistest in 30 Minuten.** Ordner „customer notes“ mit 10 Support-Tickets anlegen, Gemma lokal eine Datei „what customers are telling us.md“ schreiben lassen: Beschwerden, Ursachen, eine Aufgabe für diese Woche (22:50). Für Entwickler: lokalen Server in LM Studio starten, dann sprechen eigene Skripte das Modell über localhost an (19:40).
12. **Workflow vor Fine-Tuning.** Nicht mit Training oder Tuning beginnen. Erst einen wiederkehrenden Ablauf finden und mehrfach ausführen (24:30).
13. **Mini-Eval bauen.** Dieselben 10 Notizen lokal mit Gemma und mit einem starken Cloud-Modell verarbeiten. Vergleichen nach Vollständigkeit, korrekten Zitaten und Formattreue (25:05). Danach aufteilen: lokal für private, wiederholte, schnelle, Offline- und Massenaufgaben; Cloud für tiefes Reasoning, riesigen Kontext und breite Recherche (26:00).
14. **Geschäftsideen nach fünf Merkmalen filtern.** Kunde mit sensiblen Daten, wiederkehrender Prüfarbeit, schlechter Branchensoftware, teuren Fehlern und einem Ablauf nah am Gerät (26:30). Bedingung: Bootstrapped-B2B-Gründer.
15. **Drei Ideen mit Service-Einstieg.**
    - Lokaler QA-Prüfer für ambulante Pflegedienste: Besuchsnotizen und Pflegepläne vor Einreichung auf Lücken prüfen. Einstieg als Dienstleistung für 5 kleine Pflegedienste, die 20 häufigsten Mängel werden zur Produkt-Checkliste (27:25, 28:40).
    - Offline-Feldbericht-Copilot für Sanierungsbetriebe: Techniker macht Fotos und Sprachnotizen, die App entwirft den Versicherungsbericht ohne Netz. Eine Nische wählen (Wasserschäden), mit Inhabern sprechen, in der Demo drei alte Einsätze aufbereiten (29:30, 30:50).
    - Lokaler Pre-Send-Prüfer für freie Berufe: ausgehende Mails, Angebote, Verträge auf Compliance-Risiken wie Renditeversprechen prüfen. Start mit einer Branche und einem Dokumenttyp, etwa Mails unabhängiger Vermögensberater; anonymisierte Beispiele sammeln und in Prüfregeln übersetzen (32:20, 33:40).
16. **Persönliches „Local AI Lab“.** Ordner mit 10 arbeitsrelevanten Dateien anlegen und Gemma daraus wiederverwendbare Berichte wie einen wöchentlichen „Business Pulse“ erzeugen lassen (34:50).

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 24 Monate | Zeitfenster für „lächerlich viele“ Geschäftschancen durch lokale KI | Behauptung ohne Beleg |
| 13 Mrd. US-Dollar | Angebliche Übernahmebewertung von Hugging Face | Behauptung ohne Beleg, Sprecher sagt „I think“ |
| 2B–4B / 12B / 26B–31B | Parametergrößen je Hardwareklasse (Telefon, Laptop, Workstation) | Einschätzung des Sprechers |
| 8 / 16 / 32 GB RAM | Hardwarestufen für lokale Tests | Einschätzung des Sprechers |
| 11434 | Port der lokalen Ollama-API | Sprecher unsicher („I think“) |
| 10 | Support-Tickets bzw. Dateien für Einstiegstest und Eval | Vorschlag, kein Ergebnis |
| 5 / 20 | Pilot-Pflegedienste / häufigste Mängel als Checkliste | Vorschlag, kein Kundenfall |
| 3 | Alte Einsätze für die Sanierer-Demo | Vorschlag, kein Kundenfall |

## Wortlaute
- „Is this model good enough for the job, and does running it locally make the product better?“ (02:40). Die Entscheidungsfrage für jede Modellwahl.
- „Read these customer notes and turn them into a one page memo about what customers are struggling with, what has changed, and what the business should fix this week.“ (18:20). Testprompt für den ersten lokalen Lauf in LM Studio.
- „ollama run Gemma 4 E4B“ (05:40, 20:10). Startbefehl laut Sprecher; vorher „ollama pull“. Die genaue Modellbezeichnung im Ollama-Katalog vor Nutzung prüfen.
- „send me three old jobs and I'll show you how fast your techs could create reports.“ (30:50). Demo-Angebot an Sanierungsbetriebe.
- „I look for a customer with sensitive data, repeated review work, bad software usually, expensive mistakes“ (26:30). Filter für Geschäftsideen.

## Grenzen und Widerspruch
- Keine Benchmarks. Ob Gemma 4 E4B für medizinische Notizen, Versicherungsberichte oder Compliance-Prüfung gut genug ist, zeigt der Sprecher nicht. Genau dafür empfiehlt er selbst das Eval, liefert aber kein Ergebnis.
- Die drei Startup-Ideen sind Konzepte. Es fehlen Preise, Akquisitionskosten, Entwicklungsaufwand und Belege, dass Kunden zahlen. Die Behauptung, Berichte entstünden „in Sekunden“, ist nicht vorgeführt.
- Haftung und Regulierung der Ideen (Gesundheitsdaten, Finanzberatung) werden nur über das Argument „bleibt lokal“ behandelt. Ob ein lokales Modell rechtliche Prüfpflichten erfüllt, bleibt offen. Übertragbarkeit auf deutsche Pflegedienste oder Berater ist nicht geprüft.
- Hardware- und Größenangaben sind Faustregeln. Leistungseinbußen von LiteRT-LM auf älteren Mobilgeräten werden nicht konkretisiert.
- Bewertungen der Modellfamilien sind persönliche Eindrücke. Zu Microsoft Phi sagt der Sprecher nur, er habe es in vielen Fällen nicht gut funktionieren sehen (17:05).
- Hugging-Face-Bewertung und Ollama-Port nennt er selbst unsicher.
- Der Sprecher verkauft Startup- und KI-Produktberatung; das 24-Monats-Fenster ist eine Prognose ohne Grundlage.
