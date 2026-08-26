---
name: angebot-erstellen
description: Erstellt aus Call-Notizen oder einem Transkript ein fertiges Angebot: Ausgangslage des Kunden, Zielbild, Leistungen mit Umfang, Zeitplan, Preis mit Begründung und nächste Schritte. Die Preislogik kommt aus einem einmaligen Onboarding. Nutze diesen Skill, wenn der User sagt "erstell ein Angebot", "Angebot schreiben", "Angebot für [Kunde]", "Proposal erstellen", "aus dem Call ein Angebot machen", "write a proposal", "create an offer", "draft a quote", "turn these notes into a proposal".
---

# Angebot erstellen

Du machst aus Gesprächsnotizen oder einem Transkript ein Angebot, das der Kunde versteht und unterschreiben will. Das Angebot argumentiert vom Problem des Kunden zur Lösung, nicht von der Leistungsliste zum Preis.

**Der Skill schlägt einen Preis vor und begründet ihn. Die Entscheidung trifft immer der Nutzer.**

## Wann dieser Skill greift

Nach einem Erstgespräch oder Bedarfsgespräch, wenn daraus ein schriftliches Angebot werden soll. Auch zum Überarbeiten bestehender Angebote.

## Konnektoren

Keine nötig. Optional:

- **Google Drive oder Notion**: zum Ablegen des fertigen Angebots. Ohne: Datei ins Arbeitsverzeichnis speichern, der Nutzer legt sie selbst ab.
- **Notetaker** (Fathom, Fireflies, tl;dv oder ähnliches): Wenn verbunden, das Transkript des relevanten Calls direkt holen. Ohne: Notizen oder Transkript einfügen lassen.

## Preislogik beim ersten Lauf

Prüfe, ob im Ordner dieses Skills eine Datei `preislogik.md` existiert.

**Wenn ja:** Lies sie und nutze sie für den Preisvorschlag.

**Wenn nein:** Führe das Onboarding durch, damit der Skill nie raten muss:

1. Wie bepreist du? (Stundensatz, Tagessatz, Festpreis pro Projekt, Pakete, monatliche Pauschale)
2. Die konkreten Zahlen: Stundensatz oder Satzspanne, typische Paketpreise, übliche Projektgrößen (kleinstes und größtes realistisches Projekt in Euro)
3. Was treibt den Preis nach oben? (Express, Komplexität, Abstimmungsaufwand, Anfahrt)
4. Gibst du Rabatte, und wenn ja, wofür? (Empfehlung: Rabatte nur gegen Gegenleistung, z. B. längere Laufzeit)
5. Zahlungsbedingungen: Anzahlung, Raten, Zahlungsziel
6. Gibt es Standard-Bausteine, die in fast jedem Angebot vorkommen? (z. B. Kickoff, Konzept, Umsetzung, Übergabe)

Speichere alles als `preislogik.md` im Ordner dieses Skills. Änderungen auf Zuruf ("aktualisiere meine Preislogik").

## Ablauf

### Schritt 1: Material aufnehmen

Notizen, Transkript oder Stichpunkte entgegennehmen. Daraus extrahieren:

- Ausgangslage und Problem des Kunden (mit Originalformulierungen, die der Kunde benutzt hat)
- Was der Kunde erreichen will, und bis wann
- Besprochener Umfang, Wünsche, Grenzen
- Budget-Signale, falls gefallen
- Offene Punkte

Lücken aktiv benennen: "Aus den Notizen geht nicht hervor, bis wann der Kunde live sein will. Weißt du es, oder soll das als offener Punkt ins Angebot?"

### Schritt 2: Eckpunkte bestätigen

Vor dem Schreiben eine Kurzfassung zeigen: Ausgangslage in 2 Sätzen, vorgeschlagene Leistungsbausteine, grober Zeitplan, Preisvorschlag mit Begründung aus der Preislogik ("[X] Stunden geschätzt bei [Satz], plus Puffer für [Risiko], macht [Summe]. Alternativ als Paket [Y]").

Der Nutzer bestätigt oder korrigiert Umfang und Preis. **Erst dann das Dokument schreiben.**

### Schritt 3: Angebot schreiben

Struktur und Formulierungsregeln aus [references/angebotsstruktur.md](references/angebotsstruktur.md). Kernpunkte:

- Die Ausgangslage in der Sprache des Kunden, damit er sich verstanden fühlt
- Leistungen mit klarem Umfang und klaren Grenzen (was ist NICHT enthalten)
- Preis transparent aufgeschlüsselt, mit Begründung statt nackter Zahl
- Zeitplan mit Meilensteinen
- Nächste Schritte so konkret, dass der Kunde nur noch zusagen muss
- Keine Floskeln, kein Behördendeutsch, keine zehn Seiten AGB-Prosa

### Schritt 4: Ausgeben und ablegen

Das Angebot als Markdown-Datei ins Arbeitsverzeichnis speichern (`angebot-[kunde]-[datum].md`, ohne Umlaute im Dateinamen). Auf Wunsch zusätzlich als Word-Dokument oder PDF, wenn die Umgebung das hergibt, oder in Google Drive/Notion ablegen, wenn verbunden.

Zum Abschluss 2 bis 3 Hinweise geben, was der Nutzer vor dem Versand prüfen sollte (Preis final?, rechtliche Angaben des eigenen Unternehmens, Gültigkeitsdatum).

## Ausgabeformat

Ein sauberes Dokument nach der Struktur in [references/angebotsstruktur.md](references/angebotsstruktur.md), plus im Chat die Kurzfassung mit Preisbegründung.

## Wofür dieser Skill nicht da ist

- Rechnungen (das ist Buchhaltung, kein Angebot)
- Rechtsberatung zu Vertragsklauseln (bei Bedarf auf Anwalt oder Vorlagen des Berufsverbands verweisen)
- Kaltakquise-Angebote ohne vorheriges Gespräch (dafür fehlt das Material; erst Gespräch, dann Angebot)
