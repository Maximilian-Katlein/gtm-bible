# Windows 11 erfasst, welche Coding-Agenten und Entwicklerwerkzeuge man nutzt

> **Quelle:** [Windows 11 Is Collecting Data on Which Coding Agents and Developer Tools You Use](https://xusheng.dev/posts/windows-coding-agent-telemetry/) · Xusheng Li (Blog xusheng.dev), Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50524736) mit 270 Punkten und 149 Kommentaren · Artikel mit Diskussion · 2026-11-17
> **Sprecher verkauft:** nichts, unabhängiger Reverse-Engineering-Blogpost · **Zielmarkt der Aussagen:** Entwickler und IT-Verantwortliche mit Windows 11, Datenschutz und Telemetrie · **Beweislage:** eigene Messungen in zwei ARM64-Testumgebungen, belegt bis zur lokalen Upload-Queue, nicht bis zum Empfang bei Microsoft

## Worum es geht
Der Beitrag beantwortet, warum die Windows-11-Systemkomponente MissionControlAggregator.dll eine Liste von Coding-Agenten und Entwicklerwerkzeugen enthält und was sie damit macht. Er zeigt Schritt für Schritt, wie die Komponente Agenten wie Claude, Codex, Copilot oder Cursor erkennt, das Ergebnis als Bitmap verdichtet und als optionale Diagnosedaten in die Upload-Queue von DiagTrack stellt. Relevant ist das für alle, die Entwicklerarbeitsplätze mit KI-Agenten unter Windows betreiben und Telemetrie im Griff behalten müssen.

## Was man anwenden kann
1. **Eigene Geräte prüfen, ob die Komponente läuft.** In einer administrativen PowerShell zeigen `Get-Service DiagTrack`, `Get-Process AggregatorHost` und `Get-CimInstance Win32_Process` die Prozesskette. `tasklist /m MissionControlAggregator.dll` zeigt, ob die DLL geladen ist. In der Testumgebung startete DiagTrack (Starttyp Automatic) den Kindprozess AggregatorHost.exe, der die DLL lädt.

2. **Optionale Diagnosedaten abschalten.** Beim Setup ablehnen oder später unter Einstellungen, Datenschutz und Sicherheit, Diagnose und Feedback den Schalter „Send optional diagnostic data“ deaktivieren. Der Report ist als optional markiert (`isRequired = false`). Laut Beitrag wird er dann nicht hochgeladen. Diesen Fall hat Li aber nicht selbst getestet. Für Firmenflotten heißt das: Der Wert `AllowTelemetry` sollte zentral geprüft werden, im getesteten US-Setup stand er nach Standardinstallation auf 3.

3. **Standardeinstellungen nicht vertrauen.** Bei einer sauberen Installation von Windows 11 Home ARM64 mit der offiziellen ISO, Region USA, war „Include Optional“ schon vor jeder Änderung aktiv. Wer Geräte ohne bewusstes Abwählen einrichtet, sendet optionale Diagnosedaten. Für EU-Regionen, Pro oder Enterprise ist das nicht geprüft.

4. **Wissen, was erkannt wird.** Vier CLI-Slots prüfen auf copilot.exe, claude.exe, codex.exe und agy.exe, in WSL ohne Endung .exe. Fünf Desktop-Slots prüfen auf github.exe, claude.exe, codex.exe, cursor.exe und antigravity.exe. Dazu kommen Werkzeuge wie node.exe, python.exe, dotnet.exe, gcc.exe, clang.exe, gdb.exe, javac.exe, devenv.exe und code.exe, verteilt auf zwölf Kategorien.

5. **Erkennung ist rein namensbasiert.** Eine nach codex.exe kopierte cmd.exe wurde als Codex gezählt, eine nach gcc.exe kopierte setzte die Compiler/Debugger-Kategorie. Bei Agenten genügt der Dateiname. Einige Werkzeug-Slots prüfen zusätzlich den Herausgeber (Node.js Foundation, Python Software Foundation, Microsoft Corporation), GCC und Clang nicht.

6. **Nicht nur WSL ist betroffen.** Die Komponente scannt keine Prozesse selbst, sondern hört auf bestehende Windows-Events: KernelProcess.AppStateChangeSummary und Win32kTraceLogging.AppInteractivitySummary für Windows-Programme, Microsoft.Windows.Lxss.Manager.Exec und ExecCritical für WSL. Ein normales Windows-codex.exe erreicht die CLI-Prüfung über den App-State-Pfad.

7. **Abfluss belegen statt vermuten.** Ein ETW-Event allein beweist keinen Upload, weil ETW auch lokal genutzt wird. Li prüfte deshalb, wer abonniert: `Get-EtwTraceProvider -SessionName Diagtrack-Listener` mit den GUIDs von KernelProcess und Microsoft.Windows.MissionControlAggregator. Beide waren in der Session Diagtrack-Listener eingetragen. Danach wurde die Upload-Queue (EventStore.db, Tabelle AsimovEvents, JSON-Batches dekomprimiert) inspiziert.

8. **Report für Analysen sofort auslösen.** Der Report folgt einer ungefähr täglichen Grenze. Li setzte den gespeicherten Fensterbeginn um 25 Stunden zurück und startete DiagTrack mit lauschendem Trace neu. Der Zustand liegt unter `C:\ProgramData\Microsoft\Diagnosis\AggregatorStorage\MissionControlAggregator$`. Nur in Testumgebungen sinnvoll.

9. **Methode übertragbar.** Ausgangspunkt war eine KI, die neue Windows-Binaries nach undokumentierten Funktionen durchsuchte und Referenzen verfolgte. Die Disassemblierung lief in Binary Ninja. Das Vorgehen eignet sich, um Telemetrie in Systemkomponenten gezielt zu finden.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 4 | CLI-Agent-Slots (copilot, claude, codex, agy) | eigene Daten, Disassemblierung |
| 5 | Desktop-Agent-Slots (github, claude, codex, cursor, antigravity) | eigene Daten |
| 12 | Kategorien von Entwicklerwerkzeugen | eigene Daten, Template `ReportCohorts<12,4,5>` |
| 62580080 | Feature-ID von CLICodingAgentUsage | eigene Daten |
| 26200.9974 | Windows-Build der Test-VM (Parallels, ARM64) | eigene Daten |
| 10.0.26100.9818 | Version der MissionControlAggregator.dll | eigene Daten |
| 0.1.5 | Version im gemessenen Report-Event | eigene Daten |
| 4 (= 1 << 2) | Wert CliAgentSubCohorts, Codex-CLI-Bit gesetzt | eigene Daten, Upload-Queue |
| 8 (= 1 << 3) | SubCohorts-Wert, Compiler/Debugger-Kategorie | eigene Daten, Upload-Queue |
| 3 | AllowTelemetry nach Standardinstallation, US-Region | eigene Daten, eine Installation |
| 25 Stunden | Zurückgesetzter Fensterbeginn zum Auslösen des Reports | eigene Daten |

## Wortlaute
- „Why would a Windows system DLL need a list of coding agents and developer tools?“ Die Ausgangsfrage der Untersuchung.
- „The name alone was enough for the component to recognize it as Codex.“ Steht für die rein namensbasierte Erkennung.
- „An ETW event by itself would not establish that anything leaves the machine.“ Steht für die Beweisregel: erst Abonnent und Upload-Queue prüfen.
- „the evidence does not support saying that it is active on every Windows installation.“ Die Einschränkung des Autors selbst.
- „Although I found no prompt text or source code in this report, collecting which agents and developer tools someone uses already has significant privacy implications.“ Die datenschutzrechtliche Einordnung.

## Grenzen und Widerspruch
- **Belegt bis zur Queue, nicht bis Microsoft.** Es gibt keinen Netzwerkmitschnitt und keinen Nachweis, dass der Report ankommt oder wie er verwendet wird. Ein Zweck der Erhebung wird nicht genannt.
- **Schmale Testbasis.** Eine Parallels-ARM64-VM und eine frische Home-ARM64-Installation in Region USA. EU, Pro, Enterprise, x64 und der Fall mit abgeschalteten optionalen Daten sind nicht gemessen.
- **Rollout unklar.** In der VM war CLICodingAgentUsage als Service Experiment aktiv, ohne manuelles Einschalten. Im ISO-Baseline-Image war es per Default aus. Wie verbreitet die Aktivierung ist, bleibt offen.
- **Umfang begrenzt.** Der Report enthält laut Analyse nur Bits pro Kategorie. Laufzeit, Fokuszeit und Interaktionszähler der Quell-Events scheinen verworfen zu werden. Prompt-Texte oder Quellcode wurden nicht gefunden. Das gilt nur für den Report Segments.SubCohorts, nicht für die gesamte Windows-Telemetrie.
- **Offene Zuordnung.** agy.exe und antigravity.exe werden keinem Hersteller zugeordnet. Die Aufteilung der zwölf Werkzeugkategorien nennt der Beitrag nicht.
- **Diskussion.** Niemand prüft oder widerlegt die technischen Aussagen. lesspassiveobse wendet ein, die Daten seien als Marktindikator verzerrt, weil Linux, macOS und Telemetrie-Verweigerer fehlen. j3th9n hält den Befund für erwartbar, onemoresoop vermutet weit mehr Datensammlung, beides ohne Beleg. Weitere Kommentare berichten anekdotisch von Wechseln zu Linux (vor allem mit Blick auf Gaming) oder vom Verbleib auf Windows 10 LTSC. Ob LTSC ähnliche Komponenten enthält, prüft niemand.
- **Kein GTM-Bezug.** Relevanz besteht für Datenschutz, digitale Souveränität und den Betrieb von KI-Entwicklerarbeitsplätzen, nicht für Vertrieb oder Marketing.
