---
name: posteingang-sortieren
description: Geht den E-Mail-Posteingang durch und sortiert alles in vier Gruppen: braucht Antwort, kann warten, nur zur Kenntnis, kann weg. Fuer dringende Mails werden Antwortentwuerfe vorgeschlagen. Sendet, loescht und archiviert nie selbst. Nutze diesen Skill, wenn der User sagt "sortier meinen Posteingang", "geh meine Mails durch", "Inbox aufraeumen", "welche Mails muss ich beantworten", "E-Mail-Triage", "sort my inbox", "triage my email", "go through my emails", "inbox zero".
---

# Posteingang sortieren

Du gehst den Posteingang durch und verwandelst ihn von einem Berg in vier klare Stapel. Für die Mails, die zählen, lieferst du Antwortentwürfe. Der Nutzer behält die volle Kontrolle: **Du sendest, löschst und archivierst nie selbst. Du schlägst vor, der Nutzer bestätigt und handelt.**

## Wann dieser Skill greift

Wenn der Posteingang übergelaufen ist, nach dem Urlaub, oder als tägliche Routine.

## Konnektoren

Dieser Skill braucht **Gmail oder Outlook**.

**Wenn keines verbunden ist:** freundlich und klar sagen, dass der Skill ohne Postfach-Zugriff nicht sinnvoll arbeiten kann, und in zwei Sätzen erklären, wie man verbindet: In den Claude-Einstellungen unter Konnektoren (bzw. "Connectors" oder "Integrationen") Gmail oder Outlook verbinden und den Lesezugriff bestätigen. Danach diesen Skill erneut starten. Als Überbrückung anbieten: Der Nutzer kann einzelne Mails einfügen, dann werden diese sortiert und beantwortet, aber das ersetzt den Postfach-Durchgang nicht.

## Ablauf

### Schritt 1: Umfang klären

Beim ersten Lauf (oder wenn unklar) kurz fragen:

1. Wie weit zurück? (Standard: ungelesene plus unbeantwortete Mails der letzten 7 Tage)
2. Gibt es Absender, die immer wichtig sind (Kunden, Chef, Familie) oder nie (bestimmte Newsletter)?

Die Antworten für künftige Läufe in einer Datei `regeln.md` im Ordner dieses Skills festhalten und bei jedem Lauf lesen. Neue Erkenntnisse ("XY ist mein Steuerberater, immer wichtig") auf Zuruf ergänzen.

### Schritt 2: Sichten und sortieren

Jede Mail in genau eine Gruppe:

- **Braucht Antwort von dir**: echte Fragen, Anfragen, Fristen, wartende Menschen. Sortiert nach Dringlichkeit
- **Kann warten**: braucht irgendwann Reaktion, aber nicht heute (mit Vorschlag, wann)
- **Nur zur Kenntnis**: Informationen ohne Handlungsbedarf, in einem Satz zusammengefasst
- **Kann weg**: Newsletter ohne Wert für den Nutzer, Werbung, erledigte Threads, Automatisches

Einstufungsregeln:

- Eine Mail von einem echten Menschen mit einer Frage ist nie "Kann weg"
- Fristen und Geldbeträge machen dringend (Rechnungen, Mahnungen, Vertragsfristen, Angebote mit Ablaufdatum)
- Bei Unsicherheit die höhere Stufe wählen. Lieber eine Mail zu viel im Antwort-Stapel als eine wichtige im Papierkorb-Vorschlag
- Verdächtige Mails (Phishing-Muster, gefälschte Absender, dringlicher Zahlungsdruck) in keiner normalen Gruppe einsortieren, sondern separat mit Warnung ausweisen. Links daraus nie öffnen

### Schritt 3: Ergebnis ausgeben

```
# Posteingang: [X] Mails gesichtet

## Braucht deine Antwort ([n])
1. **[Absender]**: [Betreff]
   Worum es geht: [ein Satz] · Dringlichkeit: [heute / diese Woche]
2. ...

## Kann warten ([n])
- [Absender]: [Betreff] · Vorschlag: [nächste Woche / nach Projekt X]

## Nur zur Kenntnis ([n])
- [Absender]: [ein Satz Inhalt]

## Kann weg ([n])
- [Absender]: [Betreff]
(Vorschlag. Löschen oder archivieren musst du selbst, ich fasse nichts an.)

## Achtung ([n], nur falls vorhanden)
- [Verdächtige Mail]: [warum verdächtig]
```

### Schritt 4: Antwortentwürfe

Für die Mails im Stapel "Braucht Antwort", beginnend mit der dringendsten:

- Pro Mail einen Entwurf vorschlagen: kurz, im Ton des Nutzers (aus bisherigen Läufen und Feedback lernen, Erkenntnisse in `regeln.md` festhalten), mit klarem nächsten Schritt
- Fehlen Informationen für eine Antwort (ein Termin, eine Zahl, eine Entscheidung), den Nutzer fragen statt Platzhalter-Prosa zu schreiben
- Nach Freigabe: den Entwurf im Postfach als **Entwurf** anlegen, wenn der Konnektor das kann. Sonst als Textblock zum Kopieren. **Nie senden**

### Schritt 5: Abschluss

Kurzes Fazit: was erledigt werden kann, was der Nutzer entscheiden muss. Auf Wunsch die "Kann weg"-Liste als Checkliste ausgeben, die der Nutzer im Postfach abarbeitet.

## Harte Regeln

- **Nie senden, löschen, archivieren oder verschieben.** Auch nicht, wenn der Nutzer pauschal sagt "mach einfach". Antworten werden als Entwurf angelegt, alles andere bleibt Vorschlag.
- **Vertraulichkeit**: Mail-Inhalte nicht in andere Ablagen oder Dateien schreiben, außer der Nutzer bittet darum.
- **Keine Links aus verdächtigen Mails öffnen**, keine Anhänge unbekannter Herkunft verarbeiten.

## Wofür dieser Skill nicht da ist

- Dauerhafte Automatisierung (Filterregeln, Auto-Antworten): kann als Folgeprojekt besprochen werden, ist aber nicht dieser Skill
- Newsletter-Abmeldungen durchklicken
- Das Morning-Briefing (eigene Aufgabe; dieses zeigt nur die Antwort-Kandidaten, sortiert aber nicht)
