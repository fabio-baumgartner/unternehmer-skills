# Unternehmer-Skills

**Das KI-Mitarbeiter Starter-Kit: 23 deutsche Claude Skills für Selbständige, Freelancer, Berater und kleine Unternehmen.**

Jeder Skill funktioniert eigenständig, fragt beim ersten Einsatz selbst ab, was er über dein Business wissen muss (Onboarding statt Konfiguration), und arbeitet auch ohne verbundene Konnektoren weiter. Kein technisches Vorwissen nötig.

## Installation

**In der Claude Desktop App (empfohlen, ohne Terminal):**

1. [Claude Desktop App](https://claude.ai/download) öffnen
2. **Einstellungen** → **Plugins**
3. Oben rechts **Add** → **Add marketplace**
4. Diese URL einfügen und auf **Sync** klicken: `https://github.com/fabio-baumgartner/unternehmer-skills`
5. **Unternehmer skills** in der Plugin-Liste installieren, neuen Chat starten

**Alternativ per Terminal ([Claude Code](https://claude.com/claude-code)):**

```
claude plugin marketplace add fabio-baumgartner/unternehmer-skills
```

```
claude plugin install unternehmer-skills@unternehmer-skills
```

Danach eine neue Sitzung starten. Die Skills laden automatisch, sobald eine passende Aufgabe kommt, du musst keine Skill-Namen kennen.

**Updates holen:** in der App beim Marketplace auf **Sync** klicken, im Terminal:

```
claude plugin marketplace update unternehmer-skills
```

## Erste Schritte

Probier zuerst diese drei:

1. **"Morning Briefing"**: deine Tagesübersicht mit Terminen, Mails und Aufgaben
2. **"Schreib einen LinkedIn-Post über [dein Thema]"**: von der Idee bis zum Hook
3. Text einfügen und **"Klingt das nach KI?"**: Scorecard mit konkreten Verbesserungen

## Die 23 Skills

### Strategie & Content
| Skill | Ein Satz |
|---|---|
| content-strategie | Themenideen sammeln, priorisieren, in Content-Pillars bündeln, Themenplan ausgeben |
| linkedin-post-schreiben | Interaktiv von der Idee zum Post, mit Framework-Wahl und Hook-Bibliothek |
| infografik-erstellen | Text rein, Layout aus dem Katalog, raus kommt ein Design-Tool-Prompt oder HTML |
| newsletter-schreiben | Schrittweise vom Aufhänger zur Ausgabe, mit begründeten Betreffzeilen-Varianten |
| seo-artikel-schreiben | Suchintention klären, Gliederung abstimmen, Artikel plus Meta-Angaben |
| ki-sichtbarkeit | Prüfen, ob das Unternehmen in KI-Antworten auftaucht, plus Maßnahmenplan |
| website-copy | Homepage, Landingpage, Preisseite, Über-uns nach deutschem Regelwerk |

### Vertrieb
| Skill | Ein Satz |
|---|---|
| lead-qualifizierung | Leads gegen ein gespeichertes Wunschkunden-Profil bewerten, aus Datei oder CRM |
| call-vorbereitung | Einseitiges Briefing mit Aufhängern, Einwänden und Fragen, fünf Minuten vor dem Call |
| angebot-erstellen | Aus Call-Notizen ein Angebot mit begründetem Preis aus der eigenen Preislogik |
| call-nachbereitung | Transkript holen, Zusammenfassung, To-dos und Follow-up-Mail liefern |
| case-study-erstellen | Kundengeschichte gemeinsam entwickeln, Abschnitt für Abschnitt bestätigt |

### Betrieb & Alltag
| Skill | Ein Satz |
|---|---|
| morning-briefing | Scanbare Tagesübersicht: Termine, Antwort-Mails, Aufgaben, Liegengebliebenes |
| posteingang-sortieren | Posteingang in vier Gruppen sortieren, Antwortentwürfe für Dringendes |
| prozess-interview | Bohrendes Interview, bis ein Prozess lückenlos ist, Ergebnis als SOP oder Skill |
| de-slop | Text gegen deutschen KI-Muster-Katalog prüfen, Scorecard mit Vorschlägen |

### Claude besser nutzen
| Skill | Ein Satz |
|---|---|
| claude-os-setup | Ordnerstruktur plus Kontextdateien, damit Claude das Business kennt |
| skill-erstellen | Aus Chatverlauf, Beschreibung oder SOP einen vollständigen Skill bauen |
| refresh | Übergabe-Dokument für den frischen Chat statt /compact |
| prompt-verbessern | Rohe Idee rein, fertiger Prompt fürs Zieltool raus |

### Automatisierung & Technik
| Skill | Ein Satz |
|---|---|
| n8n-workflow-bauen | Workflows als Import-JSON oder direkt deployt und getestet |
| mcp-server-bauen | Aus einer API-Doku ein funktionierender MCP-Server samt Installation |
| browser-agent | Claude bedient Websites ohne Schnittstelle: Formulare, Daten, Screenshots |

## Onboarding und deine Daten

Viele Skills fragen beim ersten Lauf nach deinem Kontext (Zielgruppe, Angebot, Tonalität, Preise) und speichern die Antworten als lokale Profildateien in ihrem Skill-Ordner. Alles bleibt auf deinem Rechner. Ändern geht jederzeit mit einem Satz wie "aktualisiere mein Voice-Profil".

Konnektoren (Gmail, Kalender, CRM, Notetaker) sind optional: Jeder Skill sagt dir höchstens, welcher ihn besser machen würde, und arbeitet sonst mit manueller Eingabe weiter. Einzige Ausnahme ist posteingang-sortieren, das Gmail oder Outlook braucht.

## Aufbau

```
.claude-plugin/
  plugin.json          Plugin-Metadaten
  marketplace.json     Marketplace-Eintrag (Repo ist Plugin und Marketplace zugleich)
skills/
  <skill-name>/
    SKILL.md           Ablauf des Skills
    references/        Nachschlagematerial, das der Skill bei Bedarf lädt
```

## Lizenz

Kostenlos für private und kommerzielle Nutzung, anpassen für den eigenen Gebrauch erlaubt. Weiterverkauf und Weiterverteilung als eigenes Produkt sind nicht erlaubt. Details: [LICENSE.md](LICENSE.md)

## Hilfe beim Setup

Ein kurzer 20-Minuten-Call reicht, um alles gemeinsam aufzusetzen: [cal.com/fabiobaumgartner/erstgespraech](https://cal.com/fabiobaumgartner/erstgespraech)
