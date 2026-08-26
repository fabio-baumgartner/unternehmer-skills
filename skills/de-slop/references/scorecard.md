# Scorecard-Format

Das Ausgabeformat ist fest. Immer genau diese Form, damit der Nutzer sich orientieren kann.

## Aufbau

1. **Gesamturteil** als Überschrift, eines von drei:
   - `# Kann raus` : keine Funde oder nur Kosmetik
   - `# Kann raus, mit Anmerkungen` : echte Funde, aber nichts Grundsätzliches
   - `# Noch nicht` : mindestens ein Blocker
2. **Eine Zeile Einordnung**: was geprüft wurde und wie es einsortiert wurde ("LinkedIn-Post, extern, geprüft gegen die universellen Muster und deine standards.md").
3. **Die Fundtabelle**, nummeriert, schwerste Funde zuerst.
4. **Die Entscheidungsfrage** an den Nutzer.

## Das Format

```
# [Gesamturteil]

Geprüft: [Textart], [extern/intern]. Grundlage: [Muster-Katalog / zusätzlich standards.md].

| Nr. | Stelle (Zitat) | Muster | Vorschlag | Gewicht |
|-----|----------------|--------|-----------|---------|
| 1 | "In der heutigen schnelllebigen Welt ist E-Mail-Marketing wichtiger denn je." | Einstiegs-Floskel (1.1) | Streichen, mit dem zweiten Satz beginnen: "Die meisten Newsletter werden nicht geöffnet, weil ..." | Sollte raus |
| 2 | "nicht nur Zeit, sondern auch Geld" | Nicht-nur-sondern-auch (2.2) | Konkret machen: "spart dir rund 4 Stunden pro Woche" | Kosmetik |

Welche Funde soll ich umsetzen? (alle / Nummern / keine)
```

## Regeln für die Tabelle

- **Stelle**: das wörtliche Zitat aus dem Text, notfalls gekürzt mit "...". Ohne Zitat kein Fund.
- **Muster**: der Name aus dem Katalog, mit Nummer, damit der Nutzer nachlesen kann. Bei Funden aus `standards.md`: "eigener Standard" plus das betroffene No-Go.
- **Vorschlag**: konkret genug, dass der Nutzer ihn ohne Rückfrage übernehmen könnte. Bei Seelenlosigkeits-Funden: benennen, WO der Text eine Meinung oder ein Beispiel braucht, keinen erfundenen Inhalt einsetzen.
- **Gewicht**: Blocker / Sollte raus / Kosmetik (Definitionen im Muster-Katalog).
- Jeder Fund eine eigene Zeile. Keine Sammel-Zeilen wie "diverse Floskeln".
- Bei mehr als 15 Funden: die schwersten 15 zeigen und dazuschreiben, dass es weitere Kosmetik-Funde gibt, abrufbar auf Wunsch.

## Was NICHT in die Ausgabe gehört

- Keine komplett umgeschriebene Version des Textes (die kommt erst nach der Entscheidung des Nutzers, und nur an den gewählten Stellen)
- Kein Lob-Sandwich und keine Entschuldigungen
- Keine erfundenen Funde, um gründlich zu wirken. `# Kann raus` mit leerer Tabelle ist ein gutes, normales Ergebnis
