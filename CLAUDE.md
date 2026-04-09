# prompt-lib — Projektregeln

> Dieses Repo ist eine Sammlung von Prompt-Templates und Anleitungen für verschiedene Projektphasen.
> Templates werden bei Bedarf in neue Projekte kopiert und dort angepasst.

---

## Ordnerstruktur

```
prompt-lib/
├── CLAUDE.md              ← Dieses File: Regeln fürs Repo
├── bootstrap.md           ← Starter-Anleitung für neue Projekte
├── exploration/           ← Templates für die Explorations-/Discovery-Phase
├── doku-phase/            ← Templates für die Konzept-/Dokumentationsphase
├── code-phase/            ← Templates für die Implementierungsphase
├── forms/                 ← Formulare & Wizards (phasenübergreifend)
├── testing/               ← Templates für Testing-Strategien
├── deployment/            ← Templates für Deployment & Infrastruktur
├── maintenance/           ← Templates für Wartung & Refactoring
├── shared/                ← Phasenübergreifende Regeln (Git, Naming, Tracking)
├── notes/                 ← LOKAL — wird nicht gepusht (gitignored)
│   ├── meta.notes.md      ← Entstehungskontext, Struktur-Entscheidungen
│   └── *.notes.md         ← Pro Template-File ein Notes-File
└── .gitignore
```

---

## Arbeitsregeln

| # | Regel |
|---|-------|
| 1 | **Docs auf Deutsch, Dateinamen auf Englisch/Deutsch mit Bindestrichen** |
| 2 | **Nie ohne Rückfrage ändern** — bestehende Templates nie eigenmächtig umschreiben |
| 3 | **Jedes Template ist eigenständig lesbar** — keine impliziten Abhängigkeiten zu anderen Files |
| 4 | **Skalierung einbauen** — Templates enthalten Empfehlungen wann welcher Teil relevant ist (Klein/Mittel/Groß) |
| 5 | **Notes-Dateien pflegen** — Zu jedem Template gehört ein Notes-File in `notes/` mit Entstehungskontext und Weiterentwicklungs-Hinweisen |

---

## Namenskonventionen

| Element | Konvention | Beispiel |
|---------|-----------|---------|
| Ordner | Lowercase, Bindestriche | `doku-phase/` |
| Template-Files | `{thema}.md` | `doku-phase-anleitung.md` |
| Notes-Files | `{template-name}.notes.md` | `doku-phase-anleitung.notes.md` |
| Phasenübergreifend | In `shared/` ablegen | `shared/git-konventionen.md` |

---

## Wie Templates entstehen

1. **Bedarf erkennen** — Welche Phase/welcher Kontext braucht ein Template?
2. **Bestehendes prüfen** — Gibt es schon ein Template das erweitert werden kann?
3. **Template schreiben** — Eigenständig, mit Skalierung, praxisnah
4. **Notes-File anlegen** — Entstehungskontext, Quellen, Überlegungen
5. **CLAUDE.md prüfen** — Muss die Strukturbeschreibung aktualisiert werden?

---

## Kontext

Ausführliche Informationen zur Entstehung dieses Repos, verworfenen Alternativen und Struktur-Entscheidungen → `notes/meta.notes.md` (lokal, nicht im Repo).
