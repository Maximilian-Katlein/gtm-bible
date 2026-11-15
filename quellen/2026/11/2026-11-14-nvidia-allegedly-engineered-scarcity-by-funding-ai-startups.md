# Nvidia soll Knappheit inszeniert haben, indem es KI-Startups den Kauf seiner GPUs finanzierte

> **Quelle:** [Nvidia allegedly engineered scarcity by funding AI startups to buy its GPUs](https://www.techpowerup.com/354814/nvidia-allegedly-engineered-scarcity-by-funding-ai-startups-to-buy-its-gpus) · TechPowerUp (Autor Cpt.Jank), zitiert das Wall Street Journal über Wccftech · Artikel mit Diskussion ([Hacker News](https://news.ycombinator.com/item?id=50493251), 521 Punkte) · 2026-11-14
> **Sprecher verkauft:** nichts direkt, Gegenstand ist NVIDIAs Geschäft mit Rechenzentrums-GPUs · **Zielmarkt der Aussagen:** KI-Startups, kleine Cloud-Anbieter und Hyperscaler als GPU-Abnehmer · **Beweislage:** Bericht aus dritter Hand mit anonymen WSJ-Quellen, ohne Dokumente und mit nur einer Zahl.

## Worum es geht
Der Bericht wirft NVIDIA Zirkelfinanzierung vor: NVIDIA beteiligt sich an KI-Startups und kleinen Cloud-Anbietern, die das Geld wieder für NVIDIA-GPUs ausgeben. Die Frage dahinter ist, wie viel der sichtbaren KI-Hardware-Nachfrage echt ist und wie viel der Hersteller selbst bezahlt. Relevant ist das für alle, die GPU-Kapazität einkaufen, an kleine Cloud-Anbieter vertrauen oder Geschäftsmodelle auf Annahmen über Compute-Knappheit bauen.

## Was man anwenden kann
1. **Herstellerfinanzierte Nachfrage als Prüfpunkt.** Laut WSJ floss NVIDIA-Kapital in Firmen, die damit NVIDIA-GPUs kauften und Rechenzentren bauten. Wer Nachfragesignale für Compute bewertet, sollte fragen, ob der Käufer vom Lieferanten finanziert wird. Gilt als Prüfpunkt, nicht als belegter Befund für NVIDIA.
2. **Gegenparteirisiko kleiner Cloud-Anbieter prüfen.** Colette Kress, laut Artikel CFO und kommissarische CEO, soll eingewandt haben, dass die finanzierten kleinen Cloud-Anbieter sich die GPUs eigentlich nicht leisten können. Wer bei kleinen GPU-Clouds Kapazität bucht, sollte deren Finanzierungsquelle und Laufzeit kennen. Hängt die Nachfrage am Kapital des Herstellers, endet sie, wenn dieser umsteuert. Für Hyperscaler gilt der Einwand laut Bericht nicht.
3. **Überangebot und Knappheit auseinanderhalten.** Die Überschrift spricht von künstlicher Knappheit, der Text beschreibt eine „Lawine“ von TSMC-GPUs ohne unmittelbare Käufer. Für Einkaufsentscheidungen zählt die Lage beim Hersteller: Ein Abnahmerisiko auf Herstellerseite ist ein anderes Signal als echter Mangel.
4. **Custom Silicon als Treiber beobachten.** Laut Artikel stiegen Hyperscaler von Standardkomponenten auf eigene Chips um, und NVIDIA wich vermutlich auf kleine Cloud-Anbieter aus. In der HN-Diskussion (blueblisters) heißt es dazu, Kunden würden zu Konkurrenten und freie TSMC-Kapazität gern übernehmen. Das ist Interpretation, keine Zahl.
5. **Quellenkette prüfen, bevor man zitiert.** Der Kommentar von dcrazy benennt die Kette WSJ, dann Wccftech, dann TechPowerUp. Für Aussagen in eigenen Analysen oder Pitches nur das WSJ-Original verwenden, das hier nicht vorliegt.
6. **Eigene Modelle als Nachfragequelle (Hypothese).** blueblisters meint, NVIDIA hätte mit Frontier-Forschung an offenen Modellen überschüssige Rechenkapazität selbst auslasten können. Im selben Kommentar folgt die Einschränkung, dass solche Wetten auch hätten scheitern können. Spekulation ohne Zahlen.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 250 Mrd. US-Dollar | Deal zwischen NVIDIA und OpenAI, den Kress zurückfahren wollte; Laufzeit und Struktur unbekannt | WSJ über Wccftech, ohne Dokument |
| bis zu 500 US-Dollar | Preiserhöhung GeForce RTX 50 (Meldung 2026-11-03) | Nur Überschrift in der Seitenleiste |
| rund 10 % | Geplanter Aufschlag von AMD auf GPUs, Chipsätze, womöglich CPUs (Meldung 2026-09-17) | Nur Überschrift |
| 311 | Kommentare der HN-Diskussion, davon etwa 14 im Material | Zählung der Plattform |

Die Seitenleiste meldet außerdem ohne Inhalt: Einstellung der RTX 5090 zugunsten von Workstation-GPUs (2026-10-10), eine Aussage des Dell-CEO zu verschärfter Speicherknappheit 2027, den Rücktritt von Jensen Huang (2026-11-12) und eine interne Untersuchung zu ihm. Ein Zusammenhang mit dem WSJ-Vorwurf ist nicht belegt.

## Wortlaute
- „calling her a "deer in the headlights,"“: soll Huangs Reaktion auf Kress' Einwand im August gewesen sein. Steht für den behaupteten internen Konflikt, Wortlaut stammt aus anonymen Quellen.
- „I think the fact that everything is scarce is fantastic for us“: in einem TechPowerUp-Kommentar (#17) zitiert, Urheber und Datum nicht genannt. Wird als Beleg für ein Interesse an Knappheit gedeutet.
- „A WSJ article filtered through a gaming enthusiast website filtered through a general tech enthusiast website.“: dcrazy zur Quellenkette.

## Grenzen und Widerspruch
- **Keine Belege.** Drei Absätze aus dritter Hand, anonyme Quellen, keine Dokumente. Der Kommentar von metadat hält fest, dass es keinen konkreten Beweis gibt.
- **Normales Corporate Venturing?** throwaway69123 sieht gewöhnliche Anlage von Überschusskapital: Beteiligungen mit Abschlag, ein Teil fließt als margenstarker Umsatz zurück. Das trägt nur, wenn die Empfänger die GPUs später aus eigenen Einnahmen zahlen können. Genau das bestreitet Kress laut Bericht für kleine Cloud-Anbieter.
- **Nicht neu.** da_chicken verweist auf einen Guardian-Artikel vom 2025-12-28 zur Zirkelfinanzierung (nicht gelesen). Neu wären nur Absicht und interner Streit.
- **Motivhypothesen.** ex-aws-dude liest das Muster als kurzfristige Kursstützung, nickalaso vermutet Profiteure unter Leerverkäufern. Beides ohne Evidenz. abhinai zweifelt an der Neutralität der Autoren, ohne Textstelle.
- **Innere Widersprüche.** Der Artikel erklärt nicht, wie Startup-Finanzierung DRAM-Knappheit erzeugen soll, und Überschrift (Knappheit) und Text (Überangebot) passen nicht zusammen.
- **Rechtliche Folgen offen.** Die Frage nach Kartell- oder RICO-Verfahren (TechPowerUp-Kommentar #22) ist Laienspekulation.
- **Begrenzte Relevanz.** Keine Angaben zu Cloud-GPU-Preisen, EU-Verfügbarkeit oder Folgen für den Betrieb offener Modelle. Hoffnungen von Hardware-Käufern auf sinkende Preise widersprechen den gleichzeitig gemeldeten Preiserhöhungen.
