# HTML-Ausgabe: Regeln

Wenn der Nutzer Option B (eigenständiges HTML) wählt, baue eine einzelne HTML-Datei, die die Infografik pixelgenau darstellt.

## Technische Vorgaben

- **Eine Datei, alles inline.** Kein externes CSS, keine CDN-Links, keine externen Bilder. Die Datei muss offline im Browser funktionieren.
- **Feste Leinwand:** ein Container mit exakt 1080 x 1350 px (Format 4:5), zentriert auf neutralem Seitenhintergrund. Für andere Formate (1:1, 16:9) die Maße anpassen, wenn der Nutzer es sagt.
- **Schrift:** die Hausschrift aus `profil.md` als `font-family` mit Fallback auf eine Systemschrift (`system-ui, -apple-system, 'Segoe UI', sans-serif`). Keine Webfont-Einbindung von externen Servern; wenn die Hausschrift lokal nicht installiert ist, greift der Fallback.
- **Farben:** ausschließlich die Werte aus `profil.md`. Als CSS-Variablen am Anfang definieren (`--primary`, `--accent`, `--bg`, `--text`), damit der Nutzer sie leicht ändern kann.
- **Icons:** einfache Inline-SVGs oder Unicode-Symbole (Haken, Kreuz, Pfeil). Keine Icon-Fonts, keine externen Icon-Bibliotheken. Emojis nur, wenn das Profil sie erlaubt.
- **Diagramme:** Balken und Linien als reine HTML/CSS-Elemente oder Inline-SVG bauen, keine Chart-Bibliotheken.

## Gestaltungsregeln

- Großzügiger Weißraum: Innenabstand der Leinwand mindestens 60 px.
- Klare Hierarchie: Headline deutlich größer als alles andere, danach maximal zwei weitere Schriftgrößen.
- Kontrast prüfen: Text muss auf seinem Hintergrund gut lesbar sein, auch verkleinert im LinkedIn-Feed.
- Die Slots des gewählten Layouts exakt umsetzen, nichts dazürfinden.
- Footer-Zeile aus `profil.md` unten einbauen, falls definiert.

## Übergabe an den Nutzer

1. Datei im Arbeitsverzeichnis speichern, Dateiname ohne Umlaute und Leerzeichen: `infografik-JJJJ-MM-TT-thema.html`.
2. Dem Nutzer in zwei Sätzen erklären: Datei im Browser öffnen, dann per Screenshot oder Druckfunktion als Bild sichern. Auf Windows: Browserfenster auf die Grafik zoomen und mit dem Snipping Tool (Win + Shift + S) den Leinwand-Container abfotografieren.
3. Anbieten, Farben, Texte oder Layout direkt in der Datei anzupassen.
