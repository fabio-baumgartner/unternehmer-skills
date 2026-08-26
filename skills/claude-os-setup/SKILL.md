---
name: claude-os-setup
description: Baut aus einem Onboarding-Interview und vorhandenen Dokumenten eine Ordnerstruktur mit Kontextdateien auf, damit Claude das Business des Users kennt und nicht in jedem Chat alles neu erklaert bekommen muss. Haelt das System auf Zuruf aktuell (aufraeumen, Luecken finden, Veraltetes markieren). Nutze diesen Skill, wenn der User sagt "richte mein Claude OS ein", "Setup", "Claude soll mein Business kennen", "Kontext-System aufbauen", "mein System aufraeumen", "set up my workspace", "claude os", "teach Claude my business", "organize my context".
---

# Claude OS Setup

Du richtest ein dauerhaftes Arbeitssystem ein: eine Ordnerstruktur mit Kontextdateien, in der Claude das Business des Nutzers kennt. Einmal aufgesetzt, entfällt das ewige Erklären am Chat-Anfang. Das System besteht aus reinen Markdown-Ordnern und funktioniert mit jedem Editor und jeder Claude-Umgebung. Kein spezielles Programm nötig.

Der Skill hat zwei Betriebsarten: **Einrichten** (beim ersten Mal) und **Warten** (später, auf Zuruf).

## Wann dieser Skill greift

- Einrichten: beim Start, oder wenn jemand sein Kontext-Chaos in ein System verwandeln will
- Warten: "räum mein System auf", "was ist veraltet", "finde Lücken"

## Konnektoren

Keine nötig. Optional: **Google Drive oder Notion** als Quelle für vorhandene Dokumente beim Onboarding. Ohne: Der Nutzer fügt Inhalte ein oder verweist auf lokale Dateien.

## Betriebsart 1: Einrichten

### Vorprüfung

Prüfe, ob im aktuellen Arbeitsverzeichnis bereits eine `CLAUDE.md` liegt. Wenn ja, ist hier schon ein System: fragen, ob das Interview wiederholt (Dateien aktualisieren), alles zurückgesetzt (zweimal bestätigen lassen) oder abgebrochen werden soll. Wenn nein: direkt loslegen.

Außerdem klären, wo das System leben soll, falls das aktuelle Verzeichnis nicht offensichtlich passt: "In welchem Ordner soll dein System zu Hause sein?" Der Ordner sollte lokal liegen und in Zukunft der Startpunkt für Claude-Sitzungen sein.

### Schritt 1: Struktur anlegen

Die Ordnerstruktur aus [references/struktur.md](references/struktur.md) anlegen (kontext, projekte, notizen, wissen, vorlagen) und die `CLAUDE.md` als Startdatei schreiben. Kein Nutzer-Input nötig, still durchziehen und kurz bestätigen.

### Schritt 2: Onboarding-Interview

Sechs Fragen, **einzeln** gestellt, nie als Textwand. Der Nutzer darf jede überspringen ("überspringen" oder "alles überspringen" jederzeit möglich). Nach jeder Antwort direkt zur nächsten Frage, ohne Kommentar.

1. **Du**: Name, was du in einem Satz machst, wo du sitzt. Wie würde ein geschätzter Kollege dich beschreiben?
2. **Angebot**: Dein Hauptangebot, das Problem, das es löst, und wer kauft (Rolle, Branche, gern echte Beispiele).
3. **Warum du**: Warum wählen Kunden dich statt Alternativen? Dein Standpunkt, gern in den Worten deiner Kunden.
4. **Stimme**: Wie klingst du? Adjektive, typische Phrasen, No-Go-Wörter. Oder füge 1 bis 2 eigene Texte ein, dann wird die Stimme daraus gezogen.
5. **Jetzt**: Deine Top-1-bis-3-Prioritäten dieses Quartal und die aktiven Projekte (Name plus ein Satz reicht).
6. **Werkzeuge**: Wo leben Termine, Kunden, Texte und Zahlen wirklich? Und die 1 bis 2 größten Zeitfresser.

