# Massnahmen-Katalog für KI-Sichtbarkeit

Aus diesem Katalog den Plan zusammenstellen, passend zu den Lücken aus dem Check. Grundprinzip: KIs zitieren, was sie lesen, verstehen und für vertrauenswürdig halten. Für Menschen schreiben, klar strukturieren, das reicht in den meisten Fällen.

## Stufe 1: Sofort umsetzbar (unter 1 Stunde)

### Klare Selbstbeschreibung auf der Startseite

Der wichtigste Einzelhebel. Ein Absatz im Muster: "[Unternehmen] ist [was] in [wo] für [wen]. Wir helfen bei [Kernproblem] durch [Leistung]." KIs übernehmen solche Definitionssätze fast wörtlich. Vage Slogans ("Ihr Partner für Lösungen") sind für KIs unbrauchbar.

### llms.txt anlegen

Eine einfache Textdatei unter `deinedomain.de/llms.txt`, die KIs einen Überblick gibt: was das Unternehmen macht, für wen, Kernleistungen, Preisrahmen, Kontakt, wichtigste Seiten. Vorlage: [llms-txt-vorlage.md](llms-txt-vorlage.md). Hochladen wie jede andere Datei, der Webdesigner oder das CMS-Dateimanagement erledigt das in Minuten.

### Google-Unternehmensprofil prüfen

Für alle mit regionalem Bezug Pflicht: Kategorien korrekt, Leistungen gepflegt, Öffnungszeiten aktuell, Fotos vorhanden. Google-KI-Antworten und Gemini ziehen stark aus dem Unternehmensprofil.

### KI-Crawler nicht aussperren

In der `robots.txt` prüfen, ob GPTBot, ClaudeBot, PerplexityBot oder Google-Extended blockiert sind. Wer blockiert, kann nicht zitiert werden. Im Zweifel: nichts blockieren.

## Stufe 2: Diese Woche

### Eine Seite pro Kernfrage

Für jede wichtige Frage aus dem Check, die die Website nicht beantwortet, eine eigene Seite oder einen Artikel: Die Frage ist die Überschrift, die Antwort steht in den ersten Sätzen, danach Details.

Die zwei wirksamsten Themen, weil sie fast niemand ehrlich beantwortet:

- **Kostenseite**: echte Preisspannen mit Einflussfaktoren. "Eine [Leistung] kostet bei uns je nach [Faktor] zwischen X und Y Euro." Wer keine Preise nennt, überlässt Kostenfragen den Portalen.
- **Ablaufseite**: wie eine Zusammenarbeit läuft, vom Erstkontakt bis zum Ergebnis, als nummerierte Schritte.

### FAQ-Block mit echten Kundenfragen

5 bis 10 Fragen, wie Kunden sie wirklich formulieren, mit direkten Antworten in 2 bis 4 Sätzen. Auf der Startseite oder als eigene Seite. FAQ-Blöcke sind das am leichtesten extrahierbare Format für KIs.

### Extrahierbar strukturieren

Bestehende Kernseiten nach diesen Regeln prüfen:

- Jede wichtige Antwort als eigenständiger Absatz von 40 bis 60 Wörtern, verständlich ohne den Text drumherum
- Zwischenüberschriften, die wie Suchfragen klingen
- Vergleiche als Tabelle, Abläufe als nummerierte Liste
- Zahlen, Daten und Namen statt Adjektive; ein Aktualisierungsdatum an Ratgeberseiten

### Strukturierte Daten (Schema)

Wenn CMS oder Webdesigner es hergeben: FAQ-Schema für den FAQ-Block, LocalBusiness- oder Organization-Schema mit Name, Ort, Leistungen. Die meisten CMS haben Plugins dafür. Hilfreich, aber kein Ersatz für gute Inhalte, deshalb Stufe 2, nicht Stufe 1.

## Stufe 3: Laufend

### Präsenz dort, wo KIs nachschlagen

KIs zitieren häufig Drittquellen statt der eigenen Website: Bewertungsportale, Branchenverzeichnisse, Foren, Presse. Deshalb:

- Bewertungen aktiv sammeln (Google, branchenrelevante Portale), auf Bewertungen antworten
- Einträge in den 2 bis 3 wichtigsten Branchenverzeichnissen pflegen, mit konsistenter Beschreibung (gleicher Name, gleiche Leistungsbeschreibung wie auf der Website)
- Wo es passt: Fachbeiträge in Branchenmedien, ehrliche Beteiligung in Foren und Communities. Keine Fake-Einträge, kein Spam: Das fliegt auf und schadet

### Aktualität zeigen

KIs bevorzugen frische Quellen. Ratgeberseiten mit sichtbarem Datum versehen und ein- bis zweimal im Jahr durchgehen: Zahlen aktualisieren, Veraltetes streichen.

### Wiederholungs-Check

Alle 4 bis 8 Wochen dieselben Testfragen stellen und die Ergebnistabelle vergleichen. Sichtbarkeit in KI-Antworten baut sich über Wochen auf, nicht über Nacht.

## Was NICHT tun

- **Keine Texte "extra für die KI" schreiben**: Doppelte Inhalte und Keyword-Massen schaden auch bei KIs. Ein Text, gut für Menschen, klar strukturiert.
- **Keine Statistiken oder Bewertungen erfinden**: KIs verknüpfen Quellen, Widersprüche fallen auf.
- **Nicht alles hinter Kontaktformulare sperren**: Was eine KI nicht lesen kann (Login, "Preis auf Anfrage", reine Bild-PDFs), kann sie nicht zitieren.
- **Nicht auf Tools und Tricks warten**: Die Basis (Selbstbeschreibung, Kosten, Ablauf, FAQ, Verzeichnisse) bringt den Großteil der Wirkung.
