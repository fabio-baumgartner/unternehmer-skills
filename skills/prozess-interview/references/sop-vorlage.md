# SOP-Vorlage

Das Ergebnis von Phase 5. Jeder Abschnitt wird aus dem Interview gefüllt, nichts bleibt als Platzhalter stehen.

```markdown
# SOP: [Prozessname]

**Zweck:** [Warum es diesen Prozess gibt, ein bis zwei Saetze]
**Gilt fuer:** [Wer danach arbeitet]
**Ausloeser:** [Was den Prozess startet, z. B. "Anfrage per Mail geht ein"]
**Ergebnis:** [Was am Ende vorliegt und woran man erkennt, dass es gut ist]
**Stand:** [Datum] · **Verantwortlich:** [Name/Rolle]

## Voraussetzungen

- [Zugaenge, Werkzeuge, Vorlagen, Informationen, die vorliegen muessen]

## Ablauf

### Schritt 1: [Name des Schritts]

**Was:** [Konkrete Handlung]
**Wie:** [Details, die ein Fremder braucht: wo klicken, was schreiben, welche Vorlage]
**Entscheidung (falls vorhanden):** Wenn [Bedingung], dann [Weg A]. Sonst [Weg B].
**Fertig, wenn:** [pruefbares Kriterium]

### Schritt 2: ...

[alle Schritte in dieser Form]

## Sonderfaelle

| Situation | Was tun |
|-----------|---------|
| [Input unvollstaendig] | [Reaktion] |
| [Werkzeug/Person nicht verfuegbar] | [Reaktion] |
| [Abbruchfall] | [Woran man ihn erkennt, was dann passiert] |

## Häufige Fehler

- [Fehler aus der Erfahrung des Nutzers] → [wie man ihn vermeidet]

## Offene Punkte

[Nur wenn wirklich etwas bewusst offen gelassen wurde, mit Datum und Zustaendigkeit. Ideal: leer.]
```

## Qualitätskriterien für das fertige SOP

- Der Fremden-Test: Eine Person, die den Prozess nie ausgeführt hat, könnte es allein mit diesem Dokument
- Jeder Schritt hat ein prüfbares "Fertig, wenn"
- Jede Verzweigung nennt die Bedingung und beide Wege
- Keine vagen Verben ("prüfen", "klären", "abstimmen") ohne Angabe, worauf oder mit wem
- Sonderfälle stehen im Dokument, nicht nur im Kopf des Nutzers

## Grundgerüst: aus dem SOP einen Claude Skill machen

Wenn der Nutzer statt (oder zusätzlich zum) SOP einen Skill will:

```markdown
---
name: [prozessname-kurz, kleinbuchstaben, bindestriche, keine umlaute]
description: [Was der Skill macht] plus Ausloese-Phrasen: Nutze diesen Skill, wenn der User sagt "[Phrase 1]", "[Phrase 2]", "[englische Phrase]".
---

# [Prozessname]

[Zweck in 2 bis 3 Saetzen, aus dem SOP-Kopf]

## Ablauf

[Die SOP-Schritte, umformuliert als Anweisungen an Claude: was Claude tut,
was es den Nutzer fragt, was es selbst entscheidet. Entscheidungsregeln und
Sonderfaelle aus dem SOP uebernehmen.]

## Ausgabeformat

[Wie das Ergebnis aussieht]
```

Ablage: als Ordner `[prozessname]/SKILL.md` an dem Ort, an dem die Claude-Umgebung des Nutzers Skills erwartet (bei Claude Code: `.claude/skills/` im Projekt oder `~/.claude/skills/` global; in der App: über die Skill-Verwaltung hochladen). Wenn unklar, den Nutzer fragen, welche Umgebung er nutzt.
