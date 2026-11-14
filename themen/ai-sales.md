# AI im Vertrieb und B2B Sales

Diese Seite sammelt, was Quellen über den Einsatz von KI im Vertrieb und im B2B-Verkauf sagen: Modellwahl für Sales-Research, KI-gestützter Outreach, Agenten im Vertriebsablauf, Gründervertrieb für KI-Produkte und den Verkauf von KI an Enterprise und öffentliche Hand. Dazu kommen Gesprächs-, Pitch-, Verhandlungs- und Organisationstaktiken, die solche Abläufe ergänzen, jeweils mit Bedingung, Art des Belegs und Quelle.

Stand: 2026-11-14 · 12 Quellen · 41 Learnings

## Was mehrfach belegt ist

- **Genauigkeitsangaben von KI-Anbietern mit eigenen Tests nachmessen, bevor man sie im Vertrieb einsetzt (2 Quellen).** Der Halluzinationsvergleich unten stammt vom Hersteller eines der getesteten Modelle. Für Research zu Accounts und Ansprechpartnern vorher mit eigenen Fragen nachmessen. Für das Lead-Scoring von AgentRun ist die Genauigkeit ebenfalls nicht belegt und sollte mit eigenen Eval-Cases gemessen werden. Bedingung: KI für Research oder Lead-Bewertung. Beleg: Herstellerangabe in beiden Fällen, die Empfehlung zum Nachmessen ist Einordnung. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [AgentRun](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md)
- **Wiederkehrende Kundenfragen sammeln und standardisiert beantworten (2 Quellen).** Hormozi sortiert alle bisherigen DM-Verläufe in Fragegruppen und beantwortet sie am Webinar-Ende nach Häufigkeit. Bei Solve Intelligence wiederholen sich nach Festlegung des Ideal Customer Profile etwa 60 Fragen, sodass die Demo standardisierbar wird. Bedingung: vorhandener Verlauf an Kundenanfragen (Webinar-Fall) oder B2B Founder-led Sales mit klarem ICP. Beleg: Behauptung ohne Beleg (Scale or Fail) und eigene Daten (Solve Intelligence). Details unter „Pitch und Einwände“ und „Gründervertrieb für KI-Produkte“. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md), [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
- **Folgeangebote nicht erst am Ende, sondern mitten im Ablauf platzieren (2 Quellen, beide Hormozi in der Reihe Scale or Fail und damit nicht unabhängig).** Zur Hälfte und bei zwei Dritteln einer Intensivphase anbieten, solange der Kunde noch mitten in der Entscheidung ist. Im Finale verallgemeinert Hormozi das: Neben dem Inhalt eines Angebots auch den Zeitpunkt testen. Einem vom Ende in die Mitte verlegten Upsell schreibt er etwa 50 Mio. $ zu. Bedingung: Programm mit Intensivphase, im Finale ohne Einschränkung formuliert. Beleg: Behauptung ohne Beleg in beiden Fällen. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md), [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- **DM-Outreach täglich bis zum Plattformlimit betreiben, nicht darüber hinaus (3 Quellen, alle aus der Reihe Scale or Fail und damit nicht unabhängig).** Für Instagram nennt Hormozi 10 bis 20 Kontakte pro Tag, weil die Plattformen begrenzen. Für LinkedIn wird empfohlen, die DM-Limits jeden Tag voll auszuschöpfen. Im Finale gehört eine tägliche LinkedIn-Kadenz zum Maßnahmenpaket eines B2B-Eventplaners. Bedingung: Kleinbetriebe und Dienstleister, US-Markt. Beleg: eigene Daten (Ep. 1), Behauptung ohne Beleg (Ep. 5), Kundenfall (Finale). [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md), [Scale or Fail Ep. 5](../quellen/2026/11/2026-11-14-how-to-get-rich-for-service-based-businesses-thank-me-later.md), [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)

## Taktiken und Abläufe

### Outreach mit KI

- **Personalisierten Erstkontakt per KI für große Listen erzeugen.** Die KI wird an die Kontaktliste angebunden (im Beispiel rund 12.000 Makler). Sie schreibt je Kontakt persönliche Angaben in eine Tabelle und erzeugt daraus mit einer Vorlage jede Erstnachricht. Jeweils 100 Nachrichten gegenlesen und gegen einen generischen Opener testen. Bedingung: Outreach an lokale Partner. Die Wirkung ist in der Quelle nicht gemessen. Beleg: Behauptung ohne Beleg. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- **Outreach auf den Kanal mit dem besten Verhältnis von LTV zu CAC bündeln und per KI um Telefonnummern ergänzen.** Im Fall ist das LinkedIn: täglich die DM-Limits ausschöpfen, die Kontakte per KI-Scrape um Telefonnummern ergänzen und diese in einen Dialer geben. Bedingung: US-Markt. In der EU sind Scraping und Kaltanrufe durch DSGVO und UWG stark eingeschränkt. Beleg: Behauptung ohne Beleg. [Scale or Fail Ep. 5](../quellen/2026/11/2026-11-14-how-to-get-rich-for-service-based-businesses-thank-me-later.md)

### Agenten im Vertriebsablauf

- **Vom Gesprächsprotokoll zum Angebot mit einem Prompt.** In einer Demo liest ein Agent die Meeting-Notizen aus Granola, schreibt die Angebotsmail als Gmail-Entwurf, erzeugt einen Stripe-Zahlungslink und legt das Projekt in Notion an, alles über MCP-Anbindungen. Bedingung: Kleinstfirmen mit Gmail, Granola, Stripe und Notion. Es handelt sich um einen vorbereiteten Testfall mit fiktivem Prospect, nicht um einen echten Kunden. Beleg: eigene Daten (Demo). [Kurs KI-Agenten](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)

### Gründervertrieb für KI-Produkte

- **Founder-led Sales als Befragung führen, nicht als Pitch.** Die Gespräche drehen sich um Arbeitsabläufe und Zeitfresser des Kunden. Nach Festlegung des ICP wiederholen sich etwa 60 Kundenfragen, die Demo wird dadurch standardisierbar. Bedingung: B2B Founder-led Sales mit klarem ICP. Beleg: eigene Daten. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
- **Ein unfertiges KI-Produkt zuerst an Fachkräfte verkaufen.** Fachkräfte tolerieren Mängel eher als Laien, weil sie einzelne nützliche Funktionen erkennen. Patentanwälte blieben trotz Mängeln und lieferten Feedback. Bedingung: B2B-Spezialsoftware für Fachberufe. Beleg: Kundenfall. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)

