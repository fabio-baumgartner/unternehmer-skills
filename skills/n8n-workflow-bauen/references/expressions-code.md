# Spickzettel: Expressions und Code-Nodes

## Expressions (in Node-Feldern, mit `{{ }}`)

```javascript
// Feld aus dem vorherigen Node
{{ $json.feldname }}

// Webhook-Daten (liegen IMMER unter body)
{{ $json.body.feldname }}

// Feld aus einem bestimmten Node (Anzeigename!)
{{ $('Mail-Eingang').item.json.betreff }}

// Standardwert, falls leer
{{ $json.name ?? 'Unbekannt' }}

// Sicherer Zugriff auf Verschachteltes
{{ $json.kunde?.adresse?.ort }}

// Heutiges Datum
{{ $now.toFormat('yyyy-MM-dd') }}

// Datum rechnen (7 Tage zurück)
{{ $now.minus({ days: 7 }).toFormat('yyyy-MM-dd') }}

// Text zusammenbauen
{{ 'Rechnung ' + $json.nummer + ' von ' + $json.kunde }}
```

## Code-Node JavaScript (OHNE `{{ }}`)

```javascript
// Alle eingehenden Items
const items = $input.all();

// Nur das erste Item
const erste = $input.first().json;

// Daten aus einem anderen Node
const mail = $('Mail-Eingang').first().json;

// Beispiel: filtern und umformen
const ergebnis = items
  .filter(item => item.json.betrag > 100)
  .map(item => ({
    json: {
      kunde: item.json.kunde,
      betrag: item.json.betrag,
      geprüft: true
    }
  }));

// Rückgabe MUSS ein Array mit json-Schlüssel sein
return ergebnis;
```

## Code-Node Python

```python
# Alle eingehenden Items
items = _input.all()

# Erstes Item
erste = _input.first().json

# Beispiel: umformen
ergebnis = []
for item in items:
    ergebnis.append({
        "json": {
            "kunde": item.json["kunde"],
            "betrag": item.json["betrag"] * 1.19
        }
    })

# Rückgabe MUSS eine Liste mit json-Schlüssel sein
return ergebnis
```

## Die drei Regeln, die 80 % der Fehler verhindern

1. **Webhook-Daten liegen unter `body`.**
2. **In Feldern `{{ }}`, im Code-Node nicht.**
3. **Code-Nodes geben immer ein Array/eine Liste von `{ json: ... }`-Objekten zurück.**
