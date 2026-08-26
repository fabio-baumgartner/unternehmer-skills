# Zieltool-Regeln und Vorlagen

Nur den Abschnitt lesen, der zum Zieltool passt. Die Beispiele sind auf Unternehmer-Aufgaben gemünzt (Angebote, Mails, Analysen), nicht auf Technik-Spielereien.

## Chat-KIs: ChatGPT, Claude, Gemini

Grundregeln für alle drei:

- Explizit schlägt implizit: Format, Länge und Ton immer benennen
- Rolle zuweisen, wenn die Aufgabe Fachlichkeit braucht ("Du bist erfahrener Steuerberater...")
- Kontext mitgeben: die Situation, das Vorwissen des Empfängers, was schon versucht wurde
- Bei Fakten und Zahlen absichern: "Nutze nur Angaben, bei denen du sicher bist. Kennzeichne Unsicheres mit [unsicher]. Erfinde keine Quellen oder Statistiken."
- Verbote wirken stärker als Wünsche: "Keine Floskeln, keine Ausrufezeichen" schlägt "schreib natürlich"

Besonderheiten:

- **Claude**: folgt Anweisungen wörtlich. Bei mehrteiligen Prompts helfen klare Abschnitts-Überschriften (Kontext / Aufgabe / Regeln / Format). Begründungen mitgeben ("weil die Leser Laien sind") verbessert Übertragung auf Randfälle.
- **ChatGPT**: mit dem kleinsten Prompt starten, der das Ziel erreicht. Bei Geschwätzigkeit: "Unter 150 Wörter. Kein Vorspann, keine Einschränkungs-Absätze."
- **Gemini**: neigt zu erfundenen Quellenangaben. Immer die Absicherungszeile einbauen. Bei striktem Format ein beschriftetes Beispiel anhängen.
- **Reasoning-Modelle** (o3 und ähnliche "Denk-Modi"): kurze, saubere Anweisungen. KEIN "Denke Schritt für Schritt", kein Gedankengerüst, das verschlechtert die Ergebnisse. Ziel und Fertig-Kriterium nennen, mehr nicht.

### Vorlage Chat-Aufgabe

```
Du bist [Rolle mit relevanter Erfahrung].

Aufgabe: [präzises Verb + Gegenstand + Zweck]

Kontext: [Situation, Empfänger, was er weiß, was vorausging]

Regeln:
- [Ton]
- [Was enthalten sein muss]
- [Was nicht passieren darf]
- Länge: [Vorgabe]

Format: [Fließtext / Liste / Tabelle / Betreff + Mail]
```

## Coding-Agenten: Claude Code, Cursor und ähnliche

Diese Tools führen selbstständig Aktionen aus (Dateien ändern, Befehle ausführen). Der Prompt braucht deshalb Leitplanken:

- **Ausgangslage**: was existiert, wo es liegt
- **Zielzustand**: was am Ende funktioniert, prüfbar formuliert ("fertig, wenn ...")
- **Erlaubte Aktionen** und **verbotene Aktionen** ("Ändere nur Dateien in [Ordner]. Lösche nichts. Installiere nichts ohne Rückfrage.")
- **Stopp-Bedingungen**: "Frag nach, bevor du [Datenbank anfasst / etwas löschst / Geld kostet]"
- **Umfangs-Bremse**: "Mach nur, was hier steht. Keine zusätzlichen Funktionen, kein Umbau nebenbei."
- Große Vorhaben in nacheinander laufende Prompts teilen

### Vorlage Coding-Agent

```
Ausgangslage: [was existiert und wo]
Ziel: [was am Ende funktioniert]. Fertig, wenn: [prüfbares Kriterium]

Erlaubt: [Dateien/Ordner/Aktionen]
Verboten: [Löschen / Abhängigkeiten installieren / außerhalb von X arbeiten]
Stopp und Rückfrage bei: [riskante Aktionen]

Mach nur, was hier steht. Keine Extras.
```

## Bildgeneratoren: Midjourney, DALL-E, Stable Diffusion und ähnliche

- Reihenfolge: Motiv → Stil → Licht/Stimmung → Komposition → technische Angaben (Format)
- Konkret statt Adjektiv-Suppe: "Handwerkerin in grauer Arbeitsjacke, Werkstatt im Hintergrund, warmes Seitenlicht" schlägt "professionelles, hochwertiges Bild"
- Text im Bild vermeiden oder explizit vorgeben (viele Tools verhunzen Text)
- **Midjourney**: kommagetrennte Beschreibungen plus Parameter am Ende (z. B. Seitenverhältnis). Unerwünschtes über den No-Parameter ausschließen.
- **DALL-E (in ChatGPT)**: Fließtext funktioniert. Vordergrund, Mittelgrund, Hintergrund getrennt beschreiben.
- **Stable Diffusion**: Negativ-Prompt ist Pflicht (was nicht ins Bild soll).
- Bei Bearbeitung eines vorhandenen Bildes: nur das Delta beschreiben (was sich ändert, was exakt bleibt), Referenzbild anhängen lassen.

## Video-Tools: Sora, Runway, Kling und ähnliche

- Wie eine Regieanweisung schreiben: Szene, Motiv, Bewegung, Kamerafahrt (statisch / Fahrt / Schwenk), Licht, Stimmung
- Eine Szene pro Prompt, Länge und Format nennen
- Menschliche Bewegung explizit beschreiben, sonst wird sie generisch

## Workflow-Tools: n8n, Zapier, Make

- Struktur: Auslöser (App + Ereignis) → Schritte nummeriert (App + Aktion) → welche Daten von Schritt zu Schritt fließen
- Annahmen explizit: "setzt voraus, dass [App] verbunden ist"
- Fehlerfall benennen: was passiert, wenn ein Schritt scheitert

### Vorlage Workflow

```
Baue einen Workflow in [Tool]:

Auslöser: [App] · [Ereignis, z. B. "neue E-Mail mit Anhang"]
1. [App + Aktion], nutzt [Datenfeld] aus dem Auslöser
2. [App + Aktion], nutzt [Ergebnis aus Schritt 1]
3. ...

Fehlerfall: [z. B. "bei fehlendem Anhang: überspringen und Notiz in Slack"]
Voraussetzung: [verbundene Konten]
```

## Unbekanntes Tool

Die nächstliegende Kategorie oben wählen und deren Regeln anwenden. Wenn wirklich unklar: fragen, welches Tool es ist.
