# Git-Konventionen

> Phasenübergreifende Regeln für Versionskontrolle mit Git.
> Gelten ab der ersten Session — unabhängig davon ob Code oder Docs bearbeitet werden.

---

## Skalierung: Was braucht mein Projekt?

| Projektgröße | Empfohlene Elemente |
|---|---|
| **Klein** (Solo, 1-5 Files) | Commit-Format, .gitignore-Basis |
| **Mittel** (Solo/Team, 5-20 Files) | Alles aus Klein + Branch-Strategie, Tag-Konventionen |
| **Groß** (Team, 20+ Files, CI/CD) | Alles + PR-Regeln, geschützter Main-Branch, Release-Tags |

---

## Commit-Format

```
<typ>: <was wurde gemacht>

<warum — optional aber empfohlen bei nicht-offensichtlichen Änderungen>
```

### Typen

| Typ | Verwendung | Beispiel |
|-----|-----------|---------|
| `docs` | Specs, Konzepte, Tracking-Files | `docs: DB-Schema-Spec fertiggestellt` |
| `feat` | Neue Funktionalität | `feat: User-Registration Endpoint` |
| `fix` | Bugfix | `fix: Timeout bei Webhook-Retry korrigiert` |
| `refactor` | Code-Umstrukturierung ohne Verhaltensänderung | `refactor: Auth-Middleware extrahiert` |
| `test` | Tests hinzugefügt oder geändert | `test: Integration-Tests für Payment-Flow` |
| `chore` | Build, Config, Dependencies | `chore: Node-Version auf 20 aktualisiert` |
| `style` | Formatierung, keine Code-Änderung | `style: Einrückung in Config-Files vereinheitlicht` |

### Regeln

- Erste Zeile: max. 72 Zeichen, Imperativ ("hinzufügen" nicht "hinzugefügt")
- Kein Punkt am Ende der ersten Zeile
- Leerzeile zwischen Titel und Body
- Body erklärt das **Warum**, nicht das **Was** (das sieht man im Diff)
- Pro Commit ein logischer Schritt — nicht 5 unabhängige Änderungen bündeln

---

## Branch-Strategie

### Für kleine Projekte (Solo)

Direkt auf `main` arbeiten ist akzeptabel, solange regelmäßig committet wird.

### Für mittlere/große Projekte

| Branch | Zweck | Lebensdauer |
|--------|-------|-------------|
| `main` | Stabiler Stand, jederzeit deploybar | Permanent |
| `feat/<name>` | Neues Feature | Bis Merge in main |
| `fix/<name>` | Bugfix | Bis Merge in main |
| `docs/<name>` | Dokumentations-Änderungen | Bis Merge in main |

**Regeln:**
- Branch-Namen: Lowercase, Bindestriche, beschreibend (`feat/user-registration`, nicht `feat/feature1`)
- Branches leben kurz — je länger ein Branch offen ist, desto schmerzhafter der Merge
- Vor dem Merge: Rebase auf aktuellen `main`, nicht Merge-Commits anhäufen

---

## .gitignore-Basis

Mindestinhalt für jedes Projekt:

```gitignore
# Secrets
.env
.env.*
!.env.example

# Lokale Notizen
notes/

# OS
.DS_Store
Thumbs.db

# IDE
.idea/
.vscode/
*.swp
```

Projektspezifisch erweitern (Build-Artefakte, Dependencies, etc.).

---

## Tag-Konventionen

Ab mittleren Projekten: Meilensteine mit Tags markieren.

```
v0.1.0    ← Erste funktionsfähige Version
v1.0.0    ← Erster Release
v1.1.0    ← Neues Feature
v1.0.1    ← Bugfix
```

**Schema:** `v<major>.<minor>.<patch>` (Semantic Versioning)

- **Major:** Breaking Changes oder grundlegende Architektur-Änderung
- **Minor:** Neue Features, abwärtskompatibel
- **Patch:** Bugfixes

**Doku-Phase-Meilensteine** (optional):

```
docs/v1    ← Konzeptphase abgeschlossen
docs/v2    ← Nach erster Corrigendum-Session
```

---

## PR-Regeln (ab Team-Arbeit)

| Regel | Warum |
|-------|-------|
| Jeder PR hat eine Beschreibung die das **Warum** erklärt | Code-Review ohne Kontext ist Zeitverschwendung |
| PRs sind klein und fokussiert | Große PRs werden nicht gründlich reviewt |
| Mindestens ein Review vor Merge | Vier-Augen-Prinzip |
| CI muss grün sein vor Merge | Kein Raten ob Tests noch laufen |
| Kein Force-Push auf `main` | History-Rewriting auf shared Branches = Chaos |

---

## Wann committen?

| Situation | Commit? |
|-----------|---------|
| Spec fertig geschrieben | Ja |
| Arbeitstag-Ende, Spec noch in Arbeit | Ja — mit `docs: WIP <thema>` |
| Feature implementiert und getestet | Ja |
| "Mal kurz was ausprobiert" | Nein — erst wenn es einen klaren Stand gibt |
| Session-Log aktualisiert | Ja — kann mit dem inhaltlichen Commit zusammen |

**Faustregel:** Lieber ein Commit zu viel als einer zu wenig. Commits sind billig, verlorene Arbeit nicht.
