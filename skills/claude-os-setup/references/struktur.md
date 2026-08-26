# Ordnerstruktur und Startdatei

## Die Struktur

```
[arbeitsordner]/
├── CLAUDE.md            Startdatei: wer der Nutzer ist, wie hier gearbeitet wird
├── kontext/             Das Wissen ueber das Business (aendert sich selten)
│   ├── ich.md
│   ├── business.md
│   ├── zielgruppe.md
│   ├── marke-stimme.md
│   ├── strategie.md
│   └── werkzeuge.md
├── projekte/            Ein Ordner pro aktivem Projekt
│   └── [projektname]/
│       └── README.md
├── notizen/             Arbeitsnotizen, Besprechungen, Tagesdateien
│   └── archiv/          Abgeschlossenes und Veraltetes
├── wissen/              Nachschlagematerial (Artikel, Recherchen, Vorlagen Dritter)
└── vorlagen/            Eigene wiederverwendbare Vorlagen (Mails, Angebote)
```

Regeln:

- Nur Ordner anlegen, die beim Setup auch Inhalt bekommen. `wissen/` und `vorlagen/` dürfen anfangs fehlen und entstehen bei Bedarf.
- Keine leeren Platzhalter-Dateien.
- Dateinamen klein, ohne Umlaute, mit Bindestrichen.

## Vorlage: CLAUDE.md

Beim Setup mit echten Daten füllen (Name, Tätigkeit, die wichtigsten Eigenheiten). Sie ist bewusst kurz: Sie verweist auf die Kontextdateien, statt sie zu duplizieren.

```markdown
# Arbeitssystem von [Name]

[Name] ist [Taetigkeit in einem Satz]. Dieses Verzeichnis ist das dauerhafte
Arbeitssystem: Kontext ueber das Business liegt in kontext/, laufende Arbeit
in projekte/, Notizen in notizen/.

## So arbeitest du hier

- Lies bei Aufgaben mit Business-Bezug zuerst die passende Datei aus kontext/
  (Angebot und Preise: business.md · Kunden: zielgruppe.md · Ton: marke-stimme.md).
- Neue dauerhafte Fakten ("merk dir das") gehoeren in die passende kontext/-Datei,
  mit aktualisiertem Stand-Datum. Kurzlebiges gehoert nach notizen/.
- Projektarbeit laeuft im jeweiligen Ordner unter projekte/. Die README.md dort
  ist der Index: Ueberblick, Stand, naechste Schritte aktuell halten.
- Abgeschlossenes nach notizen/archiv/ verschieben, nicht loeschen.
- Sprache: Deutsch. Ansprache: [du/Sie]. [Weitere Eigenheiten aus dem Interview.]

## Aktuelle Prioritaeten (Stand: JJJJ-MM-TT)

1. [Prioritaet 1]
2. [Prioritaet 2]
```

## Vorlage: projekte/[name]/README.md

```markdown
# [Projektname]

Stand: JJJJ-MM-TT · Status: aktiv

## Ueberblick
[Was das Projekt ist und wofuer, 2 bis 3 Saetze]

## Aktueller Stand
[Wo die Dinge stehen]

## Naechste Schritte
- [ ] [Schritt]
```

## Nutzung in den Claude-Umgebungen

- **Claude Code / Claude Desktop (Cowork)**: Sitzung im Arbeitsordner starten, `CLAUDE.md` wird automatisch geladen. Der Rest wird bei Bedarf gelesen.
- **Claude im Browser (claude.ai)**: die `kontext/`-Dateien in ein Projekt hochladen. Nach Änderungen die betroffene Datei neu hochladen.
- Der Ordner darf in einem Cloud-Verzeichnis liegen (Google Drive, OneDrive, Dropbox), dann ist er auf allen Geräten gleich.
