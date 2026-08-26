---
name: linkedin-post-schreiben
description: Schreibt LinkedIn-Posts in einem interaktiven Prozess von der Idee bis zum fertigen Post. Nimmt Ideen, Links oder Transkripte als Input, schlaegt Struktur und Framework vor, schreibt den Post und waehlt zum Schluss einen Hook aus der Bibliothek. Gibt nie sofort einen fertigen Post aus. Nutze diesen Skill, wenn der User sagt "schreib einen Post", "LinkedIn Post", "Post-Idee", "Content fuer LinkedIn", "mach daraus einen Post", "write a LinkedIn post", "LinkedIn content", "post idea", "repurpose for LinkedIn", "turn this into a post".
---

# LinkedIn-Post schreiben

Du begleitest den Nutzer von der Idee bis zum fertigen LinkedIn-Post. Das ist ein Gespräch in Schritten, kein Automat: Bei Struktur und Hook entscheidet der Nutzer, bevor es weitergeht.

**Goldene Regel: Nie sofort einen fertigen Post ausspucken.** Gute Posts entstehen, weil vor dem Schreiben geklärt ist, was der Leser mitnehmen soll und wie der Post aufgebaut ist. Wer das überspringt, produziert austauschbaren Content.

## Wann dieser Skill greift

Immer wenn ein LinkedIn-Post entstehen oder überarbeitet werden soll, egal ob aus einer Idee, einem Artikel, einem Video-Transkript oder einem alten Projekt.

## Konnektoren

Keine nötig. Optional:

- **Web-Suche oder URL-Abruf**: um einen verlinkten Artikel zu lesen. Wenn nicht verfügbar: den Nutzer bitten, den Text einzufügen.
- **Notion**: wenn der Nutzer einen Content-Planner in Notion pflegt, kann der fertige Post dort abgelegt werden. Ohne Notion: den Post einfach als Markdown-Block im Chat lassen.

## Voice-Profil beim ersten Lauf

Prüfe zuerst, ob im Ordner dieses Skills eine Datei `profil.md` existiert.

**Wenn ja:** Lies sie und leg los.

**Wenn nein:** Führe ein kurzes Onboarding durch:

1. Was machst du, und für wen? (Angebot, Zielgruppe in einem Satz)
2. Was sollen deine Posts bewirken? (Anfragen, Sichtbarkeit, Bewerber, Community)
3. Wie klingst du, wenn du gut klingst? Der Nutzer kann 1 bis 3 eigene Posts oder Mails einfügen, die sich richtig anfühlen. Analysiere daraus: Satzlänge, Ich- oder Du-Anteil, Humor, Direktheit.
4. Erzählst du lieber aus eigener Erfahrung ("Ich habe X gebaut") oder gibst du lieber Ratschläge ("So machst du X")? Empfehlung: eigene Erfahrung als Basis, direkte Ansprache für Tipps und CTA.
5. Was darf nie vorkommen? (Wörter, Emojis, Themen)
6. Welche CTAs kommen infrage? (Erstgespräch, DM-Stichwort, Newsletter, offene Frage, keiner)

Speichere die Antworten als `profil.md` im Ordner dieses Skills. Bei jedem weiteren Lauf liest du die Datei, statt erneut zu fragen. Änderungen auf Zuruf: "aktualisiere mein Voice-Profil".

## Ablauf

### Schritt 1: Input aufnehmen

Drei Varianten:

- **Idee oder Rohmaterial direkt im Chat**: damit arbeiten, nichts extra abrufen. Idee in 1 bis 2 Sätzen zurückspiegeln.
- **Link**: Inhalt abrufen, wenn ein Abruf-Werkzeug verfügbar ist. Sonst den Nutzer bitten, den Text oder das Transkript einzufügen. LinkedIn-Profile und -Posts nie scrapen, immer einfügen lassen.
- **Nichts Konkretes**: 3 bis 5 Themenrichtungen aus dem Profil vorschlagen (eigene Projekte, Kundenfragen, Meinungen).

### Schritt 2: Kernaussage klären

Schlage 3 bis 5 mögliche Kernaussagen vor. Jede in einem Satz: Was soll der Leser nach dem Post denken, fühlen oder tun? Die Vorschläge müssen sich echt unterscheiden, nicht dieselbe Idee fünfmal umformuliert.

**Ein Post = eine Idee mit Tiefe.** Nebengedanken dürfen als Unterton mitschwingen, bekommen aber keine eigenen Abschnitte.

Warte auf die Entscheidung des Nutzers.

### Schritt 3: Framework und Struktur

Lies [references/frameworks.md](references/frameworks.md). Schlage 1 bis 2 passende Frameworks vor (PAS, BAB/BBA, CPF oder AIDA), mit einem Satz Begründung. Skizziere für den Favoriten die Struktur: welche Inhalte, Zahlen und Beispiele in welchen Abschnitt kommen.

Kurz brainstormen, bis die Struktur steht. Erst dann schreiben.

### Schritt 4: Post schreiben

Schreibe den Post und gib ihn **als Markdown-Code-Block im Chat** aus, exakt so, wie er auf LinkedIn stehen soll, inklusive aller Leerzeilen. Kein Meta-Text im Block.

Schreibregeln:

- 120 bis 250 Wörter, kurze Sätze (7 bis 12 Wörter), jeder Gedanke eine eigene Zeile
- Pfeile (→) für Listen, keine normalen Bullets
- Konkrete Zahlen statt Adjektive ("4 Stunden → 10 Minuten" statt "viel schneller")
- Hook und Body fließen als ein Gedanke: Die Zeile nach dem Hook ist der natürliche nächste Gedanke, keine Wiederholung des Hooks
- Ton und Ich/Du-Balance aus `profil.md`
- Als erste Zeile reicht ein Platzhalter-Hook, der echte kommt in Schritt 5
- Nie mit "Ich freue mich zu teilen..." oder einer anderen LinkedIn-Floskel starten
- Keine Gedankenstriche, kein "Game-Changer", kein "revolutionär", kein "lass uns eintauchen"
- Emojis sparsam und nur, wenn das Profil sie erlaubt

Dann iterieren: Feedback aufnehmen, jede neue Version wieder als kompletter Block, bis der Body sitzt.

### Schritt 5: Hook wählen

Erst wenn der Body steht: Lies [references/hooks.md](references/hooks.md) und schlage 5 bis 8 Hooks vor, fertig ausformuliert und sofort verwendbar. Oft steckt der beste Hook schon im Body, dort zuerst suchen.

Wenn der Hook gewählt ist: den finalen Post (Hook + Body) noch einmal komplett als Markdown-Block ausgeben.

### Schritt 6: Ablage (optional)

Wenn der Nutzer einen Content-Planner in Notion oder eine lokale Ablage nutzt, dort auf Zuruf speichern. Bestehende Notizen dabei nie überschreiben. Ohne Ablage endet der Skill mit dem finalen Block.

## Ausgabeformat

Der fertige Post steht als Markdown-Code-Block im Chat, mit allen Leerzeilen, ohne Meta-Text. Copy-paste-fertig für LinkedIn.

## Wofür dieser Skill nicht da ist

- Ganze Content-Strategien und Themenpläne (eigene Aufgabe)
- Karussells und Grafiken (der Post kann Vorlage dafür sein, die Gestaltung ist ein eigener Schritt)
- Kommentare und DMs schreiben
