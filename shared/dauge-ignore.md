# .daugeIgnore — Konventionen

> Steuert welche Dateien Dauge in den Playbook-Index aufnimmt.
> Dauge fetcht standardmäßig alle `.md`-Dateien im Repo — `.daugeIgnore` schließt alles aus, was kein Playbook ist.

---

## Wann brauche ich einen Eintrag?

Eine Datei gehört in `.daugeIgnore`, wenn sie **kein Dauge-Playbook** ist — also keinen YAML-Frontmatter mit `name`, `command` und `phase` hat.

Typische Kandidaten:
- Repo-Meta-Dateien (`README.md`, `CLAUDE.md`, `.gitignore`)
- Starter-Anleitungen (`bootstrap.md`)
- Konventions-Docs ohne Playbook-Charakter (dieser Ordner: `shared/`)
- Lokale Notizen (`notes/`)

---

## Syntax

```
# Kommentare mit #

# Einzelne Dateien
README.md
CLAUDE.md

# Ordner (trailing slash — schließt alles darin aus)
notes/
shared/

# Glob-Patterns
*.draft.md
**/intern.md
```

**Regeln:**
- Eine Regel pro Zeile
- `#` = Kommentar
- Trailing `/` = ganzer Ordner inklusive aller Unterordner
- `*` = beliebige Zeichen im Dateinamen
- `**/` = rekursiv in allen Unterordnern
- Pfade sind relativ zum Repo-Root

---

## Aktueller Stand

Folgende Dateien/Ordner sind ausgeschlossen (Stand: siehe `.daugeIgnore` im Root):

| Pfad | Grund |
|------|-------|
| `README.md` | Repo-Übersicht, kein Playbook |
| `CLAUDE.md` | Claude-Projektregeln, kein Playbook |
| `.gitignore` | Repo-Konfiguration |
| `.daugeIgnore` | Dauge-Konfiguration |
| `bootstrap.md` | Einmalige Starter-Anleitung, kein Playbook |
| `shared/` | Konventions-Docs ohne Playbook-Frontmatter |
| `notes/` | Lokale Notizen, nicht im Repo |

---

## Neue Dateien anlegen

**Ist es ein Playbook?** → YAML-Frontmatter anlegen, **nicht** in `.daugeIgnore` eintragen.

**Ist es kein Playbook?** → In `.daugeIgnore` eintragen, kein Frontmatter nötig.
