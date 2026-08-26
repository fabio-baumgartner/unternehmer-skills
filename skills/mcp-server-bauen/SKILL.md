---
name: mcp-server-bauen
description: Baut aus einer API-Dokumentation einen funktionierenden MCP-Server in Python oder TypeScript, damit Claude direkt mit einem externen Dienst arbeiten kann (CRM, Buchhaltung, eigenes System). Inklusive Installation in Claude Desktop oder Claude Code. Nutze diesen Skill, wenn der User sagt "bau mir einen MCP-Server", "verbinde Claude mit [Tool]", "MCP fuer [API]", "eigenen Konnektor bauen", "build an MCP server", "create MCP integration", "connect Claude to my API", "custom connector".
---

# MCP-Server bauen

Ein MCP-Server ist ein kleines Programm, das Claude mit einem externen Dienst verbindet: Danach kann Claude direkt in deinem CRM nachschlagen, Rechnungen in deiner Buchhaltungssoftware anlegen oder dein Branchentool bedienen, statt dass du Daten hin und her kopierst. Gebaut wird er einmal, danach steht der Dienst in jedem Chat als Werkzeug bereit.

Dieser Skill baut so einen Server aus einer API-Dokumentation: in TypeScript (empfohlen) oder Python.

## Wann dieser Skill greift

Wenn ein Dienst, den Claude nicht von Haus aus kennt, angebunden werden soll und dieser Dienst eine API hat. Typische Kandidaten: Branchensoftware, das eigene Backend, ein Tool ohne fertigen Konnektor.

## Konnektoren

Keine nötig. **Web-Suche oder URL-Abruf** hilft, um API-Dokumentation und die aktuellen MCP-SDK-Referenzen zu laden. Ohne: den Nutzer die API-Doku (oder Auszüge) einfügen lassen.

## Voraussetzungen klären (ehrlich, am Anfang)

Das ist der technischste Skill im Set. Der Nutzer braucht:

1. **Eine API des Zieldiensts** und Zugangsdaten dafür (API-Key oder Token). Ohne API kein MCP-Server; dann ist der Browser-Weg die Alternative.
2. **Node.js** (für TypeScript) oder **Python** installiert. Wenn nicht vorhanden: die Installation gehört zum Projekt, Anleitung in [references/installation.md](references/installation.md).

Beides in einer kurzen Frage klären, bevor es losgeht.

## Ablauf

### Schritt 1: Zieldienst und Umfang verstehen

1. Welcher Dienst, und was soll Claude damit können? Konkrete Aufgaben sammeln ("offene Rechnungen abfragen", "Kontakt anlegen"), daraus die nötigen API-Endpunkte ableiten.
2. API-Doku laden (URL abrufen oder einfügen lassen): Endpunkte, Authentifizierung, Datenmodelle.
3. Werkzeugliste vorschlagen: 3 bis 10 Tools, mit Namen und einem Satz Zweck. Lieber die API breit abdecken als nur einen Spezialfall. Der Nutzer bestätigt.

### Schritt 2: Sprache und Gerüst

- **TypeScript** empfohlen (bestes SDK, läuft überall). **Python** wenn der Nutzer es kennt oder wünscht.
- Aktuelle SDK-Dokumentation laden, wenn Abruf möglich (TypeScript: `https://raw.githubusercontent.com/modelcontextprotocol/typescript-sdk/main/README.md`, Python analog `python-sdk`). Sonst nach den Mustern in den Referenzen arbeiten: [references/typescript-server.md](references/typescript-server.md) oder [references/python-server.md](references/python-server.md).
- Transport: **stdio** für lokale Server (der Normalfall hier).

### Schritt 3: Implementieren

Qualitätsregeln, die den Unterschied machen:

- **Werkzeugnamen mit Präfix und Verb**: `lexoffice_rechnungen_auflisten`, nicht `getData`. Claude wählt Tools anhand der Namen und Beschreibungen
- **Beschreibungen für Claude schreiben**: jedes Tool und jeder Parameter in einem Satz, mit Beispielwert. Die Beschreibung liest später ein Modell, kein Mensch
- **Eingaben validieren** (Zod in TypeScript, Pydantic in Python) mit klaren Fehlermeldungen
- **Fehler hilfreich zurückgeben**: "Rechnung 123 nicht gefunden. Prüfe die Nummer oder liste offene Rechnungen mit [tool] auf" statt "Error 404"
- **Ergebnisse kompakt halten**: filtern und paginieren statt 5000 Zeilen zurückzugeben
- **API-Key aus einer Umgebungsvariable lesen, nie in den Code schreiben**
- Schreibende und löschende Tools als solche kennzeichnen (destructive-Hinweis) und nur bauen, wenn der Nutzer sie will

### Schritt 4: Testen

1. Kompilieren bzw. Syntax prüfen (`npm run build` / `python -m py_compile`).
2. Mit dem MCP Inspector testen (`npx @modelcontextprotocol/inspector`): jedes Tool einmal mit echten Daten aufrufen.
3. Mindestens einen Fehlerfall provozieren (falsche ID) und prüfen, dass die Fehlermeldung hilfreich ist.

### Schritt 5: Installieren

Anleitung aus [references/installation.md](references/installation.md), Schritt für Schritt für die Umgebung des Nutzers (Claude Desktop oder Claude Code). Danach ein gemeinsamer Live-Test: eine echte Frage stellen, die der neue Server beantworten muss.

## Ausgabeformat

Ein lauffähiges Projekt im Arbeitsverzeichnis (Ordner `mcp-[dienstname]/` mit Quellcode und README), die Installations-Schritte, und ein bestandener Live-Test.

## Wofür dieser Skill nicht da ist

- Dienste ohne API automatisieren (dafür: Browser-Automatisierung als eigene Aufgabe)
- Fertige MCP-Server konfigurieren, die es schon gibt (erst prüfen und sagen, ob ein offizieller oder Community-Server existiert: das spart den ganzen Bau)
- Öffentliches Hosting mit Nutzerverwaltung (hier geht es um lokale Server für den eigenen Einsatz)
