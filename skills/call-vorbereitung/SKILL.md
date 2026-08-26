---
name: call-vorbereitung
description: Bereitet auf einen Verkaufs- oder Kennenlern-Call vor. Nimmt Name, Firma oder LinkedIn-Profil entgegen, recherchiert öffentliche Quellen und liefert ein Kurzprofil mit Gesprächsaufhängern, wahrscheinlichen Einwänden und guten Fragen, alles auf einer Seite. Nutze diesen Skill, wenn der User sagt "bereite mich auf den Call vor", "Call-Vorbereitung", "wer ist mein nächster Termin", "Recherche zu [Firma] vor dem Gespräch", "Meeting-Vorbereitung", "prep me for this call", "sales call prep", "research this company before my meeting".
---

# Call-Vorbereitung

Du bereitest den Nutzer auf ein anstehendes Gespräch vor. Das Ergebnis ist **eine Seite**, die man fünf Minuten vor dem Call liest: Wer ist das, worüber reden wir, was frage ich, was wird eingewendet. Kein Recherche-Roman.

## Wann dieser Skill greift

Vor Erstgesprächen, Verkaufs-Calls, Partnergesprächen oder wichtigen Meetings mit externen Personen.

## Konnektoren

- **Web-Suche**: der Kern der Recherche. Ohne Web-Suche: in einem Satz sagen, dass die Recherche damit deutlich besser würde, und den Nutzer bitten, einzufügen, was er hat (Website-Text, LinkedIn-Profil als Text, Mail-Verlauf). Damit das Briefing bauen.
- **Google Calendar** (optional): Wenn verbunden, den nächsten externen Termin automatisch ziehen ("Dein nächster Termin ist um 14 Uhr mit Max Mustermann von der Beispiel GmbH, soll ich den vorbereiten?"). Ohne Kalender: den Nutzer fragen, um wen und welche Firma es geht.

## Ablauf

### Schritt 1: Ziel klären

Zwei kurze Fragen, falls nicht aus dem Kontext klar:

1. Mit wem sprichst du? (Name, Firma oder LinkedIn-URL; alles, was da ist)
2. Was ist das Ziel des Calls? (Erstgespräch, Angebot besprechen, Partnerschaft, Bestandskunde)

Wenn der Nutzer sein eigenes Angebot noch nie erwähnt hat, zusätzlich: Was bietest du an, und was wäre ein gutes Ergebnis dieses Calls? (Ohne das lassen sich Aufhänger und Einwände nicht zuspitzen.)

### Schritt 2: Recherchieren

Mit Web-Suche prüfen, zügig und gezielt:

- Website der Firma: Was verkaufen sie, an wen, wie positionieren sie sich?
- Größenordnung und Struktur: Team, Standorte, grobe Einordnung
- Aktuelles: News, Blogbeiträge, Stellenanzeigen (Stellenanzeigen verraten Prioritäten und Baustellen)
- Zur Person: öffentliche Rolle, Hintergrund, eigene Veröffentlichungen

LinkedIn nicht scrapen. Wenn der Nutzer LinkedIn-Inhalte nutzen will, soll er sie als Text einfügen.

Maximal 10 Minuten Recherche-Tiefe. Was sich nicht schnell finden lässt, als offene Frage für den Call notieren, das ist oft der bessere Gesprächseinstieg.

### Schritt 3: Briefing bauen

Genau dieses Format, eine Seite:

```
# Call-Briefing: [Name], [Firma]
[Datum/Uhrzeit des Calls, falls bekannt] · Ziel: [Ziel des Calls]

## Die Firma in 3 Sätzen
Was sie machen, für wen, wie sie Geld verdienen. Auffälligkeiten (Wachstum, Umbruch, Nische).

## Die Person
Rolle, Hintergrund in 1 bis 2 Sätzen, was ihr vermutlich wichtig ist.

## 3 Gesprächsaufhänger
Konkrete, recherchierte Anknüpfungspunkte. ("Ihr habt gerade [X] gelauncht: wie läuft das an?")
Kein Smalltalk-Generisches wie "das Wetter".

## Wahrscheinliche Einwände
2 bis 3 Einwände, die diese Firma diesem Angebot entgegenhalten wird, je mit einem
Antwortansatz in einem Satz. ("Kein Budget bis Q4" → aufteilen: Pilot jetzt, Rest später.)

## Gute Fragen für den Call
4 bis 6 offene Fragen, sortiert: erst Situation, dann Problem, dann Entscheidungsweg.
("Wie löst ihr [X] heute?", "Wer entscheidet am Ende mit?")

## Offen geblieben
Was die Recherche nicht klären konnte. Im Call ansprechen statt raten.
```

### Schritt 4: Übergeben

Das Briefing im Chat ausgeben. Auf Wunsch als Datei ins Arbeitsverzeichnis speichern (`call-briefing-[firma]-[datum].md`, Dateiname ohne Umlaute). Anbieten, einzelne Teile zu vertiefen, aber nur auf Nachfrage. Die eine Seite ist das Produkt.

## Regeln

- **Kurz halten.** Wenn das Briefing länger als eine Seite wird, kürzen. Der Nutzer liest es zwischen zwei Terminen.
- **Nur Verifiziertes als Fakt.** Vermutungen als solche kennzeichnen ("vermutlich", "laut Website"). Nichts erfinden, keine Umsatzzahlen schätzen und als Fakt ausgeben.
- **Auf das Angebot zuspitzen.** Aufhänger, Einwände und Fragen müssen zur Kombination aus dieser Firma und diesem Angebot passen, nicht generisch sein.

## Wofür dieser Skill nicht da ist

- Nachbereitung von Calls (Zusammenfassung, To-dos, Follow-up-Mail): eigene Aufgabe
- Tiefe Firmen-Due-Diligence oder Marktanalysen
- Kaltakquise-Listen aufbauen
