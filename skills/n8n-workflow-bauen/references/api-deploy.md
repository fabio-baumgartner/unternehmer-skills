# Deploy und Test über die n8n-API (Weg B)

Voraussetzung: `N8N_API_URL` und `N8N_API_KEY` liegen vor (aus `.env` im Arbeitsverzeichnis oder vom Nutzer genannt). Der API-Key wird in n8n unter Settings → API erzeugt.

## API-Endpunkte

| Aktion | Methode | Endpunkt |
|--------|---------|----------|
| Workflow anlegen | POST | `/api/v1/workflows` |
| Workflow aktualisieren | PUT | `/api/v1/workflows/{id}` |
| Aktivieren | POST | `/api/v1/workflows/{id}/activate` |
| Deaktivieren | POST | `/api/v1/workflows/{id}/deactivate` |
| Ausführungen listen | GET | `/api/v1/executions?limit=1` |
| Ausführung im Detail | GET | `/api/v1/executions/{id}?includeData=true` |
| Webhook auslösen | POST | `{N8N_API_URL}/webhook/{pfad}` |

Jeder Aufruf trägt den Header `X-N8N-API-KEY`. Beispiel:

```bash
curl -s "${N8N_API_URL}/api/v1/workflows" -H "X-N8N-API-KEY: ${N8N_API_KEY}"
```

Bei großen JSON-Bodies ein Heredoc verwenden, keine Zeilenfortsetzungen mit Backslash.

## Der Bau-Test-Zyklus

**Ein Node nach dem anderen. Nie zwei ungetestete Nodes stapeln.**

1. **Workflow mit Trigger anlegen** (POST). Die zurückgegebene Workflow-ID merken: Sie bleibt für den ganzen Bau dieselbe.
2. **Trigger testen**: aktivieren, auslösen (bei Webhook: die Webhook-URL aufrufen), letzte Ausführung prüfen.
3. **Nächsten Node ergänzen** (PUT mit dem kompletten aktualisierten Workflow), erneut auslösen, Ausführung prüfen:
   - Status `success` UND der neue Node taucht in den Ausführungsdaten auf → weiter
   - Fehler → Ursache im Fehlertext der Ausführung lesen, Node korrigieren, erneut testen. Nicht die Architektur vereinfachen, sondern den Fehler beheben
4. Wiederholen, bis alle Nodes stehen.
5. **Abschlusstest** mit einem realistischen Durchlauf, dann aktivieren.

Regeln:

- **Aktualisieren statt löschen.** Nie Workflows löschen oder deaktivieren, um Fehler "wegzuräumen". Eine Workflow-ID für den gesamten Bau.
- **Mit 2 Elementen testen**: datenholende Nodes (Sheets lesen, Mails holen) beim Bauen auf `limit=2` setzen, das spart Zeit und API-Kontingent. Vor der Übergabe das Limit entfernen oder auf den gewünschten Wert setzen.
- **Bei Datenbank- oder Tabellen-Nodes zuerst das Schema holen**: einen kurzen Testabruf machen, um die echten Feldnamen zu sehen, und exakt diese verwenden. Geratene Feldnamen sind die häufigste Fehlerquelle.
- **Nur die Workflows des Auftrags anfassen.** Fremde Workflows in der Instanz weder lesen noch ändern, außer der Nutzer bittet darum.
- **Credentials**: Die API kann Credentials nicht anlegen. Nodes, die Logins brauchen, im Bau als solche markieren und den Nutzer sie in der n8n-Oberfläche zuweisen lassen. Danach weitertesten.

## Abschlussbericht an den Nutzer

```
Workflow: [Name]
Link: [N8N_URL]/workflow/[id]
Status: aktiv

Getestet:
1. [Trigger]: funktioniert
2. [Node]: funktioniert ([Ergebnis])
3. ...

Noch zu tun:
- [Node X]: eigenes Konto in n8n verbinden (Node anklicken, Credential wählen)
```
