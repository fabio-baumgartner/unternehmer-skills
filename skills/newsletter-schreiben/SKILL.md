---
name: newsletter-schreiben
description: Schreibt Newsletter-Ausgaben in einem schrittweisen Prozess vom Aufhaenger bis zum fertigen Text, mit Betreffzeilen-Varianten samt Begruendung, klarem Aufbau und Call to Action. Nutze diesen Skill, wenn der User sagt "schreib einen Newsletter", "Newsletter-Ausgabe", "E-Mail an meine Liste", "Mailing schreiben", "write a newsletter", "newsletter issue", "email to my list", "repurpose into a newsletter".
---

# Newsletter schreiben

Du begleitest den Nutzer Schritt für Schritt vom Aufhänger zur fertigen Newsletter-Ausgabe. Nie sofort einen kompletten Newsletter ausgeben: Erst Kernaussage, dann Aufbau, dann Betreff, dann Text. Jede Stufe braucht die Entscheidung des Nutzers.

## Wann dieser Skill greift

Wenn eine Newsletter-Ausgabe oder eine E-Mail an eine Liste entstehen soll, aus einer Idee, einem Erlebnis, einem Artikel oder einem Video-Transkript.

## Konnektoren

Keine nötig. Optional:

- **Gmail oder Outlook**: Wenn verbunden, kann der fertige Newsletter als Entwurf angelegt werden. Nur als Entwurf, nie direkt senden. Ohne Mail-Konnektor: den fertigen Text als Markdown-Block liefern, der Nutzer fügt ihn in sein Newsletter-Tool ein.

## Profil beim ersten Lauf

Prüfe zuerst, ob im Ordner dieses Skills eine Datei `profil.md` existiert.

**Wenn ja:** Lies sie und leg los.

**Wenn nein:** Führe ein kurzes Onboarding durch:

1. Wer liest deinen Newsletter, und warum haben sie sich angemeldet?
2. Was bietest du an, und was soll der Newsletter langfristig bewirken? (Kunden, Vertrauen, Verkäufe eines Produkts)
3. Wie oft verschickst du, und wie lang sind deine Ausgaben typischerweise?
4. Wie klingst du? Der Nutzer kann 1 bis 2 alte Ausgaben oder Texte einfügen. Analysiere Satzlänge, Ansprache (du/Sie), Humor, wie persönlich es wird.
5. Wie schließt du ab? (Grußformel, feste Signatur, PS mit Angebot)
6. Was darf nie vorkommen?

Speichere die Antworten als `profil.md` im Ordner dieses Skills. Ab dann nur noch lesen, nicht erneut fragen.

## Ablauf

### Schritt 1: Aufhänger klären

Input aufnehmen (Idee, Erlebnis, Transkript, Artikel). Dann die Kernaussage festnageln: Was soll der Leser nach dieser Ausgabe wissen, glauben oder tun? Schlage 3 bis 5 Varianten vor, jede in einem Satz. Der Nutzer wählt.

### Schritt 2: Aufbau vorschlagen

Lies [references/aufbau.md](references/aufbau.md). Schlage 2 bis 3 Gliederungen vor, jede mit:

- Framework (PAS, BAB, Story → Lektion → System, Mythos-Aufräumer oder eine Mischung)
- Abschnitten mit je einem Satz, was hineinkommt
- einem Satz, warum diese Struktur zu diesem Inhalt passt

Der Nutzer wählt oder kombiniert. Erst dann weiter.

### Schritt 3: Betreffzeilen

Lies [references/betreffzeilen.md](references/betreffzeilen.md). Schlage 5 bis 7 Betreffzeilen vor, gemischt aus den Mustern (Zahl/Ergebnis, Neugier-Lücke, klare Ansage, Contrarian). Zu jeder:

- die Betreffzeile
- ein Satz Begründung, warum sie geöffnet wird
- ein Vorschautext (die Zeile, die im Posteingang nach dem Betreff sichtbar ist)

Der Nutzer wählt.

### Schritt 4: Newsletter schreiben

Schreibe die komplette Ausgabe entlang der gewählten Gliederung. Regeln:

- Ton und Ansprache aus `profil.md`, der Text muss klingen wie der Nutzer, nicht wie eine Marketingabteilung
- Kurze Absätze, oft nur ein bis zwei Sätze
- Übergänge müssen tragen: Jeder Abschnitt endet so, dass der nächste die natürliche Fortsetzung ist
- Konkrete Zahlen und echte Details statt Allgemeinplätze. Nichts erfinden: Wenn eine Geschichte oder Zahl fehlt, den Nutzer fragen
- Ein CTA pro Ausgabe, klar und ohne Druck. Zusätzliche Links nur, wenn sie dem Leser dienen
- Rhetorische Fragen sparsam, Floskeln gar nicht ("in der heutigen Zeit", "nahtlos", "spannend")
- Abschluss und Signatur aus `profil.md`

Gib den kompletten Text als Markdown-Block aus.

### Schritt 5: Iterieren und übergeben

Feedback einarbeiten, jede Version wieder als kompletter Block. Wenn der Text steht:

- Mit Mail-Konnektor: anbieten, einen Entwurf im Postfach anzulegen (Betreff + Text). Nie senden.
- Ohne: der Nutzer kopiert den Block in sein Newsletter-Tool.

## Ausgabeformat

Betreffzeile, Vorschautext und kompletter Newsletter-Text als ein Markdown-Block, copy-paste-fertig.

## Wofür dieser Skill nicht da ist

- Automatisierte Sequenzen und Funnel (Willkommensserie, Verkaufssequenz): eigenes Projekt mit eigener Dramaturgie
- Listenaufbau, Anmeldeseiten, technisches Setup des Newsletter-Tools
- Kalt-Akquise-Mails an Fremde
