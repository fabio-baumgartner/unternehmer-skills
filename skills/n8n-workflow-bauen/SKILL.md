---
name: n8n-workflow-bauen
description: Baut n8n-Workflows aus einer Beschreibung: wahlweise als fertiges JSON zum Importieren (ohne API-Key) oder direkt deployt und getestet über die n8n-API. Hilft auch bei einzelnen Nodes, Expressions und Code-Nodes. Nutze diesen Skill, wenn der User sagt "bau mir einen n8n-Workflow", "n8n Automatisierung", "Workflow erstellen", "warum funktioniert mein n8n-Flow nicht", "n8n Expression", "create n8n workflow", "build automation in n8n", "deploy to n8n", "n8n node help".
---

# n8n-Workflow bauen

n8n ist ein Werkzeug, mit dem man Apps ohne Programmieren verbinden kann: "Wenn eine Mail mit Rechnung ankommt, lege sie in Google Drive ab und trage sie in eine Tabelle ein." Dieser Skill baut solche Workflows aus einer einfachen Beschreibung.

Zwei Wege, je nachdem, was der Nutzer hat:

- **Weg A: JSON zum Importieren.** Kein API-Key nötig. Der Skill baut den Workflow als Datei, der Nutzer importiert sie in n8n mit zwei Klicks. Der Standardweg für Einsteiger.
- **Weg B: Direkt deployen.** Mit n8n-API-Key baut und testet der Skill den Workflow direkt in der n8n-Instanz, Node für Node.

## Wann dieser Skill greift

Wenn ein wiederkehrender Ablauf automatisiert werden soll und n8n das Werkzeug ist (oder werden soll). Auch für Fragen zu einzelnen Nodes, Expressions und Code-Nodes.

## Konnektoren

- **n8n-API-Key** (optional): ermöglicht Weg B. Beim Start prüfen: Liegt im Arbeitsverzeichnis eine `.env` mit `N8N_API_URL` und `N8N_API_KEY`, oder nennt der Nutzer beides? Wenn nicht: in einem Satz erwähnen, dass mit API-Key direkt deployt und getestet werden könnte, und mit Weg A weiterarbeiten.

## Ablauf

### Schritt 1: Den Ablauf verstehen

Bevor irgendetwas gebaut wird, den Ablauf in Alltagssprache festnageln:

1. **Auslöser**: Was startet den Workflow? (Zeitplan, eingehende Mail, Formular, Webhook)
2. **Schritte**: Was passiert dann, der Reihe nach? Welche Apps sind beteiligt?
3. **Daten**: Welche Information fließt von Schritt zu Schritt?
4. **Fehlerfall**: Was soll passieren, wenn ein Schritt scheitert?

Den verstandenen Ablauf als nummerierte Liste zurückspiegeln und bestätigen lassen. Wenn der Nutzer Tools nennt (z. B. "mit Google Sheets"), genau diese verwenden, nie stillschweigend ersetzen.

### Schritt 2: Bauen

Regeln für beide Wege (Details: [references/bau-regeln.md](references/bau-regeln.md)):

- Native n8n-Nodes vor HTTP-Request vor Code-Node. Code nur, wo Logik es wirklich braucht
- Für KI-Aufgaben den AI-Agent- oder Chat-Model-Node verwenden
- Keine Platzhalter-Daten ("REPLACE_ME"): Wo eine echte Angabe fehlt (Tabellen-ID, Kanalname), den Nutzer fragen oder die Stelle klar als "in n8n auswählen" markieren
- Sinnvolle Node-Namen ("Rechnung erkennen" statt "IF 1")

**Weg A (JSON):** Den kompletten Workflow als eine JSON-Datei ins Arbeitsverzeichnis schreiben (`workflow-[name].json`, ohne Umlaute im Dateinamen), nach dem Strukturmuster in [references/workflow-json.md](references/workflow-json.md). Danach die Import-Anleitung geben (drei Schritte, steht in derselben Referenz) und erklären, welche Zugangsdaten (Credentials) der Nutzer in n8n noch anklicken muss: Credentials wandern nie ins JSON.

**Weg B (API):** Nach dem Prozess in [references/api-deploy.md](references/api-deploy.md): Workflow mit Trigger anlegen, dann **einen Node nach dem anderen** hinzufügen und nach jedem Node testen (Ausführung prüfen, erst bei Erfolg weiter). Nie mehrere ungetestete Nodes stapeln. Bei Fehlern die Ursache beheben, nicht auf eine "einfachere" Architektur ausweichen. Workflows aktualisieren statt löschen und neu anlegen. Beim Testen datenholende Nodes auf 2 Elemente begrenzen. Nur an Workflows arbeiten, die der Nutzer genannt hat.

### Schritt 3: Übergeben

Am Ende bekommt der Nutzer:

- Weg A: die JSON-Datei, die Import-Anleitung, die Liste der noch zu verbindenden Credentials, und einen Testvorschlag ("Führ den Workflow einmal manuell mit einer Test-Mail aus")
- Weg B: den Workflow-Link, den Status (aktiv/inaktiv), was getestet wurde, und was noch manuell zu tun ist

Plus in beiden Fällen zwei Sätze, was der Workflow tut, so dass der Nutzer es einem Kollegen erklären könnte.

## Hilfe bei Nodes, Expressions und Code

Auch ohne Workflow-Auftrag hilft der Skill bei Einzelfragen. Spickzettel in [references/expressions-code.md](references/expressions-code.md):

- Expressions (`{{ $json.feld }}`), Zugriff auf andere Nodes, Datumsformate
- Die Webhook-Falle: eingehende Daten liegen unter `$json.body`, nicht direkt unter `$json`
- Code-Nodes in JavaScript und Python, mit den Rückgabe-Regeln

## Wofür dieser Skill nicht da ist

- Die Entscheidung, OB n8n das richtige Werkzeug ist, gehört an den Anfang: Für einmalige Aufgaben oder reine Text-Arbeit ist Claude selbst schneller, für starre Wenn-dann-Abläufe zwischen Apps ist n8n ideal. Das ehrlich sagen
- n8n-Hosting und Server-Betrieb (auf n8n-Cloud oder die offizielle Doku verweisen)
- Zapier- und Make-Workflows (die Logik ist übertragbar, das JSON nicht)
