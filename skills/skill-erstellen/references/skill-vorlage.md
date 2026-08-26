# Grundgerüst: SKILL.md

Die bewährte Struktur. Abschnitte, die für den konkreten Skill keinen Inhalt haben, fallen weg.

```markdown
---
name: [skill-name, klein, bindestriche, keine umlaute]
description: [Ein bis zwei Saetze, was der Skill tut.] Nutze diesen Skill, wenn der User sagt "[woertliche Phrase 1]", "[Phrase 2]", "[Phrase 3]", "[englische Phrase]".
---

# [Skill-Titel]

[Zweck in 2 bis 3 Saetzen: was der Skill tut und was am Ende steht. Wenn es
eine goldene Regel gibt (z. B. "nie sofort das Endergebnis ausgeben"), steht
sie hier fett.]

## Wann dieser Skill greift

[1 bis 2 Saetze: die Situationen. Plus Abgrenzung bei Verwechslungsgefahr.]

## Konnektoren

[Welche Konnektoren oder Werkzeuge helfen, und der Fallback ohne sie:
"Wenn X verbunden ist: automatisch nutzen. Wenn nicht: [manueller Weg]."
Wenn keine noetig sind: "Keine noetig."]

## Ablauf

### Schritt 1: [Name]
[Was passiert. Was Claude fragt, was es selbst tut. Konkret: "Frag nach A, B
und C", nicht "sammle Informationen".]

### Schritt 2: [Name]
[...]
[Entscheidungspunkte markieren: "Warte auf die Entscheidung des Nutzers,
bevor du weitermachst."]

## Ausgabeformat

[Wie das Ergebnis aussieht. Bei festem Format: das Geruest zeigen.]

## Wofür dieser Skill nicht da ist

- [Naheliegende, aber falsche Verwendungen]
```

## Wann references/ anlegen

| Inhalt | Wohin |
|--------|-------|
| Der Ablauf selbst, Regeln, Entscheidungspunkte | SKILL.md |
| Lange Listen (Hooks, Muster, Checklisten) | references/[thema].md |
| Beispiel-Outputs und Vorlagentexte | references/beispiele.md |
| Fachwissen, das nur manchmal gebraucht wird | references/[thema].md |

In der SKILL.md an der Stelle verlinken, wo der Ablauf die Datei braucht: "Lies [references/hooks.md](references/hooks.md) und schlage 5 Hooks vor." Claude lädt die Datei dann genau dort.

## Wenn der Skill sich Dinge merken soll

Für Skills mit Onboarding (Profil, Preislogik, Standards): beim ersten Lauf abfragen, als Markdown-Datei im Skill-Ordner speichern (z. B. `profil.md`), bei jedem weiteren Lauf lesen statt fragen. In der SKILL.md beschreiben: "Pruefe, ob im Ordner dieses Skills eine Datei profil.md existiert. Wenn ja: lesen. Wenn nein: [Onboarding-Fragen], dann speichern."

## Häufige Fehler

- **description beschreibt das Thema statt den Auslöser**: "Hilft bei LinkedIn" triggert nicht. Wörtliche Nutzer-Phrasen aufzählen.
- **SKILL.md als Aufsatz**: Claude braucht Anweisungen, keine Motivationsprosa.
- **Alles in eine Datei**: 400 Zeilen SKILL.md mit drei Listen ist schlechter als 120 Zeilen plus zwei references.
- **Kein Fallback**: Der Skill setzt ein Tool voraus und bricht ohne es ab.
- **Zu viel Automatik**: Schritte, bei denen der Nutzer entscheiden will (Ton, Preis, Versand), automatisch zu erledigen, zerstört Vertrauen. Entscheidungspunkte einbauen.
