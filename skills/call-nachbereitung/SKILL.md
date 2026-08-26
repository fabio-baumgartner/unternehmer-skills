---
name: call-nachbereitung
description: Bereitet einen Call nach: holt das Transkript direkt vom verbundenen Notetaker (Fathom, Fireflies, tl;dv, Granola, Otter) oder nimmt es eingefuegt entgegen und liefert Zusammenfassung, Entscheidungen, To-dos mit Zustaendigkeit und Frist sowie eine fertige Follow-up-Mail im Ton des Gespraechs. Nutze diesen Skill, wenn der User sagt "bereite den Call nach", "Call-Nachbereitung", "fass das Meeting zusammen", "Follow-up zum Gespraech", "was waren die To-dos", "meeting follow-up", "summarize this call", "recap the meeting", "action items from the call".
---

# Call-Nachbereitung

Du verwandelst einen gelaufenen Call in drei Dinge: eine Zusammenfassung, die man in einer Minute liest, eine klare To-do-Liste und eine versandfertige Follow-up-Mail. Der Wert liegt in der Verbindlichkeit: Wer nach dem Call sauber nachfasst, gewinnt Projekte.

## Wann dieser Skill greift

Direkt nach Verkaufsgesprächen, Projektmeetings, Kickoffs oder Abstimmungen, wenn Ergebnisse festgehalten und kommuniziert werden sollen.

## Konnektoren

Prüfe beim Start, was verbunden ist:

- **Notetaker** (Fathom, Fireflies, tl;dv, Granola, Otter oder ähnliches): das jüngste Transkript automatisch holen, oder das zu einem genannten Termin ("der Call mit Müller von gestern"). Vor der Verarbeitung kurz bestätigen: "Ich habe das Transkript vom Call mit [X] um [Uhrzeit], 43 Minuten. Der richtige?"
- **Kein Notetaker**: in einem Satz sagen, dass ein verbundener Notetaker das Abholen automatisieren würde, dann: "Füg das Transkript oder deine Notizen hier ein." Auch Stichpunkte aus dem Gedächtnis funktionieren, das Ergebnis wird entsprechend gekennzeichnet.
- **Gmail oder Outlook** (optional): die Follow-up-Mail als **Entwurf** anlegen. Nie selbst senden.
- **Notion, CRM oder Aufgabentool** (optional): To-dos nach Freigabe dort ablegen. Ohne: To-dos bleiben in der Ausgabe, der Nutzer übernimmt sie selbst.

## Ablauf

### Schritt 1: Transkript beschaffen

Wie oben: vom Notetaker holen oder einfügen lassen. Kurz klären, wer die Teilnehmer waren und in welcher Beziehung sie zum Nutzer stehen (Kunde, Interessent, Partner, intern), falls nicht aus dem Transkript erkennbar. Das bestimmt den Ton der Mail.

### Schritt 2: Auswerten

Aus dem Material extrahieren:

- **Kernthemen**: worum ging es wirklich (nicht die Agenda, sondern was besprochen wurde)
- **Entscheidungen**: was wurde verbindlich beschlossen, was wurde verworfen
- **To-dos**: jede Aufgabe mit Zuständigkeit (wer) und Frist (bis wann). Wenn im Gespräch keine Frist genannt wurde: eine plausible vorschlagen und als Vorschlag kennzeichnen
- **Offene Punkte**: was vertagt oder nicht geklärt wurde
- **Signale**: bei Verkaufsgesprächen zusätzlich Kaufsignale, Einwände und den vereinbarten nächsten Schritt

Nichts erfinden. Was unklar im Transkript ist, als unklar kennzeichnen oder den Nutzer fragen.

### Schritt 3: Ergebnis ausgeben

```
# Nachbereitung: [Call-Titel], [Datum]
Teilnehmer: [Namen und Rollen]

## Zusammenfassung
3 bis 6 Sätze. Was war das Ziel, was kam heraus.

## Entscheidungen
- [Entscheidung 1]
- [Entscheidung 2]

## To-dos
| Aufgabe | Wer | Bis wann |
|---------|-----|----------|
| ... | [Name] | [Datum, ggf. "(Vorschlag)"] |

## Offene Punkte
- ...

## Nächster Schritt
Der eine wichtigste nächste Schritt in einem Satz.
```

### Schritt 4: Follow-up-Mail schreiben

Eine versandfertige Mail an die Gesprächspartner:

- **Im Ton des Gesprächs**: förmlich, wenn das Gespräch förmlich war (Sie), locker, wenn es locker war (du). Am Transkript ablesen, im Zweifel fragen
- Aufbau: Dank in einem Satz ohne Floskel, die 2 bis 3 wichtigsten Ergebnisse, die To-dos beider Seiten mit Fristen, der vereinbarte nächste Schritt mit konkretem Datum oder Terminvorschlag
- Kurz: unter 200 Wörter. Die Mail bestätigt, sie wiederholt nicht das ganze Gespräch
- Betreffzeile mitliefern ("Zusammenfassung und nächste Schritte: [Thema]")

Mit Mail-Konnektor: nach Freigabe als Entwurf ins Postfach legen. Ohne: als Markdown-Block zum Kopieren.

### Schritt 5: To-dos verteilen (optional)

Wenn ein Aufgabentool, Notion oder CRM verbunden ist: anbieten, die To-dos des Nutzers dort anzulegen. Vorher zeigen, was genau angelegt wird. Bestehende Einträge nie überschreiben.

## Regeln

- **Nie selbst senden.** Mails immer nur als Entwurf oder Textblock. Der Nutzer sendet.
- **Zuständigkeit ohne Namen ist kein To-do.** Lieber nachfragen als "Team kümmert sich" stehen lassen.
- **Vertraulich behandeln**: Transkripte enthalten oft Interna. Keine Inhalte in andere Ablagen schreiben, ohne dass der Nutzer es sagt.

## Wofür dieser Skill nicht da ist

- Angebote aus dem Call erstellen (eigene Aufgabe; dieser Skill liefert dafür die perfekte Vorlage)
- Calls transkribieren (das macht der Notetaker; ohne Transkript oder Notizen gibt es nichts nachzubereiten)
- Gesprächscoaching und Analyse der Verkaufstechnik (auf Wunsch als Zusatz, aber nicht der Kern)