### KI an Enterprise und öffentliche Hand verkaufen

- **Für die Fertigungsindustrie auf dem Kunden-Tenant anbieten.** Fertigungsunternehmen verlangen, dass kein geistiges Eigentum an Unterauftragsverarbeiter zurückfließt. Wer an die Industrie verkauft, sollte Agentenplattform und Modellanpassung direkt auf dem Tenant des Kunden anbieten. Bedingung: Fertigungsindustrie, Enterprise B2B. Beleg: Kundenfall. [Mistral CEO](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
- **Große Kunden in Custom Deployments ermutigen, möglichst alle internen Daten und Arbeitsweisen hochzuladen.** Das erhöht laut den Gründern von Solve Intelligence die Kundenbindung stark. Zur Spannung mit der Tenant-Empfehlung siehe „Strittig“. Bedingung: Enterprise- und Mid-Market-Kanzleien. Beleg: eigene Daten. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
- **Skalierungsoptionen schon in den Pilotvertrag schreiben.** Nach einem validierten Pilot steigt der Bedarf laut Mistral sprunghaft, Zahlen unter „Zahlen und Richtwerte“. Bedingung: Enterprise-Rollout nach erfolgreichem Pilot. Beleg: Kundenfall. [Mistral CEO](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
- **Public Sector nach Staatsgröße unterscheiden.** Der Vertrieb an Regierungen kleiner Staaten ähnelt laut Mensch einem normalen Enterprise-Vertrieb mit kurzen Wegen. In großen Staaten ist die Beschaffung deutlich komplexer und fragmentierter. Bedingung: Public Sector Sales. Beleg: Herstellerangabe. [Mistral CEO](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

### Vertriebsorganisation im Dienstleistungsgeschäft

- **Zweistufig verkaufen: Außendienst gewinnt den Auftrag, Innendienst erweitert ihn.** Der Außendienst gewinnt die Reparatur. Danach folgt ein Onboarding-Gespräch im Innendienst, in dem weitere Leistungen verkauft werden. Vor jedem der beiden Gespräche läuft ein eigenes VSL (Video Sales Letter), das genau dieses Gespräch rahmt. Bedingung: lokaler Dienstleister mit Außen- und Innendienst. Beleg: Behauptung ohne Beleg. [$10M Service Business](../quellen/2026/11/2026-11-14-how-i-would-build-a-10m-service-business-if-i-had-to-start-o.md)
- **Provision für Haustürverkäufer in einen Betrag pro Tür übersetzen.** Statt eines Prozentsatzes rechnet man den Verdienst auf jede geklopfte Tür herunter, Rechnung unter „Zahlen und Richtwerte“. So wird jede einzelne Tür zu einem greifbaren Betrag. Bedingung: Haustürakquise, neue Verkäufer mit 40 bis 50 Türen je Abschluss. Beleg: Behauptung ohne Beleg. [$10M Service Business](../quellen/2026/11/2026-11-14-how-i-would-build-a-10m-service-business-if-i-had-to-start-o.md)

### Pitch und Einwände

- **Jeden Pitch vom Käufer aus rückwärts bauen.** Zuerst klären, was der Käufer will, dann den Pitch darauf aufbauen. Im Finale nannten beide Finalisten nicht, was ein Investor will: schnelles Wachstum, hohe Profitabilität, Verteidigbarkeit. Bedingung: keine genannt, das Beispiel ist ein Investorenpitch. Beleg: Behauptung ohne Beleg. [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- **Pitch für kaltes Publikum bauen.** Ein Pitch, der so tut, als kenne das Publikum einen nicht, konvertiert kalte und warme Leute. Ein Pitch für Warme konvertiert nur Warme. Bedingung: Skalierung über das bestehende Publikum hinaus, der Fall ist B2C. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- **Jedes Kaufbedenken in vier Schritten auflösen.**
  1. was die Leute denken,
  2. warum das falsch ist, mit einem eigenen früheren Irrtum,
  3. was stattdessen stimmt,
  4. Beweis durch Zahlen und Geschichten.

  Bedingung: keine genannt. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- **Häufige Fragen aus DM-Verläufen am Webinar-Ende beantworten.** Alle bisherigen DM-Gespräche in Fragegruppen sortieren und live beantworten, die häufigste zuerst (im Beispiel 40 %), dann die zweite (25 %), dann den Rest. Bedingung: vorhandener Verlauf an Kundenanfragen. Beleg: Behauptung ohne Beleg. Siehe auch „Was mehrfach belegt ist“. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- **Folgeangebote während der laufenden Intensivphase verkaufen.** Zur Hälfte, bei zwei Dritteln und als letzte Chance am Ende anbieten, solange der Kunde noch „mitten in der Entscheidung“ ist. Im Finale rät Hormozi, den Zeitpunkt eines Angebots genauso zu testen wie seinen Inhalt. Bedingung: Programm mit Intensivphase. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md), [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- **Fehlenden Mitentscheider mit kurzer Rückgabegarantie überbrücken.** Fehlt beim Kauf ein Mitentscheider (im Fall der Partner), eine dreitägige Rückgabegarantie ohne Begründung anbieten, damit der Kauf sofort möglich ist. Bedingung: Mitentscheider fehlt im Verkaufsgespräch, belegt nur für B2C. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)

### Reziprozität im Gespräch

- **Zwei Arten von Reziprozität unterscheiden.** Emotionale Reziprozität heißt, dass sich das Gegenüber gut fühlt. Materielle Reziprozität heißt, etwas Greifbares oder Geldwertes zu tun. Beide sollen laut Tracy ein Bedürfnis nach Gegenleistung erzeugen. Bedingung: allgemeine Gesprächs- und Verhandlungssituationen, Zielmarkt nicht genannt. Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Vor einem Termin mit einem Prospect einen kleinen Gefallen planen.** Beispiele: einen für ihn relevanten Zeitungsausschnitt mitbringen oder ein Buch schenken. Wirkung und Antwortquoten belegt Tracy nicht. Bedingung: nur wo die Geschenkrichtlinien des Kunden das zulassen, im Enterprise- und Behördeneinkauf vorher prüfen. Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Viele Fragen stellen und genau zuhören.** Je mehr man fragt, desto mehr mag einen das Gegenüber und desto offener ist es für Einfluss. In Verhandlungen soll gezeigte Offenheit die Gegenseite vernünftiger machen. Bedingung: Verhandlungen allgemein, Branche und Dealgröße nicht genannt. Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)

### Verhandlung und Wettbewerb

- **Zweifel an der Konkurrenz entlang Risiko, Geschwindigkeit und Aufwand säen.** Drei Hebel im Gespräch:
  - ein Aufschlag für Lieferung am selben Tag, mit 10 % beginnen und auf 20 % steigern,
  - ein Kostendeckel aus Schätzung plus Puffer,
  - die Frage, ob der Wettbewerber einen Deckel oder eine Versicherung bietet.

  Bedingung: Das Produkt ist von außen kaum unterscheidbar. Der Deckel lohnt sich nur, wenn Schätzungen erfahrungsgemäß um etwa 30 % abweichen und nicht um das Doppelte. Beleg: Behauptung ohne Beleg. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- **Strittige Klausel zurückstellen.** Bei Widerstand gegen eine einzelne Klausel diese beiseitelegen, den Rest des Vertrags durchgehen und am Ende zurückkehren. Bedingung: umfangreiche Verträge mit mehreren Klauseln, Tracy nennt 50 bis 60 Seiten und Mehrjahreslaufzeit. Beleg: Anekdote. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Langsam zustimmen.** Auch bei Punkten ohne Bedeutung für einen selbst nur zögernd zustimmen, um später bei wichtigen Themen mehr Stärke zu haben. Mechanismus, Tempo und Risiko für den Dealverlauf bleiben unerklärt. Bedingung: Verhandlungen über mehrere Punkte. Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Das Wort „fair“ wiederholt einsetzen.** Etwa „Das wäre mir gegenüber nicht fair“, um ein Bedürfnis nach Ausgleich auszulösen. Tracy belegt das nur mit Beispielen aus Politik und Kindererziehung, nicht mit Verkaufsfällen. Bedingung: Abwehr einer Forderung in Verhandlungen. Ob erfahrene Einkäufer die Taktik erkennen, bespricht die Quelle nicht. Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Kein Zugeständnis ohne Gegenleistung.** Das gilt auch, wenn das Zugeständnis für einen selbst keinen Wert hat. Sonst folgen laut Tracy weitere Forderungen ohne Ausgleich. Bedingung: Verhandlungen allgemein, ein Skript zum Einfordern der Gegenleistung fehlt. Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Preis und Konditionen als getrennte Hebel behandeln.** Ein höherer Preis ist tragbar, wenn Zahlungsweise oder Laufzeit deutlich günstiger sind. Zur Illustration bietet ein anonymer Verhandler $1.000 für einen Stift, der $150 gekostet hat, zahlbar in $1 bei jeder Begegnung mittwochs in New York, ohne Zinsen. Bei einer Begegnung pro Woche wären das rund 19 Jahre (Rechnung der Redaktion, nicht im Video). Bedingung: aus Käufersicht formuliert, die Übertragung auf die Verkäuferseite zeigt Tracy nicht. Das Stift-Beispiel ist kein realistischer Verhandlungsfall. Beleg: Behauptung ohne Beleg, Beispiel als Anekdote. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)

## Zahlen und Richtwerte

- **Cold Outbound auf LinkedIn an Fachjuristen:** Anfragen an 1.000 Patentanwälte ergaben rund 50 Vernetzungen, 5 Gespräche und 1 zahlenden Kunden. Als grober Planwert: etwa 1.000 Anfragen pro Neukunde. Zitat: „maybe five of them agree to jump on a call and then one of them pays.“ Bedingung: B2B Cold Outbound auf LinkedIn an Fachkräfte, Frühphase. Beleg: eigene Daten. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
- **Kanalvergleich beim Outreach an lokale Makler:** E-Mails brachten laut dem Gast null Konversion, SMS brachten etwas Traktion. Auf Instagram empfiehlt Hormozi, Profile per Agent zu finden und täglich nur 10 bis 20 Kontakte anzuschreiben, weil die Plattformen begrenzen. Bedingung: lokale Makler als Zielgruppe, Kleinbetrieb in den USA. Beleg: eigene Daten. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- **Vertragswert bei einem B2B-Eventplaner:** Über ein Preismodul und Mehrjahresverträge stieg der durchschnittliche Vertragswert von 44.000 $ auf 200.000 $, die Abschlussquote stieg dabei von 44 auf 48 %. Begleitend liefen Setter-Modell, Mengenfrage, drei VSLs, Angebot am selben Tag und tägliche LinkedIn-Kadenz. Welcher Hebel wie viel beitrug, trennt die Quelle nicht. Zitat: „We took our average contract price from 44,000 to an average of $200,000“. Bedingung: B2B-Dienstleister mit wiederkehrendem Geschäft. Beleg: Kundenfall. [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- **Halluzinationsraten von Modellen mit Tool-Nutzung** (Kimi Hallu Bench Hard, niedriger ist besser):

  | Modell | Wert |
  |---|---|
  | GPT-6 Astra | 5,5 |
  | Kimi K3.1 Pro | 8,3 |
  | Claude Opus 5.5 | 15,0 |
  | Claude Fable 5.1 | 23,3 |

  Für Sales-Research ist dieser Wert wichtig. Der Test ist aber ein interner Benchmark des Herstellers Moonshot. Bedingung: vor dem Einsatz mit eigenen Kundenfragen gegenprüfen. Beleg: Herstellerangabe. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- **Vom Pilot zum Rollout:** Enterprise-KI-Projekte starten laut Mistral oft mit 8 GPUs im Pilot und brauchen nach der Validierung Tausende GPUs für einen einzigen Anwendungsfall. Bedingung: Enterprise-Rollout nach erfolgreichem Pilot. Beleg: Kundenfall. [Mistral CEO](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
- **Zeitpunkt von Folgeangeboten:** Nur am Ende der Intensivphase angeboten, kauft laut Hormozi meist ein Drittel, mit zusätzlichen Angeboten zur Hälfte und bei zwei Dritteln die Hälfte bis zwei Drittel. Einem vom Ende in die Mitte verlegten Upsell schreibt er etwa 50 Mio. $ zu. Bedingung: Programm mit Intensivphase, Ausgangsquote im Fall 10 %. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md), [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- **Pitch für kaltes Publikum:** Bei 9 % Konversion auf warmes Publikum hält Hormozi mit einem Pitch für Kalte das Doppelte für möglich. Bedingung: B2C-Fall. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- **Provision pro Tür:** 10 % Provision auf ein Ticket von 4.000 $ ergeben 400 $. Geteilt durch 50 Türen je Abschluss sind das 10 $ pro geklopfter Tür. Bedingung: Haustürakquise, neue Verkäufer mit 40 bis 50 Türen je Abschluss. Beleg: Behauptung ohne Beleg. [$10M Service Business](../quellen/2026/11/2026-11-14-how-i-would-build-a-10m-service-business-if-i-had-to-start-o.md)

## Werkzeuge

- **AgentRun, Template „inbound-lead“:** Recherchiert jeden per Webhook gelieferten Lead und bewertet ihn von 0 bis 100 gegen das eigene ICP. Open Source. Zitat: „Researches each lead a webhook sends and scores it 0 to 100 against your ideal customer profile“. Bedingung: B2B mit definiertem ICP und Webhook aus CRM oder Formular. Genauigkeit nicht belegt. Beleg: Herstellerangabe. [AgentRun](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md)
- **Agent mit MCP-Anbindungen an Granola, Gmail, Stripe und Notion:** In der Demo erledigt er Angebotsmail, Zahlungslink und Projektanlage aus einem Prompt, Ablauf unter „Agenten im Vertriebsablauf“. Bedingung: Kleinstfirmen, vorbereiteter Testfall. Beleg: eigene Daten (Demo). [Kurs KI-Agenten](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)
- **KI-Scrape plus Dialer:** Kontakte aus dem Outreach-Kanal werden per KI um Telefonnummern ergänzt und in einen Dialer eingespeist. Ein konkretes Produkt nennt die Quelle nicht. Bedingung: US-Markt, in der EU rechtlich stark eingeschränkt. Beleg: Behauptung ohne Beleg. [Scale or Fail Ep. 5](../quellen/2026/11/2026-11-14-how-to-get-rich-for-service-based-businesses-thank-me-later.md)
- **Menu Close:** Ein Abschlussskript mit vier Schritten, das Hormozi sein Lieblingsskript nennt: „I've spent so long honing those four steps to make it just crush.“ Ein Dachdecker berichtet, es stärke Vertrauen, seine Run-Rate stieg von 370.000 $ auf 2 Mio. $. Die vier Schritte werden in der Quelle nicht erklärt, der Anteil des Skripts am Wachstum ist nicht getrennt. Bedingung: beratungsintensiver Verkauf mit Optionen. Beleg: Behauptung ohne Beleg. [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)

## Wortlaute und Vorlagen

### Outreach, Agenten und Wettbewerb

- Frage, die Zweifel am Angebot des Wettbewerbers weckt: „Hey, did the other guys give you a cap?“ Bedingung: Das eigene Angebot hat einen Kostendeckel und das Produkt ist sonst kaum unterscheidbar. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- Ablauf für KI-Personalisierung im Wortlaut: „hook up AI to the list, create an Excel sheet that has personalized information“. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- Ablauf für KI-Anreicherung mit Telefonnummern: „we want to do an AI scrape of the contacts to get numbers. And then we want to feed that into a dialer“. Bedingung: US-Markt. [Scale or Fail Ep. 5](../quellen/2026/11/2026-11-14-how-to-get-rich-for-service-based-businesses-thank-me-later.md)
- Prompt aus der Agenten-Demo: „review my meeting notes with Maltoshi from today and then draft up the email sending the proposal and creating the Stripe payment link“. Bedingung: Agent mit MCP-Zugriff auf Notizen, Mail und Zahlungsanbieter. [Kurs KI-Agenten](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)
- Begründung für Bereitstellung auf dem Kunden-Tenant: „when we work with manufacturing companies they don't want their IP to flow back to a subprocessor.“ [Mistral CEO](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)

### Gründervertrieb und Enterprise

- Wiederkehrende Fragen nach Festlegung des ICP: „there's the same sort of 60 questions that they will always ask“. Bedingung: B2B Founder-led Sales mit klarem ICP. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
- Warum Fachkräfte ein unfertiges Produkt nutzen: „even though our product sucked, there was certain specific things where if you were an actual lawyer“. Bedingung: Spezialsoftware für Fachberufe. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
- Ansage an große Kunden: „custom deployments, dump all your stuff in as much as possible.“ Bedingung: Enterprise- und Mid-Market-Kanzleien, siehe „Strittig“. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)

### Pitch und Einwände

- Ausgangspunkt jedes Pitches: „whenever I'm selling anything, I always have to start with what is you reverse engineer from the prospect.“ [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- Grundsatz für den Pitch: „You got to sell like it's cold to warm and it converts everything. If you sell like it's warm to everyone, you'll only convert warm.“ [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- Gerüst für Einwände: „They think this, right? And then you're going to say why wrong? ... What's right? And then proof.“ [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- Zeitpunkt für Folgeangebote: „you want to sell when they're mid-decision, not making a new decision. So, they're still in flight“. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- Zeitpunkt als eigener Testgegenstand: „It's not just how you sell, it's when you sell.“ [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- Fehlender Mitentscheider: „husband's not there. So I would just say give a three-day no sweat guarantee.“ Bedingung: B2C-Fall. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)

### Vertriebsteam

- Provision pro Tür als Ansage an neue Haustürverkäufer: „want to go make 10 bucks? Knock that door.“ Bedingung: Haustürakquise mit rund 50 Türen je Abschluss. [$10M Service Business](../quellen/2026/11/2026-11-14-how-i-would-build-a-10m-service-business-if-i-had-to-start-o.md)

### Gespräch und Verhandlung

- Emotionale Vorleistung zum Gesprächsbeginn: „Thank you. It's a pleasure to meet you. I know how busy you are. Thank you very much for your time.“ Bedingung: Erstgespräch oder Termin mit Entscheider. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- Strittige Klausel vertagen: „Let's put that aside for now. Let's go through the rest of the material and then let's come back to that later.“ Bedingung: umfangreiche Verträge mit mehreren Klauseln. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- Grundregel für Zugeständnisse: „never give something without getting something in return.“ [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)

## Warnungen und Fehler

### Outreach und Recht

- **Identische SMS an viele Nummern führen zur Sperre.** Laut Hormozi sperren Netzbetreiber eine Nummer als Spam, wenn derselbe Text an 100 Empfänger geht: „if the carrier see you send that same thing to 100 people, they they spam the number.“ Das Risiko sinkt mit personalisierten Texten und einem echten Nachrichtenkanal mit lokaler Vorwahl statt SMS aus einem Newsletter-Tool. Diese Lösung kostet mehr. Bedingung: SMS-Outreach in den USA. Beleg: Behauptung ohne Beleg. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- **KI-Scrape von Telefonnummern und Kaltanrufe per Dialer nicht ungeprüft in die EU übertragen.** Die Taktik stammt aus dem US-Markt. In der EU schränken DSGVO und UWG das Anreichern von Kontaktdaten und Kaltanrufe stark ein. [Scale or Fail Ep. 5](../quellen/2026/11/2026-11-14-how-to-get-rich-for-service-based-businesses-thank-me-later.md)

### Gründervertrieb

- **„Ohne Vertriebsmitarbeiter“ heißt nicht ohne Vertriebsaufwand.** Bei Solve Intelligence bedeutet es Gründervertrieb mit hohem Reiseaufwand. Mitgründer Chris verbrachte in 30 bis 40 Tagen nur zwei Nächte zu Hause, weil Kunden persönlich besucht wurden: „in the last 30 or 40 days I've probably spent two nights in my own bed.“ Bedingung: globaler Enterprise-Vertrieb mit Hauptumsatz in den USA. Beleg: eigene Daten. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)

### KI im Kundenkontakt und Herstellerangaben

- **Kunden-Agenten sperren und selbst LLMs im Service einsetzen wirkt wie Doppelmoral.** In der Diskussion zur Sperre von KI-Buchungsagenten klagt ein Nutzer, er sei 1000 Meilen vom Ziel gestrandet und habe wegen eines LLM keinen Menschen erreicht: „yet when they strand me 1000miles from my destination I cant get through to a human due to an LLM.“ Bedingung: Unternehmen, die KI im Service einsetzen und Kunden-KI einschränken. Beleg: Anekdote, Einzelerfahrung. [United, KI-Agenten-Verbot](../quellen/2026/11/2026-11-13-united-airlines-bans-ai-agents-from-booking-flights-on-behal.md)
- Herstellerangaben zur Genauigkeit von Modellen und Lead-Scoring nicht ungeprüft übernehmen, siehe „Was mehrfach belegt ist“. [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md), [AgentRun](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md)

### Gesprächs- und Drucktaktiken

- **Bonus mit „eigentlich darf ich das nicht“ ist eine Drucktaktik.** Im Video wird sie ohne Beleg empfohlen: „I'm not supposed to do this but I'll give you the the bonus if they if they ask for it.“ Vor dem Einsatz auf Glaubwürdigkeit und in der EU auf Transparenzregeln prüfen. Bedingung: B2C-Einzelgespräche. Beleg: Behauptung ohne Beleg. [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- **Reziprozität wirkt auch negativ.** Wer das Gegenüber verletzt, löst laut Tracy das Bedürfnis aus, es heimzuzahlen: „If you do something that hurts me, then I feel a deep need to get even as well.“ Beleg: Behauptung ohne Beleg. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Geschenke an Prospects vorher gegen Richtlinien prüfen.** Ein mitgebrachtes Buch oder ein anderer Gefallen kann im Enterprise- und Behördeneinkauf gegen Geschenkregeln des Kunden verstoßen. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- **Tracys Regeln als Hypothesen behandeln, nicht als belegte Methode.** Die Quelle liefert keine Daten. Wirkaussagen stützen sich auf „viele“, „Psychologen“ und politische Fernsehdebatten ohne Quellenangabe, etwa „according to psychologists, this deep need to be even.“ [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)

## Strittig

- **Wie viele Kundendaten sollen beim KI-Anbieter landen?**
  - Möglichst viele: Solve Intelligence ermutigt große Kanzleien in Custom Deployments, alle internen Daten und Arbeitsweisen hochzuladen, weil das die Kundenbindung stark erhöht. Bedingung: Enterprise- und Mid-Market-Kanzleien. Beleg: eigene Daten. [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)
  - Möglichst keine: Fertigungsunternehmen verlangen laut Mistral, dass kein geistiges Eigentum an Unterauftragsverarbeiter zurückfließt, deshalb Bereitstellung auf dem Tenant des Kunden. Bedingung: Fertigungsindustrie, Enterprise B2B. Beleg: Kundenfall. [Mistral CEO](../quellen/2026/11/2026-11-13-mistral-ceo-why-openai-anthropic-will-come-for-your-business.md)
  - Vermutete Erklärung: Branche und Bereitstellungsmodell. In der Fertigung ist das IP selbst das Schutzgut, bei Kanzleien steht der Nutzen aus Vorlagen und Arbeitsweisen im Vordergrund. Ob Solves Custom Deployments beim Kunden oder beim Anbieter laufen, sagt die Quelle nicht. Laufen sie auf Kundeninfrastruktur, lösen sich beide Positionen weitgehend auf.

## Offene Fragen

### Outreach und Kanäle

- Bringt der KI-personalisierte Opener mehr Antworten als ein generischer? Die Quelle empfiehlt den Test, nennt aber kein Ergebnis. [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- Gilt die Kanalreihenfolge (SMS vor E-Mail) auch außerhalb lokaler US-Makler, etwa im DACH-B2B mit anderen Regeln für SMS-Werbung? [Scale or Fail Ep. 1](../quellen/2026/11/2026-11-09-give-me-42-minutes-i-ll-show-you-how-to-sell-like-the-top-1.md)
- Welche Kennzahlen für LTV und CAC machen LinkedIn im Fall zum besten Kanal, und gilt das auch für Dienstleister im DACH-Raum, wo der Dialer-Schritt rechtlich kaum möglich ist? Die Quelle nennt keine Werte. [Scale or Fail Ep. 5](../quellen/2026/11/2026-11-14-how-to-get-rich-for-service-based-businesses-thank-me-later.md)
- Hält der Planwert von etwa 1.000 LinkedIn-Anfragen pro Neukunde auch für andere Fachberufe, für den DACH-Markt und nach der Frühphase, wenn das Produkt reifer ist? [Solve Intelligence](../quellen/2026/11/2026-11-14-solve-intelligence-millions-in-revenue-with-zero-salespeople.md)

### KI-Werkzeuge und Modelle

- Bestätigen unabhängige Tests die Reihenfolge der Halluzinationsraten? [Kimi K3.1 Pro Model Card](../quellen/2026/11/2026-11-09-moonshotai-kimi-k3-1-pro-model-card-auf-hugging-face.md)
- Wie genau trifft ein ICP-Score von 0 bis 100 aus automatischer Lead-Recherche die späteren Abschlüsse? [AgentRun](../quellen/2026/11/2026-11-13-show-hn-agentrun-open-source-self-improving-managed-agents.md)
- Hält der Ablauf vom Gesprächsprotokoll zum Angebot mit echten Kunden und unvollständigen Notizen, oder nur im vorbereiteten Testfall? [Kurs KI-Agenten](../quellen/2026/11/2026-11-13-building-ai-agents-that-actually-work-full-course.md)

### Pitch, Abschluss und Organisation

- Erhöht ein eigenes VSL vor jedem der beiden Verkaufsgespräche messbar die Abschlussquote? Die Quelle liefert keine Zahlen. Im Finale gehören drei VSLs zum Maßnahmenpaket eines B2B-Eventplaners, ihr Anteil am Ergebnis ist aber nicht getrennt. [$10M Service Business](../quellen/2026/11/2026-11-14-how-i-would-build-a-10m-service-business-if-i-had-to-start-o.md), [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- Lassen sich die B2C-Taktiken aus „Scale or Fail, Verkaufen“ (Pitch für Kalte, kurze Rückgabegarantie bei fehlendem Mitentscheider, Folgeangebote mitten in der Intensivphase) auf B2B mit Buying Committees übertragen? [Scale or Fail, Verkaufen](../quellen/2026/11/2026-11-13-if-you-hate-selling-please-watch-this-scale-or-fail.md)
- Was sind die vier Schritte des Menu Close, und welcher Anteil der genannten Run-Rate-Steigerung geht auf das Skript zurück? [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
- Welcher Hebel trug beim B2B-Eventplaner den Anstieg des Vertragswerts: Preismodul, Mehrjahresverträge oder die begleitenden Maßnahmen? [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)

### Verhandlung und Reziprozität

- Erhöht ein kleiner Gefallen vor dem Termin messbar Termin- oder Abschlussquoten? Tracy nennt keine Zahlen. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- Warum soll langsames Zustimmen später mehr Stärke geben, und ab welchem Tempo gefährdet es den Deal? Die Quelle erklärt es nicht. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- Mit welchem Wortlaut fordert man die Gegenleistung für ein Zugeständnis ein? Die Quelle liefert kein Skript. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md)
- Lässt sich der Grundsatz „Preis gegen Konditionen“ aus Käufersicht auf die Verkäuferseite übertragen, etwa höherer Listenpreis gegen längere Zahlungsziele? Der Fall des B2B-Eventplaners, der den Vertragswert unter anderem über Mehrjahresverträge steigerte, deutet in diese Richtung, trennt den Effekt aber nicht. [Tracy, Reziprozität](../quellen/2026/11/2026-11-09-using-the-law-of-reciprocity-and-other-persuasion-techniques.md), [Scale or Fail Finale](../quellen/2026/11/2026-11-14-8-entrepreneurs-compete-for-100-000-scale-or-fail-finale.md)
