# Setup und Login-Strategien

## Option 1: Claude in Chrome (Chrome-Erweiterung)

Der einfachste Weg für Seiten, auf denen der Nutzer schon eingeloggt ist.

1. In Chrome die Erweiterung "Claude in Chrome" installieren (Chrome Web Store) und mit dem Claude-Konto anmelden. Verfügbarkeit hängt vom Claude-Plan ab.
2. In den Claude-Einstellungen die Browser-Nutzung erlauben.
3. Fertig: Claude sieht und bedient die Tabs, inklusive bestehender Logins.

Geeignet für: eingeloggte Portale, schnelle Einzelaufgaben. Weniger geeignet für lange Massenläufe.

## Option 2: agent-browser CLI

Das Kommandozeilen-Werkzeug für gründlichere Automatisierung, genutzt aus Claude Code oder Claude Desktop mit Terminal-Zugriff.

**Installation (einmalig):**

1. Voraussetzung Node.js: von nodejs.org die LTS-Version installieren (Standardeinstellungen). Prüfen im Terminal: `node --version`
2. Das Werkzeug installieren:
   ```bash
   npm install -g agent-browser
   ```
3. Browser bereitstellen (lädt bei Bedarf ein Chrome herunter; vorhandenes Chrome wird automatisch erkannt):
   ```bash
   agent-browser install
   ```
4. Test:
   ```bash
   agent-browser open https://example.com && agent-browser get title
   ```
   Erscheint der Seitentitel, ist alles bereit.

Aktualisieren später mit `agent-browser upgrade`.

## Login-Strategien (CLI)

Grundregel aus dem Skill: **Passwörter tippt der Nutzer selbst.** Die Strategien unten sorgen dafür, dass ein einmal gemachter Login wiederverwendet wird.

### A: Vorhandenes Chrome-Profil nutzen (kein Setup)

Der Nutzer ist in seinem Chrome bereits überall eingeloggt:

```bash
agent-browser profiles                     # verfügbare Profile anzeigen
agent-browser --profile Default open https://portal.beispiel.de
```

### B: Sitzungs-Name (automatisches Merken)

Für wiederkehrende Aufgaben auf derselben Seite:

```bash
agent-browser --session-name portal open https://portal.beispiel.de/login
# → Nutzer loggt sich im geöffneten Fenster selbst ein
agent-browser close                        # Sitzung wird gespeichert

# Beim nächsten Mal: automatisch wieder eingeloggt
agent-browser --session-name portal open https://portal.beispiel.de/übersicht
```

### C: Status-Datei (manuell speichern und laden)

```bash
# Nach dem Login des Nutzers:
agent-browser state save ./auth.json
# Später:
agent-browser state load ./auth.json
agent-browser open https://portal.beispiel.de/übersicht
```

**Achtung:** Solche Status-Dateien enthalten Sitzungs-Tokens im Klartext. Nicht teilen, nicht in Git einchecken, nach Projektende löschen. Dem Nutzer diesen Hinweis immer mitgeben.

### Zwei-Faktor-Authentifizierung

2FA-Codes gibt immer der Nutzer selbst ein. Ablauf: Claude navigiert bis zur 2FA-Abfrage, der Nutzer tippt den Code im sichtbaren Browserfenster, danach übernimmt Claude wieder. Mit Strategie B oder C bleibt die Sitzung danach meist mehrere Wochen gültig.

## Welcher Weg für wen

| Situation | Empfehlung |
|-----------|------------|
| Schnelle Aufgabe auf eingeloggter Seite | Claude in Chrome |
| Wiederkehrende Portal-Arbeit | CLI mit Sitzungs-Name |
| Daten-Extraktion mit vielen Seiten | CLI |
| Nutzer ohne Terminal-Erfahrung | Claude in Chrome, CLI nur mit Begleitung einrichten |
