# agent-browser CLI: Befehlsreferenz

Gilt für Weg 2 (das CLI-Werkzeug agent-browser). Die eingebauten Browser-Werkzeuge von Claude Desktop und Claude in Chrome haben eigene Funktionen und brauchen diese Referenz nicht.

## Das Kernmuster

```bash
# 1. Seite öffnen
agent-browser open https://beispiel.de/formular

# 2. Struktur erfassen: liefert Element-Referenzen wie @e1, @e2
agent-browser snapshot -i

# 3. Mit den Referenzen arbeiten
agent-browser fill @e1 "max@beispiel.de"
agent-browser fill @e2 "Mustermann GmbH"
agent-browser click @e3

# 4. Nach Navigation oder Seitenänderung: neu erfassen
agent-browser snapshot -i
```

**Wichtigste Regel: Nach jedem Seitenwechsel `snapshot -i` neu ausführen.** Alte @-Referenzen zeigen sonst auf Elemente, die es nicht mehr gibt.

## Mehrere Befehle bündeln

Für 2+ aufeinanderfolgende Befehle immer `batch` verwenden:

```bash
agent-browser batch "open https://beispiel.de" "snapshot -i"
agent-browser batch "click @e5" "wait 1000" "screenshot"
```

Getrennt ausführen nur, wenn die Ausgabe eines Befehls erst gelesen werden muss (z. B. Snapshot lesen, dann gezielt klicken).

## Befehle nach Aufgabe

### Navigation und Erfassen

```bash
agent-browser open <url>              # Seite öffnen
agent-browser snapshot -i             # interaktive Elemente mit @refs
agent-browser snapshot -i --urls      # zusätzlich Link-Ziele anzeigen
agent-browser get url                 # aktuelle URL
agent-browser get title               # Seitentitel
agent-browser get text @e1            # Text eines Elements
agent-browser close                   # Browser schließen
```

### Interaktion

```bash
agent-browser click @e1               # klicken
agent-browser fill @e2 "text"         # Feld leeren und ausfüllen
agent-browser type @e2 "text"         # tippen ohne zu leeren
agent-browser select @e1 "Option"     # Dropdown wählen
agent-browser check @e1               # Checkbox setzen
agent-browser press Enter             # Taste drücken
agent-browser scroll down 500         # scrollen
```

### Warten (gegen zu frühe Klicks)

```bash
agent-browser wait @e1                # bis Element erscheint
agent-browser wait 2000               # Millisekunden
agent-browser wait --text "Erfolgreich gespeichert"   # bis Text erscheint
agent-browser wait --url "**/danke"   # bis URL-Muster erreicht
agent-browser wait "#spinner" --state hidden          # bis Ladekreis weg ist
```

### Erfassen und Sichern

```bash
agent-browser screenshot              # Screenshot
agent-browser screenshot --full       # ganze Seite
agent-browser pdf seite.pdf           # Seite als PDF
agent-browser download @e1 ./datei.pdf   # Download per Klick auslösen
```

### Tabs

```bash
agent-browser tab list                # offene Tabs
agent-browser tab new <url>           # neuen Tab öffnen
agent-browser tab 2                   # zu Tab 2 wechseln (Zählung ab 0)
agent-browser tab close               # aktuellen Tab schließen
```

### Dialoge

Alert-Dialoge werden automatisch bestätigt. Bestätigungs- und Eingabe-Dialoge brauchen explizite Behandlung:

```bash
agent-browser dialog status           # ist ein Dialog offen?
agent-browser dialog accept           # bestätigen
agent-browser dialog accept "Eingabe" # Eingabe-Dialog mit Text bestätigen
agent-browser dialog dismiss          # abbrechen
```

## Muster: Daten aus einer Liste ziehen

```bash
agent-browser open https://alt-system.de/kunden
agent-browser snapshot -i                    # Struktur ansehen
agent-browser get text @e7                   # Tabelleninhalt lesen
# Bei mehreren Seiten: "Weiter"-Element klicken, warten, erneut lesen
agent-browser click @e12
agent-browser wait --text "Seite 2"
agent-browser snapshot -i
```

Die gelesenen Daten strukturiert sammeln und am Ende als Tabelle oder CSV übergeben.

## Muster: Formular sicher absenden

```bash
# Alles ausfüllen, Screenshot als Kontrolle, DANN den Nutzer fragen
agent-browser batch "fill @e1 'Wert 1'" "fill @e2 'Wert 2'" "screenshot"
# → Screenshot dem Nutzer zeigen: "So ist es ausgefüllt. Absenden?"
# Erst nach Freigabe:
agent-browser click @e9
agent-browser wait --text "Vielen Dank"
```

## Fehlerbilder

| Symptom | Ursache und Lösung |
|---------|--------------------|
| Klick trifft nichts / "ref not found" | Seite hat sich geändert, Snapshot veraltet → `snapshot -i` neu |
| Feld bleibt leer trotz fill | Feld ist ein Sonder-Widget → `click` aufs Feld, dann `keyboard type "text"` |
| Seite lädt ewig | Mit `wait --text` auf ein konkretes Element warten statt auf Netzwerkruhe |
| Element nicht im Snapshot | Es liegt außerhalb des sichtbaren Bereichs → erst scrollen, dann neu erfassen |
