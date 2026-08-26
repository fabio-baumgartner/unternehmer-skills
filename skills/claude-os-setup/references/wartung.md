# Wartungsroutine

Auf Zuruf ausführen ("räum mein System auf", "System-Check", "was ist veraltet"). Die Routine prüft, berichtet und ändert erst nach Freigabe.

## 1. Bestandsaufnahme

Alle Markdown-Dateien des Systems auflisten (kontext, projekte, notizen, wissen, vorlagen). Prüfen:

- Liegt etwas am falschen Ort? (Projektnotizen lose in notizen/ statt im Projektordner, Kontextwissen in einer Tagesnotiz)
- Gibt es Dateien ohne erkennbaren Zweck oder mit kryptischen Namen?

## 2. Veraltetes finden

- **Stand-Daten prüfen**: Kontextdateien, deren `Stand:` älter als 3 bis 6 Monate ist, zur Durchsicht vorschlagen. Besonders kritisch: Preise, Prioritäten, Angebot.
- **Projekte**: README-Dateien mit Status "aktiv", aber ohne Bewegung. Nachfragen: abgeschlossen, pausiert oder vergessen? Abgeschlossene nach `notizen/archiv/` vorschlagen.
- **Inhaltliche Marker**: Formulierungen wie "aktuell", "dieses Quartal", "demnächst" mit konkretem Datumsbezug prüfen. Was von gestern "demnächst" war, ist heute falsch.

## 3. Lücken finden

Gegen diese Liste prüfen, was dem System fehlt, obwohl es häufig gebraucht wird:

- Preise oder Preislogik nirgends dokumentiert
- Zielgruppe beschrieben, aber ohne echte Einwände und Formulierungen
- Stimme beschrieben, aber ohne Beispieltexte
- Werkzeuge unvollständig (wo leben eigentlich die Rechnungen?)
- Projekte im Kopf des Nutzers, die keinen Ordner haben

Lücken als Fragen formulieren, nicht als Vorwurf: "Soll ich deine Preislogik aufnehmen? Die fehlt noch, und Angebots-Aufgaben brauchen sie."

## 4. Duplikate und Widersprüche

- Dieselbe Information in zwei Dateien in unterschiedlichen Versionen (alte Preise in business.md, neue in einer Notiz)
- Widersprüche zwischen CLAUDE.md und Kontextdateien
- Vorschlag: eine Quelle pro Fakt, die andere Stelle verweist oder fliegt

## 5. Bericht und Umsetzung

Bericht in dieser Form:

```
# System-Check [Datum]

## Veraltet ([n])
- [Datei]: [was und warum] → Vorschlag: [aktualisieren/archivieren]

## Lücken ([n])
- [Was fehlt] → [warum es fehlt und eine Frage dazu]

## Duplikate/Widersprüche ([n])
- [Fakt]: [Datei A] sagt X, [Datei B] sagt Y → Vorschlag: [welche Quelle gewinnt]

## Aufräumen ([n])
- [Datei]: [Vorschlag: verschieben nach .../löschen]

Was soll ich umsetzen? (alle / Nummern / keine)
```

Regeln:

- **Nie ungefragt löschen.** Selbst nach Freigabe: Löschen heißt zuerst nach `notizen/archiv/` verschieben, endgültiges Löschen macht der Nutzer selbst.
- Nach der Umsetzung die `Stand:`-Daten der geänderten Dateien aktualisieren.
- Empfehlung an den Nutzer: den Check ungefähr einmal im Quartal laufen lassen.
