---
name: refresh
description: Erzeugt ein Übergabe-Dokument, mit dem man in einem frischen Chat nahtlos weiterarbeitet: Ziel der nächsten Sitzung, relevante Dateien als Verweis statt als Kopie, offene Entscheidungen, nächster Schritt. Drei Stufen: kurz, normal, ausführlich. Nutze diesen Skill, wenn der User sagt "refresh", "neuer Chat mit Kontext", "Übergabe erstellen", "der Chat wird zäh", "frischer Start", "mach einen Handoff", "fresh start", "hand off this session", "start a new chat with context", oder wenn eine lange Sitzung erkennbar schlechter wird.
---

# Refresh

Lange Chats ermüden: Das Fenster füllt sich mit altem Hin und Her, die Antworten werden schlechter. Refresh erzeugt ein Übergabe-Dokument für einen **frischen** Chat: das Ziel der nächsten Sitzung, die richtigen Dateien als Verweis, offene Entscheidungen, der nächste Schritt. Neu aufbauen statt zusammenfassen.

**Abgrenzung zu /compact:** `/compact` fasst den bisherigen Verlauf zusammen und macht im selben, vollgelaufenen Fenster weiter. Refresh macht das Gegenteil: Es nimmt nur mit, was die nächste Aufgabe braucht, und startet sauber. Wenn der Chat driftet oder zäh wird, ist Refresh die bessere Wahl.

## Wann dieser Skill greift

Am Ende einer Arbeitssitzung, vor einem Themenwechsel, oder wenn die Antwortqualität in einem langen Chat spürbar nachlässt.

## Konnektoren

Keine nötig.

## Die drei Stufen

Der Nutzer kann eine Stufe nennen ("refresh kurz"). Ohne Angabe gilt **normal**.

- **kurz**: der Spickzettel. Ziel, die nächsten 3 Schritte, offene Entscheidungen, nackte Dateipfade. Kein Durchsuchen der Sitzung.
- **normal** (Standard): das Übergabe-Dokument. Alles aus kurz, plus was erledigt ist, welche Entscheidungen getroffen wurden, und zu jeder Datei ein Halbsatz, warum sie zählt.
- **ausführlich**: das volle Briefing. Alles aus normal, plus Sackgassen, die die nächste Sitzung nicht wiederholen soll, Pfade zu Daten- und Protokolldateien, und welche Skills die nächste Sitzung starten sollte.

## Ablauf

### Schritt 1: Das Ziel erfragen

Genau eine Frage: "Was ist das Ziel deiner nächsten Sitzung?" Dann **warten**. Kein Dokument, kein Entwurf, bevor die Antwort da ist. Einzige Ausnahme: Das Ziel stand schon in der Anfrage, dann direkt weiter.

### Schritt 2: Klären, wohin die Übergabe geht

Eine Übergabe nützt nur, wenn ihr Leser die erwähnten Dateien öffnen kann.

- **Bleibt hier** (Standard): derselbe Nutzer, dieselbe Maschine, frischer Chat im selben Ordner. Lokale Pfade sind in Ordnung.
- **Reist**: geht an eine andere Person, eine andere Maschine oder per Mail. Dann sind lokale Pfade wertlos. Kleine wichtige Inhalte werden wörtlich eingebettet, für den Rest gemeinsame Quellen verlinkt (geteilter Ordner, Notion, URL). Im Zweifel einmal fragen: "Für dich hier, oder zum Weitergeben?"

### Schritt 3: Sammeln (normal und ausführlich)

Die laufende Sitzung durchgehen: Was wurde erledigt, was entschieden, welche Dateien wurden erstellt oder geändert, was blieb offen.

**Kritische Prüfung:** Für alles, was die nächste Sitzung braucht, fragen: Liegt das in einer Datei, die der frische Chat öffnen kann? Der frische Chat kann **diesen** Chat nicht lesen.

- Liegt es als Datei im Projektordner: als Pfad verweisen, nie den Inhalt kopieren.
- Existiert es nur in diesem Chat (ein finaler Text, eine Entscheidung, eine Zahlenliste): entweder jetzt als Datei speichern und verweisen, oder wörtlich in den Abschnitt "Mitgenommene Daten" einbetten.
- Nie auf temporäre Orte verweisen (Scratchpad, tmp-Ordner): die überleben die Sitzung nicht.

**Straffen:** Was die frische Sitzung sowieso automatisch lädt (CLAUDE.md, Projektkontext), nicht auflisten. Wenn im selben Ordner weitergearbeitet wird, auf den Ordner verweisen statt jede Datei aufzuzählen.

### Schritt 4: Schreiben und ausgeben

Das Dokument als `refresh-[ziel-kurz].md` im Projektordner speichern (Dateiname ohne Umlaute) **und komplett im Chat ausgeben**, denn der Chat-Text ist das, was der Nutzer in die frische Sitzung einfügt.

## Ausgabeformat

Genau diese Form, nicht zutreffende Abschnitte weglassen:

```
# Sitzungs-Übergabe: [Ziel]

Weiterarbeit in [Projekt / Arbeitsverzeichnis]. Ziel dieser Sitzung: [Ziel]

## Wo die Dinge stehen          (normal + ausführlich)
[Erledigtes, getroffene Entscheidungen]

## Nächste Schritte
1. ...

## Dateien öffnen (lesen, nicht neu herleiten)
- [Pfad]: [warum sie zählt]

## Mitgenommene Daten            (nur was nirgendwo sonst liegt)
[wörtlich eingebettete Inhalte]

## Nicht wiederholen             (nur ausführlich)
- [Sackgasse / verworfener Ansatz]

## Skills starten                (nur ausführlich)
- [Skill und wofür]
```

Danach ein Satz: "In einen frischen Chat einfügen und weiterarbeiten." (Beim Weitergeben: was genau mitzuschicken ist.)

## Wofür dieser Skill nicht da ist

- Zusammenfassen im selben Chat (das ist `/compact`)
- Dauerhafte Notizen und Wissensablage (dafür das Kontext-System oder eigene Notizen; die Übergabe ist ein Einweg-Dokument für die nächste Sitzung)
