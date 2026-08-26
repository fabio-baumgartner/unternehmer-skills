# Installation: den fertigen Server mit Claude verbinden

Diese Schritte muss jemand ohne Vorwissen befolgen können. Beim Erklären die konkreten Pfade und Namen des gebauten Servers einsetzen, keine Platzhalter stehen lassen.

## Voraussetzungen nachinstallieren (falls nötig)

- **Node.js** (für TypeScript-Server): von nodejs.org die LTS-Version laden und mit den Standardeinstellungen installieren. Prüfen: Terminal öffnen, `node --version` eingeben, eine Versionsnummer muss erscheinen.
- **Python** (für Python-Server): von python.org laden, bei der Installation das Häkchen "Add to PATH" setzen. Prüfen: `python --version`.

## Claude Desktop

1. Die Konfigurationsdatei öffnen:
   - **Windows**: `%APPDATA%\Claude\claude_desktop_config.json` (Win + R, den Pfad einfügen, Enter)
   - **Mac**: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Wenn die Datei nicht existiert: in Claude Desktop unter Einstellungen → Entwickler → "Konfiguration bearbeiten" anlegen lassen.
2. Den Server eintragen (bestehende Einträge stehen lassen, nur den neuen Block in `mcpServers` ergänzen):

**TypeScript-Server:**
```json
{
  "mcpServers": {
    "dienstname": {
      "command": "node",
      "args": ["C:\\pfad\\zum\\projekt\\mcp-dienstname\\dist\\index.js"],
      "env": { "DIENST_API_KEY": "hier-den-api-key-einsetzen" }
    }
  }
}
```

**Python-Server:**
```json
{
  "mcpServers": {
    "dienstname": {
      "command": "python",
      "args": ["C:\\pfad\\zum\\projekt\\mcp-dienstname\\server.py"],
      "env": { "DIENST_API_KEY": "hier-den-api-key-einsetzen" }
    }
  }
}
```

3. **Windows-Pfade brauchen doppelte Backslashes** (`\\`) in der JSON-Datei.
4. Claude Desktop komplett beenden und neu starten (auch aus dem System-Tray beenden).
5. Prüfen: In den Einstellungen unter Konnektoren/MCP muss der Server erscheinen. Dann eine Testfrage stellen, die nur der neue Server beantworten kann ("Liste meine offenen Rechnungen aus [Dienst]").

## Claude Code

Im Projektordner (oder mit `--scope user` für überall):

```bash
claude mcp add dienstname --env DIENST_API_KEY=hier-den-key -- node /pfad/zu/dist/index.js
```

bzw. für Python:

```bash
claude mcp add dienstname --env DIENST_API_KEY=hier-den-key -- python /pfad/zu/server.py
```

Prüfen mit `claude mcp list`, dann eine neue Sitzung starten und die Testfrage stellen.

## Häufige Probleme

| Symptom | Ursache und Lösung |
|---------|--------------------|
| Server taucht nicht auf | JSON-Syntaxfehler in der Config (fehlendes Komma, einfacher Backslash). Datei mit einem JSON-Prüfer kontrollieren |
| "command not found" | Node/Python nicht im PATH. Vollen Pfad zur node.exe/python.exe als `command` eintragen |
| Server startet, Tools schlagen fehl | API-Key falsch oder fehlt im `env`-Block. Key direkt testen (kurzer API-Aufruf) |
| Ging gestern, heute nicht | Dienst-API geändert oder Key abgelaufen. Fehlermeldung des Tools lesen, sie wurde extra hilfreich gebaut |

## Sicherheit

- Der API-Key steht in der Config-Datei im Klartext. Die Datei nicht teilen, nicht in Screenshots zeigen, nicht in Git einchecken.
- Nur die Rechte vergeben, die gebraucht werden: Wenn der Dienst API-Keys mit Leserechten anbietet und Claude nur lesen soll, den Lese-Key verwenden.
