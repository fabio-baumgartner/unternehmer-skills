# Bau-Regeln: Node-Auswahl und Architektur

## Node-Auswahl: die Rangfolge

| Rang | Node-Typ | Wann |
|------|----------|------|
| 1 | Nativer Node | Es gibt einen eingebauten Node für die App (Gmail, Sheets, Slack, Notion, Airtable, ...). Immer zuerst |
| 2 | AI-Agent / Chat-Model-Node | Für JEDE KI-Aufgabe (Text zusammenfassen, klassifizieren, extrahieren) |
| 3 | Loop-Node (Split in Batches) | Wenn mehrere Elemente einzeln verarbeitet werden müssen |
| 4 | HTTP-Request-Node | Kein nativer Node vorhanden oder der native kann die eine benötigte Operation nicht |
| 5 | Code-Node | Nur für Logik, die anders nicht abbildbar ist |

Grundsatz: Was der Nutzer an Tools nennt, wird verwendet. Nie stillschweigend ersetzen ("Ich habe statt Airtable mal Sheets genommen" geht nicht).

## Architektur-Muster

- **Ein Workflow, eine Aufgabe.** Zwei unabhängige Abläufe werden zwei Workflows, nicht ein Monster.
- **Trigger-Wahl**: Zeitplan (Schedule) für regelmäßige Läufe, App-Trigger (z. B. Gmail Trigger) für "wenn etwas Neues ankommt", Webhook für Auslösung von außen, Form-Trigger für einfache Eingabemasken.
- **IF/Switch früh**: Verzweigungen so früh wie möglich, damit nicht jeder Zweig alles durchläuft.
- **Fehlerpfad**: Für produktive Workflows einen Error-Workflow oder wenigstens eine Benachrichtigung (Mail/Slack) bei Fehlschlag vorsehen. Den Nutzer fragen, wohin Fehlermeldungen gehen sollen.
- **Keine Endlosschleifen-Risiken**: Wenn ein Workflow in dieselbe App schreibt, die ihn triggert (z. B. Mail-Trigger + Mail-Versand), Filter einbauen, damit er sich nicht selbst auslöst.

## Typische Fehlerquellen

- **Webhook-Daten liegen unter `body`**: `{{ $json.body.feldname }}`, nicht `{{ $json.feldname }}`. Die häufigste Einzelfalle überhaupt.
- **Geratene Feldnamen**: Tabellen- und Datenbank-Nodes brauchen die exakten Spaltennamen. Erst Schema ansehen, dann bauen.
- **Expression vs. Code verwechselt**: In Node-Feldern gilt `{{ }}`-Syntax, im Code-Node reines JavaScript/Python ohne `{{ }}`.
- **Rückgabeformat im Code-Node**: JavaScript muss ein Array von Objekten mit `json`-Schlüssel zurückgeben (`return [{ json: {...} }]`), Python eine Liste (`return [{"json": {...}}]`). Alles andere bricht.
- **Leere Ergebnisse als Erfolg gewertet**: Ein grüner Node mit 0 Items ist oft ein Filter- oder Feldnamen-Fehler. Item-Anzahl prüfen, nicht nur die Farbe.
- **Zeitzonen bei Schedule-Triggern**: Die Instanz-Zeitzone prüfen, sonst läuft "täglich 7 Uhr" zur falschen Stunde.
