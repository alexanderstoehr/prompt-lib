# Bootstrap: Neues Projekt aufsetzen

> Schritt-für-Schritt-Anleitung für den Start eines neuen Projekts.
> Wird einmalig am Anfang durchlaufen — danach übernehmen die phasenspezifischen Templates.

---

## Schritt 1: Projektordner & Git

```bash
mkdir projekt-name
cd projekt-name
git init
```

---

## Schritt 2: Ordnerstruktur anlegen

```
projekt-name/
├── docs/
│   ├── specs/          ← Konzept-Docs (Source of Truth für alle Features)
│   ├── tracking/       ← Session-Log, Changelog, Decisions, Problems
│   ├── guides/         ← How-To-Docs (entstehen beim Coden)
│   └── archive/        ← Unveränderte Kopie der Original-Docs aus der Konzeptphase
├── .gitignore
└── CLAUDE.md
```

---

## Schritt 3: Tracking-Files anlegen

Diese Files werden ab der ersten Session geführt:

| File | Zweck |
|------|-------|
| `docs/tracking/session-log.md` | Chronologisches Protokoll jeder Session (reverse-chronologisch, neueste oben) |
| `docs/tracking/changelog.md` | Pro geänderte Datei: was und warum |
| `docs/tracking/decisions.md` | Jede Entscheidung mit Begründung + verworfenen Alternativen |
| `docs/tracking/problems-solutions.md` | Aufgetretene Probleme + Lösungen |

### Vorlagen

**session-log.md:**
```markdown
# Session-Log

### Session 1 | YYYY-MM-DD | Thema

**Ergebnis:** Was wurde erreicht
**Geänderte Files:** Liste aller bearbeiteten Dateien
**Entscheidungen:** Welche Entscheidungen wurden getroffen (mit Verweis auf DEC-XXX)
**Offene Punkte:** Was muss noch geklärt werden
**Nächste Schritte:** Konkrete nächste Aktion für die Folgesession
```

**decisions.md:**
```markdown
# Entscheidungs-Register

### DEC-001 | YYYY-MM-DD | Session 1 | Titel

**Kontext:** Hintergrund
**Entscheidung:** Was wurde entschieden
**Begründung:** Warum diese Entscheidung
**Alternativen verworfen:** Was wurde nicht gewählt und warum
**Betroffene Specs:** Welche Docs betroffen
```

---

## Schritt 4: CLAUDE.md erstellen

Die CLAUDE.md ist das zentrale Regelwerk das Claude Code in jeder Session lädt. Mindestinhalt:

```markdown
# Projektname — Projektregeln

## Grundprinzipien
1. Nie ohne Rückfrage ändern
2. Qualität vor Geschwindigkeit
3. Alles dokumentieren
4. Docs auf Deutsch, Code auf Englisch

## Ordnerstruktur
[Ordnerstruktur des Projekts]

## Dokumentationspflicht
[Welche Tracking-Files wann aktualisiert werden]

## Git-Konventionen
[Commit-Format, Branch-Strategie]
```

Erweitern je nach Projektphase — siehe phasenspezifische Templates.

---

## Schritt 5: Scratchpad anlegen

```markdown
# Offene Notizen

## 📌 Noch zu klären
[Offene Fragen mit vollem Kontext]

## 📝 Notizen
[Arbeitsnotizen, Gedankenstützen]

## ✅ Geklärt (Archiv)
[Finalisierte Entscheidungen — hierher verschoben wenn geklärt]
```

Speicherort: `docs/tracking/notizen-offen.md` oder `docs/specs/notizen-offen.md` — je nach Präferenz.

---

## Schritt 6: Projekt-Struktur-Datei anlegen

Ab mittleren Projekten (5+ Specs) eine zentrale Registratur anlegen:

```markdown
# Projekt-Struktur

## File-Register
| File | Status | Abhängigkeiten | Beschreibung |
|------|--------|---------------|--------------|
| db-schema.md | ⏳ blockiert | db-entscheidungen.md | Vollständiges DB-Schema |

## Arbeitsreihenfolge
1. [Erstes File — keine Abhängigkeiten]
2. [Zweites File — abhängig von 1]
3. ...
```

---

## Schritt 7: .gitignore

Mindestinhalt:

```
.env
.env.*
notes/
```

Projektspezifisch erweitern (IDE-Files, Build-Artefakte, etc.).

---

## Welche Templates aus der prompt-lib kopieren?

| Projektgröße | Empfohlene Templates |
|---|---|
| **Klein** (1-5 Specs) | `doku-phase/doku-phase-anleitung.md` (Kern-Elemente nutzen) |
| **Mittel** (5-15 Specs) | Doku-Phase-Anleitung + `shared/` Regeln |
| **Groß** (15+ Specs) | Voller Umfang aller relevanten Phasen-Templates |

Templates werden **kopiert und angepasst**, nicht verlinkt — jedes Projekt ist eigenständig.

---

## Erste Session starten

Nach dem Bootstrap:
1. Session-Log-Eintrag für Session 1 schreiben
2. Mit der Doku-Phase beginnen (falls Konzeptphase) oder direkt coden (falls kleines Projekt)
3. Doku-Phase-Anleitung als Leitfaden verwenden
