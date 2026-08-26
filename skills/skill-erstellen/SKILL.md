---
name: skill-erstellen
description: Baut aus einem Chatverlauf, einer Beschreibung oder einem SOP einen vollstaendigen Claude Skill: Ordner, SKILL.md mit Frontmatter und guten Triggern, references bei Bedarf. Verbessert auch bestehende Skills und erklaert die Installation. Nutze diesen Skill, wenn der User sagt "mach daraus einen Skill", "Skill erstellen", "bau mir einen Skill", "das will ich als Skill", "verbessere meinen Skill", "warum triggert mein Skill nicht", "create a skill", "build a skill", "turn this into a skill", "improve my skill".
---

# Skill erstellen

Du baust Claude Skills: wiederverwendbare Anleitungen, die Claude automatisch lädt, wenn eine passende Aufgabe kommt. Ein Skill ist ein Ordner mit einer `SKILL.md` (Pflicht) und optionalen `references/`-Dateien. Aus einem guten Chatverlauf, einer Beschreibung oder einem SOP wird so ein Ablauf, der beim nächsten Mal auf Zuruf funktioniert.

## Wann dieser Skill greift

- Ein Arbeitsablauf hat im Chat gut funktioniert und soll wiederholbar werden
- Ein SOP oder eine Prozessbeschreibung soll als Skill ausführbar werden
- Ein bestehender Skill soll besser werden (triggert nicht, zu vage, zu aufgebläht)

## Konnektoren

Keine nötig.

## Ablauf: neuen Skill bauen

### Schritt 1: Quelle und Ziel klären

Je nach Ausgangslage:

- **Chatverlauf**: Der beste Fall. Fragen: "Welcher Teil dieses Chats soll zum Skill werden, und was war am Ergebnis gut?" Aus dem Verlauf den tatsächlichen Ablauf extrahieren: was der Nutzer lieferte, welche Schritte zur guten Ausgabe führten, welche Korrekturen unterwegs kamen (die Korrekturen sind Gold: sie werden zu Regeln im Skill).
- **Beschreibung**: Wenn nur eine Idee da ist ("ein Skill, der meine Wochenberichte schreibt"), die Kernfragen klären: Was ist der Input? Was ist der Output, und wie sieht ein gutes Ergebnis konkret aus? Welche Schritte liegen dazwischen? Was entscheidet der Nutzer, was entscheidet Claude? Bei komplexen Abläufen mit vielen Unklarheiten empfehlen, vorher ein gründliches Prozess-Interview zu machen.
- **SOP**: Die Schritte in Anweisungen an Claude übersetzen: was Claude tut, was es fragt, woran es erkennt, dass ein Schritt fertig ist.

### Schritt 2: Skill-Namen festlegen

Kurz, kleingeschrieben, mit Bindestrichen, ohne Umlaute: `wochenbericht-schreiben`, nicht `Wöchentlicher Bericht`. Der Name beschreibt die Aufgabe, nicht das Werkzeug.

### Schritt 3: Die description schreiben (der wichtigste Teil)

Die `description` im Frontmatter entscheidet, ob der Skill automatisch lädt. Claude sieht bei der Auswahl nur Name und description, nicht den Skill-Inhalt. Regeln:

1. **Erst was, dann wann**: ein bis zwei Sätze, was der Skill tut, dann die Trigger-Phrasen.
2. **Trigger-Phrasen wörtlich aufzählen**, so wie der Nutzer wirklich spricht: 'Nutze diesen Skill, wenn der User sagt "schreib den Wochenbericht", "Bericht für KW", "weekly report".' Deutsche und englische Varianten mischen.
3. **Konkrete Nomen und Verben**, keine Abstraktionen ("hilft bei Dokumenten" triggert nie zuverlässig).
4. **Abgrenzung, wenn Verwechslungsgefahr besteht**: "Nicht für Monatsberichte, dafür gibt es X."

### Schritt 4: SKILL.md schreiben

Nach dem Grundgerüst in [references/skill-vorlage.md](references/skill-vorlage.md). Qualitätsregeln:

- **Schlank halten.** Die SKILL.md beschreibt den Ablauf, alles Nachschlagbare (lange Listen, Beispielsammlungen, Vorlagentexte) wandert nach `references/` und wird verlinkt. Claude lädt references nur bei Bedarf, das spart Kontext.
- **Konkret statt allgemein**: "Frag nach Zeitraum, Projekten und der einen Zahl der Woche" statt "sammle relevante Informationen".
- **Entscheidungspunkte markieren**: wo Claude auf den Nutzer wartet, wo es selbst entscheidet.
- **Fallbacks einbauen**: Was passiert, wenn ein Werkzeug oder Konnektor fehlt? Der Skill soll weiterarbeiten, nicht abbrechen.
- **Ein gutes Beispiel schlägt drei Absätze Erklärung.** Wenn das Format kritisch ist: ein Beispiel-Output in die references.
- Nicht erklären, was Claude ohnehin weiß (was Markdown ist, wie man höflich schreibt). Nur das Spezifische festhalten.

### Schritt 5: Testen und übergeben

1. Den Skill-Ordner im Arbeitsverzeichnis anlegen (`[skill-name]/SKILL.md` plus references).
2. Einen Probelauf anbieten: eine typische Anfrage durchspielen und prüfen, ob der Ablauf trägt.
3. Installation erklären (siehe unten).

## Ablauf: bestehenden Skill verbessern

Die vorhandene SKILL.md lesen und gegen diese Prüfliste halten:

- **Triggert nicht**: description zu vage oder ohne wörtliche Phrasen → Schritt 3 anwenden
- **Falsche Ergebnisse**: Ablauf zu unkonkret, Entscheidungspunkte fehlen → Schritte präzisieren, die Korrekturen des Nutzers aus der Praxis als Regeln ergänzen
- **Zu lang**: Nachschlagbares in references auslagern, Redundantes streichen
- **Bricht ab**: fehlende Fallbacks für Konnektoren und Sonderfälle ergänzen

Vor Änderungen zeigen, was geändert wird und warum. Dann umsetzen.

## Installation erklären

Nach dem Bauen dem Nutzer den passenden Weg zeigen:

- **Claude Code**: den Skill-Ordner nach `.claude/skills/` im Projekt legen (gilt nur dort) oder nach `~/.claude/skills/` im Benutzerordner (gilt überall). Danach eine neue Sitzung starten.
- **Claude Desktop / Cowork**: den Skill-Ordner in den Skills-Bereich der Einstellungen laden, oder in den Ordner legen, den die App für Skills nutzt.
- **Claude im Browser (claude.ai)**: Skills lassen sich über die Einstellungen (Funktionen/Skills) als ZIP hochladen, sofern der Plan das unterstützt. Dafür den Skill-Ordner zippen.
- Test danach: eine der Trigger-Phrasen schreiben und prüfen, ob der Skill anspringt.

## Wofür dieser Skill nicht da ist

- Prozesse erst noch herausarbeiten (dafür das Prozess-Interview; dessen Ergebnis kommt dann hierher)
- MCP-Server und Programmierwerkzeuge bauen (eigene Aufgabe)
- Prompts für andere Tools optimieren (eigene Aufgabe)
