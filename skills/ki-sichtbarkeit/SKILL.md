---
name: ki-sichtbarkeit
description: Prueft, ob ein Unternehmen in den Antworten von KI-Assistenten wie ChatGPT, Perplexity und Google-KI auftaucht, und leitet konkrete Massnahmen ab, inklusive llms.txt und strukturierter Inhalte. Nutze diesen Skill, wenn der User sagt "KI-Sichtbarkeit", "tauche ich in ChatGPT auf", "von KI empfohlen werden", "llms.txt", "KI-SEO", "AI SEO", "AEO", "GEO", "AI visibility", "show up in AI answers", "get cited by ChatGPT", "optimize for Perplexity".
---

# KI-Sichtbarkeit

Immer mehr Kunden fragen zuerst eine KI: "Welcher Steuerberater in Köln ist gut für Selbstständige?" oder "Was kostet eine Website vom Profi?" Dieser Skill prüft, ob das Unternehmen des Nutzers in solchen Antworten vorkommt, und liefert einen Maßnahmenplan, den ein Selbstständiger in ungefähr einer Stunde umsetzen kann.

**Der praktische Check steht im Zentrum, nicht die Theorie.**

## Wann dieser Skill greift

Wenn jemand wissen will, ob und wie er in KI-Antworten auftaucht, oder seine Website dafür verbessern will.

## Konnektoren

- **Web-Suche**: stark empfohlen. Damit lassen sich die Testfragen real prüfen und die Website des Nutzers lesen. Ohne Web-Suche: in einem Satz sagen, dass Web-Suche den Check besser macht, dann Plan B fahren: Der Nutzer stellt die Testfragen selbst in ChatGPT oder Perplexity und fügt die Antworten hier ein. Die Auswertung und der Maßnahmenplan funktionieren genauso.

## Ablauf

### Schritt 1: Ausgangslage aufnehmen

Frag, falls nicht bekannt:

1. Was machst du, für wen, und in welchem Gebiet? (Branche, Angebot, Region oder deutschlandweit/DACH)
2. Wie heißt das Unternehmen, und wie lautet die Website-Adresse?
3. Wer sind die 2 bis 3 wichtigsten Wettbewerber?

### Schritt 2: Kundenfragen generieren

Erzeuge 10 bis 15 Fragen, die potenzielle Kunden einer KI stellen würden. Mische diese Typen:

- **Empfehlungsfragen**: "Welche [Anbieter] in [Region] sind empfehlenswert für [Zielgruppe]?"
- **Vergleichsfragen**: "[Unternehmen] oder [Wettbewerber], was passt besser für [Fall]?"
- **Problemfragen**: "Wie löse ich [Problem, das das Angebot löst]?"
- **Kostenfragen**: "Was kostet [Leistung] ungefähr?"
- **Direktfragen**: "Was macht [Unternehmen], und ist es seriös?"

Zeige die Liste, der Nutzer darf streichen und ergänzen.

### Schritt 3: Den Check durchführen

**Mit Web-Suche:** Beantworte jede Frage so, wie eine such-gestützte KI sie beantworten würde: recherchieren, Quellen ansehen, Antwort formulieren. Notiere pro Frage: Taucht das Unternehmen auf? Als Empfehlung oder nur am Rand? Wer taucht stattdessen auf, und aus welcher Quelle stammt deren Nennung (eigene Website, Portal, Forum, Verzeichnis)?

**Ohne Web-Suche:** Gib dem Nutzer die Frageliste zum Selbsttest in ChatGPT, Perplexity und Google (KI-Übersicht) und werte die eingefügten Antworten aus. Zusätzlich: aus eigenem Wissen einschätzen, wie sichtbar die Marke ist, mit dem Hinweis, dass das eine Schätzung ist.

### Schritt 4: Lücken benennen

Fasse als Ergebnistabelle zusammen:

| Frage | Taucht auf? | Wer stattdessen | Woher deren Nennung |
|---|---|---|---|

Benenne die 3 bis 5 größten Lücken in Klartext, zum Beispiel: "Bei Kostenfragen zitieren die KIs Portale, weil auf deiner Website keine Preisspanne steht." Häufige Lückenmuster: keine klare Selbstbeschreibung auf der Website, keine Preisinformationen, keine Inhalte zu den Problemfragen, keine Präsenz in Verzeichnissen und Bewertungsportalen, Website technisch schwer lesbar.

### Schritt 5: Maßnahmenplan liefern

Erstelle einen priorisierten Plan aus [references/massnahmen.md](references/massnahmen.md), zugeschnitten auf die gefundenen Lücken. Aufbau:

1. **Sofort (heute, unter 1 Stunde)**: klare "Was wir machen"-Absätze auf der Startseite, llms.txt anlegen (Vorlage: [references/llms-txt-vorlage.md](references/llms-txt-vorlage.md)), Google-Unternehmensprofil prüfen
2. **Diese Woche**: eine Seite pro Kernfrage aus dem Check (besonders Kosten und Ablauf), FAQ-Block mit echten Kundenfragen
3. **Laufend**: Bewertungen sammeln, Einträge in relevante Verzeichnisse, Inhalte aktuell halten

Zu jeder Maßnahme: was genau tun, warum es auf die gefundene Lücke einzahlt, und fertige Textbausteine, wo möglich. Biete an, die Texte (llms.txt, Selbstbeschreibung, FAQ) direkt gemeinsam zu schreiben.

### Schritt 6: Wiedervorlage

Empfiehl, den Check in 4 bis 8 Wochen mit denselben Fragen zu wiederholen und die Ergebnistabelle zu vergleichen. Die Frageliste dafür am Ende noch einmal kompakt ausgeben.

## Ausgabeformat

1. Ergebnistabelle des Checks
2. Die 3 bis 5 Lücken in Klartext
3. Maßnahmenplan in drei Stufen (sofort / diese Woche / laufend) mit fertigen Textbausteinen

## Wofür dieser Skill nicht da ist

- Klassisches SEO-Audit (Rankings, Backlinks, Technik)
- Einzelne SEO-Artikel schreiben (eigene Aufgabe, die dieser Skill als Maßnahme empfehlen kann)
- Werbeanzeigen in KI-Produkten
