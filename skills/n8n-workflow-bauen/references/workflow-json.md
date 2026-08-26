# Workflow-JSON: Struktur und Import

## Die JSON-Struktur

Ein n8n-Workflow ist ein JSON-Objekt mit Nodes und deren Verbindungen:

```json
{
  "name": "Rechnungen ablegen",
  "nodes": [
    {
      "id": "eindeutige-id-1",
      "name": "Mail-Eingang",
      "type": "n8n-nodes-base.gmailTrigger",
      "typeVersion": 1,
      "position": [250, 300],
      "parameters": {}
    },
    {
      "id": "eindeutige-id-2",
      "name": "In Drive ablegen",
      "type": "n8n-nodes-base.googleDrive",
      "typeVersion": 3,
      "position": [500, 300],
      "parameters": {}
    }
  ],
  "connections": {
    "Mail-Eingang": {
      "main": [[{ "node": "In Drive ablegen", "type": "main", "index": 0 }]]
    }
  },
  "settings": { "executionOrder": "v1" }
}
```

Regeln:

- `connections` verweist auf den **Anzeigenamen** des Nodes (`name`), nicht auf die `id`
- Jeder Node braucht `type` UND `typeVersion`. Bei Unsicherheit über die installierte Version eine verbreitete, stabile Version wählen und im Übergabetext erwähnen, dass n8n beim Import auf eine neuere Version aktualisieren kann
- `position` steuert nur die Anordnung auf der Leinwand: Nodes von links nach rechts mit ungefähr 250er-Abständen setzen, damit der Flow lesbar ist
- **Credentials nie ins JSON schreiben.** Nodes, die einen Login brauchen (Gmail, Sheets, Slack), bekommen ihre Zugangsdaten erst in n8n zugewiesen. Im Übergabetext auflisten, welche Nodes das betrifft

## Import-Anleitung für den Nutzer

So kommt die Datei in n8n (gilt für n8n Cloud und selbst gehostet):

1. In n8n oben rechts auf die drei Punkte klicken, dann **"Import from File"** wählen (je nach Version auch über "Workflows" → "Import").
2. Die JSON-Datei auswählen. Der Workflow erscheint auf der Leinwand.
3. Jeden rot markierten Node anklicken und die eigenen Zugangsdaten (Credentials) auswählen oder neu verbinden. n8n führt durch den Login.
4. Einmal auf **"Execute Workflow"** klicken und prüfen, ob jeder Node grün wird.
5. Wenn alles passt: den Schalter oben rechts auf **"Active"** stellen.

## Häufige Import-Stolpersteine

- **Node ist rot mit "Credentials not set"**: normal, Schritt 3 der Anleitung.
- **"Unknown node type"**: Der Node ist in dieser n8n-Version nicht installiert (Community-Node oder veraltet). Den Node im JSON gegen einen nativen tauschen oder den Nutzer den Community-Node installieren lassen.
- **Webhook-Trigger reagiert nicht**: Im Testmodus gilt die Test-URL ("Execute Workflow" gedrückt halten), im Aktiv-Modus die Produktions-URL. Beide stehen im Webhook-Node.
- **Expressions zeigen nichts an**: Erst wenn einmal Daten durch den Workflow gelaufen sind, kann n8n Felder anzeigen. Zuerst eine Testausführung machen.
