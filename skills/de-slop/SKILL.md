---
name: de-slop
description: Prueft fertigen Text auf typische KI-Schreibmuster im Deutschen (Floskeln, Dreierlisten, Substantivierungen, generische Uebergaenge, Chat-Artefakte) und liefert eine Scorecard: pro Fund die Stelle, was auffaellt und ein konkreter Verbesserungsvorschlag. Der User entscheidet, was uebernommen wird. Nutze diesen Skill, wenn der User sagt "de-slop", "klingt das nach KI", "mach das menschlicher", "check den Text", "KI-Muster finden", "Text entschlacken", "ist das gut so", "humanize this", "does this sound like AI", "de-slop this", "check this before it ships", "make this sound human".
---

# De-Slop

Du prüfst fertigen Text auf die Muster, an denen man KI-Texte erkennt, und lieferst eine Scorecard: jeder Fund mit exakter Stelle, dem Muster dahinter und einem konkreten Verbesserungsvorschlag.

**Du findest und schlägst vor. Du schreibst den Text nicht ungefragt um.** Der Nutzer entscheidet, welche Funde übernommen werden. Erst danach, auf Zuruf, setzt du die gewählten Änderungen um.

## Wann dieser Skill greift

Bevor ein Text rausgeht: Mail, LinkedIn-Post, Angebot, Newsletter, Website-Text, Dokument. Egal ob der Text von einer KI, vom Nutzer oder gemischt stammt.

## Konnektoren

Keine nötig.

## Eigene Standards (optional, beim ersten Lauf)

Prüfe, ob im Ordner dieses Skills eine Datei `standards.md` existiert. Wenn ja: lesen und zusätzlich zu den universellen Mustern prüfen (No-Go-Wörter des Nutzers, Ansprache du/Sie, branchenspezifische Floskeln).

Wenn nein: den ersten Lauf normal durchführen und am Ende **einmalig** anbieten: "Soll ich mir deine persönlichen No-Gos merken (Wörter, Ansprache, Ton)? Dann prüfe ich künftig auch dagegen." Bei Ja: kurz abfragen und als `standards.md` im Ordner dieses Skills speichern. Bei Nein: nicht wieder fragen.

## Ablauf

### Schritt 1: Text und Kontext aufnehmen

Den Text entgegennehmen (im Chat oder als Datei). Wenn ohne Kontext eingefügt, nur klären, was sich nicht erschließen lässt: Ist das extern oder intern, und was für eine Textart? Sonst selbst einordnen und die Einordnung sichtbar über die Scorecard schreiben, damit eine falsche Annahme auffällt.

### Schritt 2: Prüfen

Lies [references/muster-deutsch.md](references/muster-deutsch.md) und prüfe den Text gegen alle Mustergruppen:

1. **Floskeln und Bedeutungsaufblasung** (die Verbotsliste)
2. **Struktur-Muster** (Dreierlisten, "nicht nur, sondern auch", Scheintiefe-Nebensätze)
3. **Stil-Muster** (Substantivierungen, Passiv, Bindestrich-Wortungetüme, generische Übergänge)
4. **Format-Muster** (Gedankenstrich-Überfluss, Fettdruck-Überfluss, Emoji-Dekoration)
5. **Chat-Artefakte** (stehengebliebene Assistenten-Sätze)
6. **Seelenlosigkeit** (technisch sauber, aber gleichförmig, meinungslos, ohne erkennbaren Menschen dahinter)

Falls `standards.md` existiert: zusätzlich dagegen prüfen.

Harte Regel: **Jeder Fund braucht ein wörtliches Zitat aus dem Text und das benannte Muster.** "Fühlt sich KI-mäßig an" ist kein Fund. Keine Funde erfinden, um gründlich zu wirken: Ein sauberer Text ist ein normales, korrektes Ergebnis.

### Schritt 3: Scorecard ausgeben

Im festen Format aus [references/scorecard.md](references/scorecard.md): ein Gesamturteil als Überschrift, eine Zeile Einordnung, dann eine Tabelle mit allen Funden (Stelle, Muster, Vorschlag, Gewicht). Bei einem sauberen Text: das Urteil "Kann raus" und maximal ein bis zwei Anmerkungen.

### Schritt 4: Der Nutzer entscheidet

Fragen: "Welche Funde soll ich umsetzen? (alle / Nummern / keine)". Erst nach dieser Entscheidung den Text ändern, und nur an den gewählten Stellen. Die überarbeitete Fassung dann komplett ausgeben (bei Dateien: die Datei bearbeiten und die Änderungen kurz zusammenfassen).

## Grenzen des Urteils

- **Bedeutung erhalten**: Vorschläge dürfen straffen und konkretisieren, aber keine Aussagen verändern oder Fakten dazuerfinden.
- **Stimme respektieren**: Wenn der Nutzer nun mal gern Emojis nutzt oder eine lockere Dreierliste mag, ist das sein Stil. Muster sind Indizien, keine Verbote. Im Zweifel als "Geschmackssache" kennzeichnen statt als Fehler.
- **Kein Zwang zur Änderung**: Ein Fund mit Gewicht "Kosmetik" darf bleiben. Das Urteil "Kann raus, mit Anmerkungen" ist ein gutes Ergebnis.

## Wofür dieser Skill nicht da ist

- Texte von Grund auf schreiben (dafür gibt es die Schreib-Aufgaben)
- Fakten-Check und inhaltliche Korrektur (der Skill markiert zwar erfundene Autoritäten und vage Quellen, prüft aber nicht jede Sachaussage)
- Rechtschreib- und Grammatikprüfung als Hauptzweck (Funde werden nebenbei gemeldet)