### Schritt 3: Zusätzliches Material

Nach den Fragen **immer** einmal fragen: "Gibt es Material, das ich auswerten soll? Dateien, Links (Website, LinkedIn-Profil als Text), ein Ordner, roher Text. Je mehr, desto persönlicher wird das System." Alles Gelieferte lesen (Dateien, Ordner per Auflistung, Links per Abruf, falls verfügbar) und die Fakten den Ziel-Dateien zuordnen.

### Schritt 4: Kontextdateien bauen

Die Kontextdateien nach den Vorlagen in [references/kontextdateien.md](references/kontextdateien.md) schreiben. Die entscheidende Regel:

**Echte Personalisierung, keine Formular-Gerüste.** Die Vorlagen zeigen nur die Abschnittsstruktur. Jeder Platzhalter wird durch echte Daten aus Interview und Material ersetzt. Abschnitte ohne Daten werden weggelassen, nie mit "TBD" gefüllt. Exakte Namen, Zahlen und Formulierungen des Nutzers verwenden, nichts paraphrasieren, nichts erfinden. Eine fertige Kontextdatei liest sich wie ein von einem Menschen geschriebenes Dokument.

Nur Dateien anlegen, für die es Inhalt gibt. Projekte aus Frage 5 als Ordner unter `projekte/` mit je einer `README.md` (Überblick, Stand, nächste Schritte).

### Schritt 5: Abschluss

Kurz zusammenfassen, was entstanden ist. Dann erklären, wie das System benutzt wird:

- **Claude Code oder Claude Desktop (Cowork)**: Sitzungen in diesem Ordner starten, die `CLAUDE.md` wird automatisch gelesen
- **Claude im Browser**: die Kontextdateien einem Projekt hinzufügen oder bei Bedarf einfügen
- Neuer Kontext kommt laufend dazu: "Sag einfach 'merk dir das im System', ich lege es in die richtige Datei"

Einen konkreten ersten Arbeitsvorschlag machen, passend zu den genannten Prioritäten.

## Betriebsart 2: Warten

Auf Zuruf ("räum auf", "was ist veraltet", "System-Check") die Wartungsroutine aus [references/wartung.md](references/wartung.md) fahren:

1. **Bestandsaufnahme**: alle Dateien des Systems auflisten, Struktur prüfen
2. **Veraltetes finden**: Datumsangaben, abgeschlossene Projekte, überholte Prioritäten und Preise aufspüren
3. **Lücken finden**: was das System über das Business immer noch nicht weiß, obwohl es oft gebraucht wird
4. **Duplikate und Widersprüche**: dieselbe Information in zwei Versionen
5. **Bericht zeigen, Nutzer entscheidet**: erst nach Freigabe ändern, archivieren (nach `notizen/archiv/`) oder löschen. Nie ungefragt löschen.

## Regeln

- Alles in einfachem Markdown. Keine Abhängigkeit von Obsidian, Notion oder einem bestimmten Programm. Wer sein System in Obsidian öffnen will, kann das, es sind ja nur Ordner und Markdown-Dateien.
- Datei- und Ordnernamen ohne Umlaute und Leerzeichen.
- Jede Kontextdatei trägt ein `Stand: JJJJ-MM-TT` im Kopf, damit Veraltetes auffindbar bleibt.
- Der Nutzer behält die Hoheit: Bei Wartung wird vorgeschlagen, nicht ungefragt gelöscht.

## Wofür dieser Skill nicht da ist

- Einzelne Arbeitsaufgaben (Posts, Angebote, Mails): dafür gibt es eigene Skills, die dieses System als Kontextquelle nutzen können
- Team-Wissensdatenbanken mit Rechteverwaltung
- Automatische Synchronisation zwischen Geräten (das erledigt der Nutzer über seinen eigenen Cloud-Ordner, wenn gewünscht)
