---
name: morning-briefing
description: Erstellt eine kompakte Uebersicht fuer den Tag: Termine, offene Aufgaben, Mails, die eine Antwort brauchen, und was von gestern liegen geblieben ist. Kurz und scanbar, kein Fliesstext. Kann als wiederkehrende Aufgabe eingerichtet werden. Nutze diesen Skill, wenn der User sagt "Morning Briefing", "was steht heute an", "mein Tagesueberblick", "Tagesbriefing", "wie sieht mein Tag aus", "morning brief", "daily briefing", "what's on today", "start my day".
---

# Morning-Briefing

Du lieferst eine Übersicht für den Tag, die man in unter einer Minute liest: Termine, Aufgaben, Mails mit Antwortbedarf, Liegengebliebenes. Scanbar, priorisiert, ohne Fließtext.

## Wann dieser Skill greift

Morgens zum Tagesstart, oder wann immer der Nutzer eine Standortbestimmung für den Tag will.

## Konnektoren

Prüfe beim Start, was verbunden ist, und nutze alles, was da ist:

- **Google Calendar oder Outlook-Kalender**: Termine des Tages automatisch ziehen (Titel, Uhrzeit, Teilnehmer, Ort/Link).
- **Gmail oder Outlook**: ungelesene und unbeantwortete Mails der letzten 1 bis 2 Tage sichten und die heraussuchen, die eine Antwort vom Nutzer brauchen. Nur lesen, nie etwas senden, verschieben oder löschen.
- **Aufgabentool oder Notion** (falls verbunden): offene Aufgaben mit Fälligkeit heute oder überfällig.

**Ohne Konnektoren** bricht nichts ab. Sag in einem Satz, welche Verbindung das Briefing automatisch machen würde, und arbeite manuell:

1. Frag: "Welche Termine hast du heute, und was muss heute unbedingt fertig werden?"
2. Prüfe, ob im Arbeitsverzeichnis eine Aufgabendatei liegt (z. B. `aufgaben.md`, `todo.md` oder eine vom Nutzer benannte Datei). Wenn ja: lesen und einbeziehen. Beim ersten Lauf fragen, ob so eine Datei existiert und wo.

## Ablauf

### Schritt 1: Daten sammeln

Aus allen verfügbaren Quellen zusammentragen:

- **Termine heute**: Uhrzeit, Titel, mit wem. Auffälligkeiten markieren (Überschneidungen, fehlende Video-Links, Termine ohne Agenda)
- **Aufgaben**: heute fällig, überfällig, und was gestern geplant war und nicht erledigt wurde (aus dem letzten Briefing oder der Aufgabendatei, falls vorhanden)
- **Mails**: die 3 bis 7 Mails, die tatsächlich eine Antwort des Nutzers brauchen. Newsletter und FYI-Mails gehören nicht ins Briefing

### Schritt 2: Priorisieren

Nicht alles ist gleich wichtig. Markiere maximal 3 Dinge als "Heute zählt": die Termine oder Aufgaben, deren Scheitern heute echten Schaden anrichten würde. Der Rest ist Übersicht.

### Schritt 3: Briefing ausgeben

Genau dieses Format, kompakt halten:

```
# Briefing [Wochentag, Datum]

## Heute zählt
1. [Das Wichtigste, mit Uhrzeit falls terminiert]
2. ...
3. ...

## Termine
- 09:00  [Titel] mit [Person] [Auffälligkeit, falls vorhanden]
- 14:00  ...
(Keine Termine: "Heute frei von Terminen.")

## Braucht deine Antwort
- [Absender]: [Betreff] · [warum es eilt, in 3 bis 5 Worten]
- ...

## Aufgaben
- [ ] [heute fällig]
- [ ] [überfällig, markiert mit "seit TT.MM."]

## Von gestern liegen geblieben
- [Punkt] → Vorschlag: [heute einplanen / delegieren / bewusst streichen]
```

Abschnitte ohne Inhalt weglassen statt leer zeigen. Danach eine Frage, maximal: "Soll ich eine der Antwort-Mails vorbereiten oder einen Termin vorbereiten?"

### Schritt 4: Gedächtnis für morgen

Wenn der Nutzer es erlaubt, am Ende den Stand in eine Datei `briefing-log.md` im Arbeitsverzeichnis schreiben (Datum, offene Punkte). Daraus speist sich morgen der Abschnitt "Von gestern liegen geblieben". Ohne Datei funktioniert das Briefing trotzdem, nur ohne Gestern-Vergleich.

## Als wiederkehrende Aufgabe einrichten

Der Skill kann jeden Werktag automatisch laufen. So richtet der Nutzer das ein:

- **Claude mit geplanten Aufgaben** (Desktop-App oder Claude Code mit Scheduler): eine wiederkehrende Aufgabe anlegen, z. B. werktags 7:30 Uhr, mit dem Prompt "Erstelle mein Morning-Briefing". Wenn die Umgebung einen Befehl wie `/schedule` oder "geplante Aufgaben" anbietet, diesen nutzen.
- **Ohne Scheduler**: der Nutzer startet den Tag mit der Nachricht "Morning Briefing". Ein Satz genügt, der Skill übernimmt den Rest.

Beim ersten Lauf einmalig anbieten: "Soll ich dir zeigen, wie das Briefing jeden Morgen automatisch kommt?"

## Regeln

- **Kein Fließtext.** Listen, Zeiten, Stichworte. Das Briefing wird überflogen, nicht gelesen.
- **Nichts erfinden.** Ohne Kalenderzugriff keine Termine "vermuten". Lücken benennen ("Kalender nicht verbunden, Termine bitte kurz nennen").
- **Nur lesen.** Der Skill sendet keine Mails, verschiebt keine Termine, hakt keine Aufgaben ab. Er schlägt vor, der Nutzer handelt.

## Wofür dieser Skill nicht da ist

- Mails beantworten und Posteingang aufräumen (eigene Aufgabe: Posteingang sortieren)
- Wochen- und Monatsplanung
- Nachrichten- und Branchen-News (kann auf Wunsch ergänzt werden, gehört aber nicht zum Kern)
