# Entscheidungs-Log-Konventionen

> Phasenübergreifende Regeln für die Dokumentation von Entscheidungen.
> Jede nicht-triviale Entscheidung wird einmal sauber dokumentiert — mit Begründung und verworfenen Alternativen. Das spart Stunden an "Warum haben wir das nochmal so gemacht?"-Diskussionen.

---

## Skalierung: Was braucht mein Projekt?

| Projektgröße | Empfohlene Elemente |
|---|---|
| **Klein** (wenige Entscheidungen) | Basis-Format, fortlaufende Nummerierung |
| **Mittel** (10-30 Entscheidungen) | Alles aus Klein + Kategorien, Querverweise zu Specs |
| **Groß** (30+ Entscheidungen) | Alles + Status-Tracking, Impact-Bewertung, Übersichtstabelle |

---

## Basis-Format

```markdown
### DEC-001 | YYYY-MM-DD | Session N | Titel

**Kontext:** Warum stand diese Entscheidung an?
**Entscheidung:** Was wurde entschieden
**Begründung:** Warum diese Option
**Alternativen verworfen:**
- Option B — warum nicht
- Option C — warum nicht
**Betroffene Specs:** Welche Docs/Files betroffen
```

### Pflichtfelder

| Feld | Immer? | Warum |
|------|--------|-------|
| **Kontext** | Ja | Ohne Kontext ist die Entscheidung in 2 Wochen nicht mehr nachvollziehbar |
| **Entscheidung** | Ja | Ein Satz, klar und eindeutig |
| **Begründung** | Ja | Das wichtigste Feld — "weil es besser ist" reicht nicht |
| **Alternativen verworfen** | Ja | Verhindert dass dieselbe Diskussion nochmal geführt wird |
| **Betroffene Specs** | Wenn zutreffend | Macht Auswirkungen sichtbar |

---

## Kern-Regeln

| # | Regel | Warum |
|---|-------|-------|
| 1 | **Fortlaufende Nummerierung** (DEC-001, DEC-002, ...) | Ermöglicht eindeutige Verweise aus Session-Log und Specs |
| 2 | **Chronologisch** — älteste oben, neueste unten | Entscheidungen bauen aufeinander auf, die Reihenfolge ist wichtig |
| 3 | **Nie löschen, nur ergänzen** | Wenn eine Entscheidung revidiert wird, bleibt die alte stehen + neue Entscheidung mit Verweis |
| 4 | **Verweise statt Kopien** | Im Session-Log steht "DEC-005 getroffen", die Details stehen nur hier |
| 5 | **Jede Entscheidung hat mindestens eine verworfene Alternative** | Wenn es keine Alternative gab, war es keine Entscheidung sondern eine Feststellung |

---

## Wann ist etwas eine "Entscheidung"?

| Situation | Entscheidung? | Beispiel |
|-----------|--------------|---------|
| Tech-Stack-Wahl | Ja | "PostgreSQL statt MongoDB" |
| Architektur-Grundsatz | Ja | "Monolith statt Microservices" |
| Feature in/out of Scope | Ja | "Kein Multi-Tenancy in V1" |
| Namensgebung (Tabelle, API-Route) | Nur bei Diskussion | "users statt accounts Tabelle" |
| Offensichtliches (z.B. .gitignore anlegen) | Nein | Das ist Handwerk, keine Entscheidung |
| Bug-Fix-Strategie | Selten | Nur wenn mehrere Lösungswege existierten |

**Faustregel:** Wenn jemand in 3 Monaten fragen könnte "Warum habt ihr das so gemacht?" — dann ist es eine Entscheidung.

---

## Entscheidungen revidieren

Entscheidungen können revidiert werden. Die alte Entscheidung bleibt bestehen, die neue referenziert sie:

```markdown
### DEC-012 | 2025-04-10 | Session 15 | Wechsel von REST zu GraphQL

**Kontext:** REST-API aus DEC-003 stößt an Grenzen bei verschachtelten Abfragen
**Entscheidung:** GraphQL für Client-facing API, REST für interne Services
**Begründung:** N+1-Problem bei Dashboard-Queries nicht performant lösbar
**Revidiert:** DEC-003 (REST für alle APIs)
**Alternativen verworfen:**
- REST mit Custom-Endpoints pro View — zu viele Endpoints, schwer wartbar
- GraphQL überall — Overkill für einfache interne Service-Kommunikation
**Betroffene Specs:** api-design.md, frontend-architektur.md
```

---

## Kategorien (ab mittleren Projekten)

Zur besseren Orientierung optional einen Kategorie-Tag im Titel:

| Kategorie | Verwendung |
|-----------|-----------|
| `[Architektur]` | Strukturelle Grundsatzentscheidungen |
| `[Tech]` | Tech-Stack, Libraries, Tools |
| `[Scope]` | Feature rein/raus, Priorisierung |
| `[Security]` | Sicherheitsrelevante Entscheidungen |
| `[Data]` | Datenmodell, DB-Schema, Storage |
| `[Process]` | Arbeitsweise, Workflows |

Beispiel: `DEC-007 | 2025-03-15 | Session 5 | [Security] JWT statt Session-Cookies`

---

## Übersichtstabelle (ab großen Projekten)

Am Anfang der Datei eine Schnellübersicht:

```markdown
## Übersicht

| ID | Datum | Kategorie | Titel | Status |
|----|-------|-----------|-------|--------|
| DEC-001 | 2025-03-01 | [Tech] | PostgreSQL als Datenbank | Aktiv |
| DEC-002 | 2025-03-01 | [Architektur] | Monolith-First | Aktiv |
| DEC-003 | 2025-03-05 | [Tech] | REST für alle APIs | Revidiert → DEC-012 |
```

Diese Tabelle macht es möglich, schnell zu sehen welche Entscheidungen noch gelten und welche überholt sind.

---

## Speicherort

```
docs/tracking/decisions.md
```

Eine Datei pro Projekt. Bei sehr großen Projekten (50+ Entscheidungen) kann nach Kategorie gesplittet werden, aber das ist selten nötig.

---

## Häufige Fehler

| Fehler | Problem | Besser |
|--------|---------|--------|
| Keine Alternativen dokumentiert | Gleiche Diskussion wird wiederholt | Mindestens eine Alternative mit Begründung |
| "Weil es besser ist" als Begründung | Nicht nachvollziehbar | Konkrete Kriterien: Performance, Wartbarkeit, Zeitaufwand |
| Entscheidungen nur im Session-Log | Nicht auffindbar | Session-Log verweist auf DEC-XXX, Details stehen hier |
| Triviales als Entscheidung | Register wird unübersichtlich | Nur dokumentieren wenn es eine echte Wahl gab |
| Alte Entscheidungen löschen | Geschichte geht verloren | Status auf "Revidiert" setzen, neue Entscheidung anlegen |
