# Coding-Agenten betreiben, ohne ihnen die eigenen Zugangsdaten zu geben

> **Quelle:** [Running coding agents without handing them my credentials](https://blog.antonio.cx/running-agents-with-lend) · Antonio (antoniomika), blog.antonio.cx, pico.sh · Artikel mit Diskussion auf [Hacker News](https://news.ycombinator.com/item?id=50526152) (129 Punkte) · 2026-11-18
> **Sprecher verkauft:** Kein direkter Verkauf. Der Autor hat das vorgestellte Tool lend selbst gebaut, und die Agenten-VMs laufen bei picd, dem Hosting-Dienst von pico.sh. · **Zielmarkt der Aussagen:** Entwickler, die Coding-Agenten wie Claude Code oder Codex auf Wegwerf-VMs betreiben · **Beweislage:** Selbstbeschreibung des Tool-Autors, keine Tests oder Red-Team-Ergebnisse.

## Worum es geht
Wie lässt man Coding-Agenten auf entfernten VMs mit GitHub, Cloud-CLIs und SSH-Keys arbeiten, ohne die Tokens auf die VM zu kopieren? Die Antwort des Autors ist lend: ein Proxy vor dem lokalen SSH-Agenten, der Kommandos auf dem Laptop ausführt und jede Anfrage gegen eine lokale Policy plus Touch-ID-Freigabe prüft. Relevant für Teams, die mehrere Agenten parallel laufen lassen und ihre Zugangsdaten auf einer vertrauenswürdigen Maschine halten wollen.

## Was man anwenden kann
1. **Agenten auf Wegwerf-VMs, Zugangsdaten auf dem Laptop.** Der Autor lässt Claude Code in einem Repo arbeiten und Codex als Reviewer in einem anderen, dazu eine Langläufer-Aufgabe. Alle laufen auf VMs mit eigener Docker-Engine. SSH-Keys, 1Password-Vault und eingeloggte gh- und Cloud-CLIs bleiben auf dem Laptop. Gilt als eigener Workflow des Autors, der zugleich beim Hosting-Anbieter arbeitet.
2. **Zwei verbreitete Muster vermeiden.** Ein Token in `~/.config/gh/hosts.yml` auf der VM ist für jeden Prozess lesbar, auch für alles, was der Agent startet. `ssh -A` hält die privaten Schlüssel zwar lokal, erlaubt der VM aber jede Signatur ohne Nachfrage und ohne Protokoll. Außerdem deckt `ssh -A` keine API-Tokens oder CLI-Logins ab.
3. **Policy mit Default-Deny auf dem Laptop.** Die JSON-Policy setzt `"default": "deny"` und erlaubt nur gelistete Kommandos per absolutem Pfad, etwa `/opt/homebrew/bin/gh`, mit Freigabemodus `biometric:inline`. SSH-Keys werden per Fingerprint freigegeben. Nicht gelistete Keys sind für die VM unsichtbar.
4. **Regeln eng schneiden.** `args_prefix` wie `["pr", "view"]` erlaubt nur bestimmte Subkommandos. `max_signatures` begrenzt Signaturen pro Key und Session. Leases (z. B. fünf Minuten oder drei Nutzungen) gelten nur für exakt das freigegebene Kommando mit exakten Argumenten und enden mit der Session oder beim Bildschirmsperren.
5. **Anbindung an Claude Code per MCP.** `lend mcp` stellt ein einziges Tool `run_local_command` bereit. Pflichtparameter sind Kommando und Begründung. Ohne MCP geht es per CLI: `lend exec --reason "..." -- gh repo view ...`. Verbunden wird vom Laptop mit `lend ssh --config ./policy.json -- agent-vm`, der Proxy lebt nur für diese Verbindung.
6. **Secrets injizieren statt übergeben.** Eine Kommandoregel kann über `secret_reader` (z. B. 1Password CLI `op read --no-newline`) ein Secret als Umgebungsvariable an das lokale Kommando hängen, etwa `GH_TOKEN` für `gh pr view`. Die VM kann weder Variablen noch Referenzen wählen. Im Demo verlangt 1Password zusätzlich eine eigene Touch-ID. Bedingung: 1Password CLI auf dem Laptop.
7. **Agenten-eigene Rückfragen zentral freigeben.** `lend approve --hook claude-code` als PermissionRequest-Hook leitet Permission-Fragen der Agenten an denselben Mac-Dialog weiter, ohne etwas auf dem Laptop auszuführen. Adapter gibt es laut Autor für Codex, Antigravity und pi. Ist der Laptop nicht erreichbar, fragt der Agent in der eigenen UI. In Skripten: `lend approve --topic deploy ... && terraform apply`.
8. **Stabilen Socket für persistente Sessions bauen.** Nach einem SSH-Reconnect ändert sich der Socket-Pfad, laufende Agenten in herdr oder tmux behalten den alten `SSH_AUTH_SOCK` und scheitern. Lösung des Autors: Symlink an festem Pfad (`~/.ssh/lend/agent.sock`), den `~/.ssh/rc` bei jedem Login nach Prüfung mit `lend doctor --remote` aktualisiert. Absoluter Pfad zu lend nötig, weil `~/.ssh/rc` vor der PATH-Ergänzung läuft. Bereits laufende Agenten einmal neu starten.
9. **Beobachten und notbremsen.** `lend status --all --watch` zeigt Verbindungen, Anfragen und Leases. `lend pause --all` bricht alles ab und lehnt Neues ab. `lend history` protokolliert standardmäßig ohne Argumente, Ausgaben und Secrets.
10. **Agenten orchestrieren und mobil beantworten.** herdr ist ein Terminal-Multiplexer, der pro Pane anzeigt, ob ein Agent arbeitet, wartet oder fertig ist. Agenten können einander starten, prompten und Ergebnisse lesen. Der Client Ovis zeigt Rückfragen als Karten auf dem Telefon, Erreichbarkeit über Tailscale vorausgesetzt.

## Zahlen und ihre Herkunft
| Zahl | Worauf sie sich bezieht | Beleg |
|---|---|---|
| 129 | Punkte der HN-Diskussion | Plattformangabe |
| 5 Minuten / 3 Nutzungen | Beispielwerte für Leases in lend | Herstellerangabe |
| Zig Milliarden Tokens, über 100.000 PowerShell-Aufrufe | bob1029s Nutzung von GPT mit erhöhten Rechten ohne bösartigen Vorfall | Anekdote eines Kommentators |

## Wortlaute
- „herdr agent prompt reviewer "Review the diff on am/fix-retries" --wait --until done“: Ein Agent beauftragt einen Codex-Reviewer und wartet auf das Ergebnis.
- „The policy lives on the laptop and lists what the VM is allowed to ask for. Everything else is denied.“: Das Grundprinzip der Default-Deny-Policy.
- „The reason and caller details come from the VM, so they're marked as unverified.“: Die Vertrauensgrenze im Freigabedialog.
- „lend approve --topic deploy --title "terraform apply" && terraform apply“: Menschliche Freigabe als Gate vor einer Infrastrukturänderung.

## Grenzen und Widerspruch
- **Kein Sandboxing.** Ein freigegebenes Kommando läuft mit den Rechten des Nutzers. Wer eine Shell, einen Interpreter oder ein stdin-lesendes Programm freigibt, erlaubt praktisch beliebige Ausführung, weil stdin im Prompt nicht angezeigt wird. Wer `env`, `sh` oder `op` selbst freigibt, gibt injizierte Secrets direkt zurück.
- **Fälschbare Angaben, offener Socket.** Begründung und Aufruferdaten kommen von der VM. Jeder, der den weitergeleiteten Socket erreicht, Root eingeschlossen, kann während der Session Anfragen stellen. Die Policy und die Freigabe bleiben die einzige Grenze.
- **Reifegrad.** Laut Autor früh, nur macOS und Linux, kein PTY, also keine interaktiven Programme. Biometrische Freigabe nur auf macOS, auf Linux Zenity-Dialog oder Terminal. Die SSH-Verbindung muss offen bleiben. Bei mehreren Verbindungen gewinnt die letzte Symlink-Aktualisierung.
- **Fähigkeit statt Credential.** saagarjha und recroad wenden ein, dass der Agent das Secret zwar nicht sieht, aber alles tun kann, was es erlaubt. Der Dialog sei Zeremonie ohne Grundlage für eine informierte Entscheidung. Zur Freigabemüdigkeit bei vielen Touch-ID-Prompts sagt der Artikel nichts.
- **Kein Wirksamkeitstest.** scotty79 schlägt vor, Agenten gezielt aufzufordern, die Credentials trotzdem zu beschaffen. Ein solcher Test fehlt.
- **Alternativen aus der Diskussion, ungeprüft:** Docker Sandboxes (`sbx secret set`), Nono und Smolvm für HTTP-Secret-Injektion (laut LeBit auf Tailscale-Knoten umgangen), fnox mit YubiKey-Touch, keepassxc-cli, pass (nur lokal), ein unprivilegierter Unix-User statt VM (knocte, Tool skynot). Traubenfuchs verlässt sich auf eine Prompt-Anweisung zur Bestätigung schreibender Aktionen, das ist keine technische Durchsetzung.
- **Lücken im Material.** Der Artikel bricht bei „Prior art“ ab. Lizenz, Version und Installationsweg von lend fehlen. Von der Diskussion lagen nur die ersten Kommentare vor.
