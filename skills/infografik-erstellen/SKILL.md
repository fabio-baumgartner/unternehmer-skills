---
name: infografik-erstellen
description: Verwandelt fertigen Text, ein Thema oder Stichpunkte in eine Infografik, zum Beispiel fuer LinkedIn. Waehlt ein passendes Layout aus einem Katalog (Zahl im Fokus, Vergleich, Schritte, Liste, Konzept) und liefert wahlweise einen fertigen Prompt fuer ein Design-Tool oder eine eigenstaendige HTML-Grafik. Nutze diesen Skill, wenn der User sagt "mach eine Infografik", "Grafik aus diesem Post", "visualisiere das", "Infographic", "infographic", "post graphic", "create an infographic", "turn this into a visual".
---

# Infografik erstellen

Du verwandelst Text in **eine** Infografik. Eine Infografik = ein Layout aus dem Katalog, gefüllt mit den Kernaussagen des Textes. Du wählst das Layout, dessen Form zum Inhalt passt, füllst die Slots mit kurzen, konkreten Texten und lieferst das Ergebnis in dem Format, das der Nutzer braucht.

## Wann dieser Skill greift

Wenn aus einem LinkedIn-Post, einem Thema, Zahlen oder Stichpunkten eine Grafik werden soll, meistens für Social Media, aber auch für Website oder Präsentation.

## Konnektoren

Keine nötig. Die Ausgabe funktioniert komplett ohne externe Tools.

## Design-Profil beim ersten Lauf

Prüfe zuerst, ob im Ordner dieses Skills eine Datei `profil.md` existiert.

**Wenn ja:** Lies sie und nutze die Werte.

**Wenn nein:** Führe ein kurzes Onboarding durch:

1. Hast du Markenfarben? (Primärfarbe, eine Akzentfarbe, Hintergrund. Hex-Codes, wenn vorhanden, sonst Beschreibung wie "dunkelblau und orange")
2. Hast du eine Hausschrift? (Wenn nein: eine klare serifenlose Schrift wie Inter oder Poppins vorschlagen)
3. Soll unten auf jeder Grafik etwas Festes stehen? (Name, Tagline, Website, Logo-Hinweis, oder nichts)
4. Eher hell oder eher dunkel als Grundstimmung?
5. Emojis auf Grafiken: ja oder nein? (Empfehlung: nein, Icons wirken hochwertiger)

Wenn der Nutzer keine Markenfarben hat, schlage eine einfache Kombination vor: neutraler heller Hintergrund, eine dunkle Textfarbe, eine Akzentfarbe. Speichere alles als `profil.md` im Ordner dieses Skills.

## Ablauf

### Schritt 1: Input aufnehmen

Akzeptiere: einen fertigen LinkedIn-Post, ein Thema, Rohdaten und Zahlen, Stichpunkte, einen Artikel. Wenn der Nutzer einen ganzen Post einfügt, visualisiert die Grafik meist dessen Kernpunkt, nicht den ganzen Post. Bei Unklarheit in einem Satz bestätigen, was die Grafik tragen soll.

### Schritt 2: Form benennen und Layouts vorschlagen

1. Benenne die Form des Inhalts in einem Satz ("Das ist ein Vorher/Nachher-Vergleich über 4 Dimensionen").
2. Lies [references/layout-katalog.md](references/layout-katalog.md) und schlage 2 bis 3 Layouts vor, jeweils mit einem Satz, warum es passt, und einem Favoriten. Mindestens ein Vorschlag sollte aus einer anderen Kategorie kommen, damit es eine echte Wahl gibt.
3. Warte auf die Entscheidung des Nutzers.

### Schritt 3: Layout füllen

1. Schreibe die Texte Slot für Slot, entsprechend dem Schema des gewählten Layouts.
2. Kurz halten: Fragmente schlagen Sätze. Wenn der Inhalt das Layout sprengt, kürzen oder ein geräumigeres Layout vorschlagen, nicht quetschen.
3. Jede Behauptung braucht eine Zahl oder einen konkreten Namen. Fehlt eine Zahl im Ausgangstext: ehrlich aus dem Text ableiten oder den Nutzer fragen. Nie Statistiken erfinden.
4. Zeige die gefüllten Texte im Chat zur Kontrolle, bevor du das Endformat baust.

### Schritt 4: Ausgabeformat wählen und bauen

Frag den Nutzer (falls noch nicht klar), welches Format er will:

**Option A: Prompt für ein Design-Tool** (Claude Design, Canva-KI, Gemini/Nano Banana oder ähnliches). Baue einen vollständigen Markdown-Prompt:

```markdown
# Design-Prompt: Infografik

**Format:** 4:5, 1080 x 1350 px (LinkedIn-Standard, bei Bedarf anpassen)
**Layout:** [Kategorie + Layout-Name], [ein Satz zur Struktur]
**Farben:** [aus profil.md]
**Schrift:** [aus profil.md]

## Inhalt (Slot fuer Slot)
[alle Slots, exakt gefüllt]

## Regeln
- [Emojis-Regel aus profil.md]
- Kurze Fragmente, keine Textwaende
- [Footer-Zeile aus profil.md, falls vorhanden]
```

**Option B: Eigenständiges HTML.** Baue eine einzelne HTML-Datei nach den Regeln in [references/html-ausgabe.md](references/html-ausgabe.md), speichere sie im Arbeitsverzeichnis (Dateiname ohne Umlaute, z. B. `infografik-2026-08-13-thema.html`) und erkläre in einem Satz, wie der Nutzer daraus ein Bild macht (im Browser öffnen, Screenshot in 1080er-Breite).

### Schritt 5: Iterieren

Feedback einarbeiten. Textkorrekturen direkt im Prompt oder HTML ändern. Ein Layoutwechsel geht zurück zu Schritt 2.

## Wenn kein Layout passt

1. Erklären, warum keines passt.
2. Das nächstliegende Layout nennen und was sich ändern müsste (auf 5 Zeilen kürzen, die eine dominante Zahl finden, in zwei Grafiken teilen).
3. Fragen: passend machen, Text umformen oder eine kleine Serie bauen?

## Wofür dieser Skill nicht da ist

- Mehrseitige Karussells (das ist eine Serie, kein Einzelbild; der Skill kann aber die Inhalte pro Slide vorbereiten)
- Logos, komplette Brand-Designs, Fotobearbeitung
- Diagramme aus großen Datensätzen (dafür Tabellenkalkulation oder ein Diagramm-Tool)
