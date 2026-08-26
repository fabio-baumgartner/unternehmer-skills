---
name: lead-qualifizierung
description: Bewertet Leads gegen ein einmal definiertes Wunschkunden-Profil (ICP), wahlweise aus einer Datei (CSV, Excel) oder direkt aus dem verbundenen CRM (HubSpot, Pipedrive, Attio, Notion). Jeder Lead bekommt eine Bewertung mit Begruendung, bei CRM-Anbindung wird sie zurueckgeschrieben. Nutze diesen Skill, wenn der User sagt "Leads bewerten", "Leads qualifizieren", "welche Leads passen", "Leadliste filtern", "Leads priorisieren", "qualify leads", "score these leads", "filter my leads", "which leads match my ICP", "segment this list".
---

# Lead-Qualifizierung

Du bewertest Leads gegen das Wunschkunden-Profil des Nutzers. Ergebnis: eine sortierte Liste, in der jeder Lead eine Einstufung (heiß, warm, kalt, raus) und eine nachvollziehbare Begründung hat.

## Wann dieser Skill greift

Wenn eine Leadliste gefiltert, bewertet oder priorisiert werden soll, egal ob sie als Datei kommt oder im CRM liegt.

## Konnektoren

Prüfe beim Start, was verbunden ist:

- **CRM verbunden** (HubSpot, Pipedrive, Attio, eine Notion-Datenbank oder ähnliches): Leads direkt von dort ziehen und die Bewertung nach Freigabe zurückschreiben.
- **Kein CRM**: Der Datei-Workflow (CSV, Excel, JSON) ist ein vollwertiger Weg, keine Notlösung. In einem Satz erwähnen, dass ein verbundenes CRM das Zurückschreiben der Bewertungen ermöglichen würde, dann normal weiterarbeiten.
- **Web-Suche**: wichtig für die Recherche pro Lead. Ohne Web-Suche nur mit den vorhandenen Daten bewerten und das Ergebnis entsprechend als "Datenlage begrenzt" kennzeichnen.

## Wunschkunden-Profil beim ersten Lauf

Prüfe, ob im Ordner dieses Skills eine Datei `icp.md` existiert.

**Wenn ja:** Lies sie, fasse sie in zwei Sätzen zusammen und frag, ob sie noch stimmt.

**Wenn nein:** Definiere das Profil mit dem Nutzer. Frag konkret, nicht abstrakt:

1. Beschreib deinen besten bestehenden Kunden. Was macht ihn zum besten?
2. Harte Kriterien: Branche, Unternehmensgröße, Region, eingesetzte Software, Rolle des Ansprechpartners, Budgetrahmen. Was davon ist Pflicht, was ist nice-to-have?
3. Ausschlusskriterien: Was disqualifiziert sofort? (zu klein, falsche Branche, öffentlicher Sektor, was auch immer)
4. Bei Pflichtkriterien nachhaken: "Müssen ALLE erfüllt sein, oder reicht eines von mehreren?"

Wenn der Nutzer vage bleibt ("gute Firmen"), nachbohren: "Was genau macht eine Firma passend? Was müsste sie tun, damit du sie NICHT kontaktierst?"

Speichere das Ergebnis als `icp.md` im Ordner dieses Skills (Kriterien, Pflicht/Optional-Logik, Ausschlüsse). Beim nächsten Lauf nicht neu abfragen. Details zum Bewertungsraster: [references/bewertung.md](references/bewertung.md)

## Ablauf

### Schritt 1: Leads laden

**Aus Datei:** Datei einlesen und zurückmelden: Anzahl der Leads, vorhandene Spalten, 2 bis 3 Beispielzeilen. Fehlende Spalten für ein Pflichtkriterium sofort benennen, nicht raten. Duplikate melden, aber nicht ungefragt löschen.

**Aus dem CRM:** Mit dem Nutzer klären, welche Leads gemeint sind (alle offenen, eine bestimmte Liste oder Pipeline-Stufe, seit Datum X). Dann laden und dieselbe Übersicht zeigen.

### Schritt 2: Recherchieren und bewerten

**Wichtigste Regel: Nie allein auf die Listendaten verlassen.** Listen sind oft veraltet oder falsch. Mit Web-Suche pro Lead kurz prüfen: Website des Unternehmens plus mindestens eine unabhängige Quelle (Verzeichnis, LinkedIn-Unternehmensseite, Bewertungsportal, News).

Pro Lead festhalten:

- **Einstufung**: Heiß / Warm / Kalt / Raus (Raster in [references/bewertung.md](references/bewertung.md))
- **Begründung**: 1 bis 2 Sätze mit den ausschlaggebenden Fakten ("Erfüllt Branche und Größe, nutzt laut Website bereits Wettbewerber X")
- **Datenlücken**: was sich nicht verifizieren ließ

Im Zweifel eher aufnehmen als rauswerfen: Grenzfälle als Warm markieren und dem Nutzer die Entscheidung lassen.

**Bei großen Listen** (mehr als ungefähr 25 Leads): dem Nutzer vorab den Plan nennen (Anzahl, geschätzte Dauer) und die Liste in Blöcken abarbeiten, mit Zwischenstand nach jedem Block. Wenn die Umgebung parallele Unteraufgaben (Sub-Agents) unterstützt, Blöcke parallel bearbeiten, das verkürzt die Laufzeit deutlich.

### Schritt 3: Ergebnis liefern

**Immer:** eine sortierte Ergebnisliste im Chat (Heiß zuerst) plus, beim Datei-Workflow, eine aktualisierte Datei mit zwei neuen Spalten: `Bewertung` und `Begruendung`. Alle Originalspalten bleiben erhalten.

**Mit CRM:** die Bewertungen erst nach ausdrücklicher Freigabe des Nutzers zurückschreiben (als Feld, Tag oder Notiz, je nachdem, was das CRM hergibt). Vor dem Schreiben zeigen, was wohin geschrieben wird. Nie Leads löschen oder Pipeline-Stufen verschieben, nur die Bewertung ergänzen.

### Schritt 4: Nächste Schritte vorschlagen

Zum Abschluss: die 5 bis 10 heißesten Leads mit je einem Satz, warum sie oben stehen, und der Hinweis, womit der Nutzer anfangen sollte.

## Ausgabeformat

```
## Ergebnis: [X] Leads bewertet

| Lead | Firma | Bewertung | Begründung |
|------|-------|-----------|------------|
| ... | ... | Heiß | Erfüllt alle Pflichtkriterien, sucht laut Stellenanzeige gerade [Rolle] |

Heiß: X · Warm: X · Kalt: X · Raus: X
Datei: [Pfad] (mit Spalten "Bewertung" und "Begruendung")
```

## Wofür dieser Skill nicht da ist

- Neue Leads finden und Listen aufbauen (das ist Recherche, kein Qualifizieren; der Skill bewertet, was da ist)
- Kaltakquise-Nachrichten schreiben und versenden
- CRM-Aufräumaktionen (Duplikate zusammenführen, Felder migrieren)
