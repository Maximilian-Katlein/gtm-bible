# KI-Agenten stellen in einem Prüfungsversuch bessere Fragen als KPMG-Prüfer

> **Quelle:** [AI agents ask better questions than KPMG accountants in audit trial](https://europeanbusinessmagazine.com/ai-agents-better-questions-kpmg/) · EBM Newsdesk (European Business Magazine), Sekundärbericht auf Basis eines Financial-Times-Artikels; Berichtsgegenstand KPMG UK · Artikel mit Diskussion auf Hacker News ([Diskussion](https://news.ycombinator.com/item?id=50547777), 371 Punkte) · 2026-11-19
> **Sprecher verkauft:** Wirtschaftsprüfung (Big Four); hier ein internes Experiment, kein Produkt · **Zielmarkt der Aussagen:** börsennotierte Unternehmen in Großbritannien (FTSE 250), Prüfungs- und Beratungsbranche · **Beweislage:** ein einziger Parallelversuch, ausschließlich KPMG-Selbstauskunft über FT und EBM, ohne Qualitätszahlen.

## Worum es geht
Können KI-Agenten Teile einer Abschlussprüfung übernehmen, die bisher Teams junger Prüfer erledigen? KPMG UK hat das im Experiment Project Exponential an einem FTSE-250-Unternehmen getestet. Relevant ist der Fall für alle, die Multi-Agenten-Systeme für regelbasierte Wissensarbeit planen oder verkaufen, und für alle, die einschätzen wollen, wie belastbar solche Erfolgsmeldungen sind.

## Was man anwenden kann
1. **Agenten über die ganze Prozesskette, nicht nur für Hilfsarbeit.** Mehr als 100 Agenten liefen neben einem konventionellen Prüfteam und deckten Datenbeschaffung, Analyse, Dokumentation, Entwürfe für Schlussfolgerungen und Vorschläge für die nächsten Prüfschritte ab. Für eigene Piloten heißt das: Die Kette als Ganzes testen, nicht einzelne Handgriffe. Technische Details (Modelle, Framework, Rollen) nennt der Artikel nicht.
2. **Parallelbetrieb statt Ersatz als Pilotdesign.** Die Agenten arbeiteten neben dem menschlichen Team, ein Prüfungspartner zeichnete den Versuch ab, die Ergebnisse flossen aber nicht in die formelle Billigung des Abschlusses ein. So lässt sich ein KI-Prozess in einem haftungsrelevanten Umfeld vergleichen, ohne Haftungsrisiko einzugehen.
3. **Mit kleinem Ausbauschritt skalieren.** Die Entwicklung dauerte laut KPMG rund vier Monate. Der nächste Schritt sind bis zu 20 größere Prüfungen, kein Rollout über tausende Mandate, weil die Technik dafür noch nicht reif ist. Ein Pilot im zweistelligen Bereich ist ein realistisches Muster für regulierte Branchen.
4. **Datenqualität des Kunden vorab prüfen.** Manche Unternehmen haben nicht die sauberen, strukturierten Daten, die Agenten brauchen. Wer Agenten in Kundenprozesse einbaut, sollte den Reifegrad der Buchhaltungs- und Dokumentendaten als Eingangskriterium setzen, sonst bleibt der Nutzen aus.
5. **Menschlichen Eingriff für komplexe Regelwerke einplanen.** Im Versuch musste ein Prüfer eingreifen, weil ein Agent regulatorische Anforderungen falsch mit der Unternehmensdokumentation abglich. Review-Punkte gehören an die Stellen, an denen Regelwerk und Firmendaten zusammengeführt werden.
6. **Review nicht dem Spardruck opfern.** Ein Kommentator warnt: Wenn KI-Investitionen Produktivitätsgewinne beweisen sollen, entsteht Druck, Ausgaben nur oberflächlich zu prüfen. Der Artikel nennt Übervertrauen in automatisierte Schlussfolgerungen und erfundene Ausgaben selbst als Risiko. Review-Zeit sollte daher fest im Business Case stehen.
7. **Einsatzfeld nach Aufgabentyp wählen.** Mehrere Kommentatoren verorten den Vorteil dort, wo Verfahren fest und der Suchraum definiert ist (Regelanwendung, Prüfung, Hacking als adversarieller Prozess). Schwächer seien Agenten bei schlecht definierten Aufgaben wie der Datenfindung vor Prüfungsbeginn und bei Planung ohne Anleitung. Das sind Meinungen ohne Daten, taugen aber als Prüfraster für Use-Case-Auswahl.
8. **Preisfrage im Angebot klären.** KPMG nennt potenziell erhebliche Zeitersparnis, bestätigt aber nicht, dass Honorare sinken. Wer Dienstleistungen mit Agenten effizienter macht, muss entscheiden, ob der Gewinn als Marge bleibt oder an Kunden geht. Kunden werden danach fragen.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| mehr als 100 | KI-Agenten im Versuch Project Exponential | Herstellerangabe (KPMG via FT) |
| 1 | geprüftes Unternehmen, FTSE 250, nicht genannt | Herstellerangabe |
| ca. 4 Monate | Entwicklungszeit der Technologie | Herstellerangabe |
| bis zu 20 | geplante größere Prüfungen im Ausbau | Herstellerangabe |
| keine | Zeitersparnis, Kosten, Fehlerquote, Maß für „bessere Fragen“ | fehlt im Artikel |

## Wortlaute
- „gone considerably deeper into issues than the regular audit team“: Aussage von Cath Burnet, Head of Audit bei KPMG UK, in indirekter Rede. Eingeschränkt durch „in several instances“ und „sometimes“, also keine durchgängige Überlegenheit.
- „its findings were not used as the basis for formally approving the company’s accounts“: die Abgrenzung, die den Versuch vom echten Mandat trennt.
- „does not establish that AI can replace accountants or independently deliver a reliable statutory audit“: die Einschränkung des Artikels selbst, schwächer als seine Überschrift.

## Grenzen und Widerspruch
- **Nur Selbstauskunft.** KPMG führte den Versuch durch und berichtet selbst. Der FT-Originalartikel liegt nicht vor, der in der Diskussion verlinkte FT-Link ist abgeschnitten. Ein Kommentator vergleicht das mit Behauptungen von Tech-Konzernen über den Anteil KI-generierten Codes.
- **Kein Maßstab.** Was „bessere Fragen“ sind, wie oft das vorkam, welche Prüfer mit welcher Erfahrung verglichen wurden und wie hoch die Fehlerrate der Agenten war, bleibt offen. Mehrere Kommentare vermuten, das Ergebnis sage mehr über unerfahrene, überlastete Prüfer als über die KI. Ein Kommentator nennt den deutschen Spottnamen „Kinder Prüfen Meine Gesellschaft“.
- **Vollständigkeit statt Einsicht?** Eine Hypothese aus der Diskussion: Agenten starten mit den häufigsten Standardfragen und schlagen Prüfer damit durch Vollständigkeit, nicht durch besondere Einsicht.
- **Anreizproblem.** Ein Kommentator fragt, ob schärfere Prüfung überhaupt gewollt ist, wenn Prüfungsmandate mit Beratungsumsatz verflochten sind, und verweist auf Enron. Einordnung: Enrons Prüfer war Arthur Andersen, nicht KPMG. Die Frage an Branchenpraktiker blieb unbeantwortet.
- **Extrapolation in der Diskussion.** Einige Kommentare leiten eine generelle Überlegenheit trainierter Agenten ab (einmal trainieren statt jeden Menschen neu, keine Bequemlichkeit, Training mit Experten über Netzwerke wie Mercor). Belege fehlen; das Argument zur Bequemlichkeit setzt gelöstes Alignment und Cheating voraus.
- **Stichprobe oder Vollprüfung** ist im Artikel offen. Die These, Prüfung werde zur Vollerhebung, stammt nur aus einem Kommentar, ebenso der Einwand, dass Vollprüfung jede Kleinigkeit zum Befund macht.
- **Regulatorik.** Der britische Financial Reporting Council warnt laut Artikel, KI dürfe Unabhängigkeit und professionelle Skepsis nicht untergraben. Eine konkrete FRC-Publikation wird nicht zitiert. Die Verantwortung für das Prüfungsurteil bleibt beim Menschen.
- **Keine Technik.** Modelle, Orchestrierung, Datenzugriff, Hosting und Datenschutz bleiben unbenannt. Für Nachbau oder Anbieterwahl gibt die Quelle nichts her.
