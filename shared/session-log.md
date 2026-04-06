# Session-Log-Konventionen

> Phasenübergreifende Regeln für das Führen von Session-Logs.
> Das Session-Log ist der rote Faden zwischen Arbeitssitzungen — es stellt sicher, dass keine Session ohne Kontext startet und keine Entscheidung verloren geht.

---

## Skalierung: Was braucht mein Projekt?

| Projektgröße | Empfohlene Elemente |
|---|---|
| **Klein** (1-5 Sessions erwartet) | Basis-Format, Append-Only-Regel |
| **Mittel** (5-20 Sessions) | Alles aus Klein + Entscheidungs-Verweise (DEC-XXX), Nächste-Schritte-Pflicht |
| **Groß** (20+ Sessions) | Alles + Session-Typen kennzeichnen, Meilenstein-Markierungen |

---

## Basis-Format

```markdown
### Session N | YYYY-MM-DD | Thema

**Ergebnis:** Was wurde erreicht
**Geänderte Files:** Liste aller bearbeiteten Dateien
**Entscheidungen:** Welche Entscheidungen wurden getroffen (mit Verweis auf DEC-XXX)
**Offene Punkte:** Was muss noch geklärt werden
**Nächste Schritte:** Konkrete nächste Aktion für die Folgesession
```

### Pflichtfelder

| Feld | Immer? | Warum |
|------|--------|-------|
| **Ergebnis** | Ja | Ohne Ergebnis war die Session nicht produktiv — oder das Ergebnis wurde nicht erkannt |
| **Geänderte Files** | Ja | Macht Diffs nachvollziehbar, verhindert vergessene Änderungen |
| **Entscheidungen** | Wenn welche gefallen sind | Entscheidungen ohne Dokumentation sind wertlos |
| **Offene Punkte** | Wenn welche existieren | Verhindert dass Fragen still verschwinden |
| **Nächste Schritte** | Ja | Das wichtigste Feld — ohne das fängt die nächste Session bei Null an |

---

## Kern-Regeln

| # | Regel | Warum |
|---|-------|-------|
| 1 | **Reverse-chronologisch** — neueste Session oben | Aktueller Stand sofort sichtbar, kein Scrollen nötig |
| 2 | **Append-Only** — Einträge werden nie rückwirkend geändert | Nachvollziehbarkeit geht sonst verloren |
| 3 | **Jede Session bekommt einen Eintrag** | Auch "nur gelesen" oder "nur geprüft" ist ein Ergebnis |
| 4 | **Nächste Schritte sind konkret** | "Weiter an Feature X arbeiten" ist zu vage. Besser: "API-Endpoint für User-Registration implementieren" |
| 5 | **Eintrag am Ende der Session schreiben** | Nicht am Anfang der nächsten — da fehlt der Kontext schon |

---

## Session-Typen (ab mittleren Projekten)

Zur besseren Orientierung im Log kann das Thema einen Typ-Prefix bekommen:

| Prefix | Bedeutung | Beispiel |
|--------|-----------|---------|
| `[Doku]` | Spec-Arbeit, Konzeption | `Session 5 | 2025-03-12 | [Doku] Payment-Spec` |
| `[Code]` | Implementierung | `Session 12 | 2025-04-01 | [Code] Auth-Middleware` |
| `[Review]` | Corrigendum, Code-Review | `Session 8 | 2025-03-20 | [Review] DB-Schema-Prüfung` |
| `[Fix]` | Bugfix, Problem-Behebung | `Session 15 | 2025-04-10 | [Fix] Rate-Limiter Timeout` |
| `[Ops]` | Deployment, Infrastruktur | `Session 18 | 2025-04-15 | [Ops] Staging-Deployment` |

Optional — Konsistenz ist wichtiger als Vollständigkeit. Wenn Typen verwendet werden, dann durchgehend.

---

## Meilenstein-Markierungen (ab großen Projekten)

Bei Phasen-Übergängen einen expliziten Meilenstein-Eintrag setzen:

```markdown
### --- MEILENSTEIN: Konzeptphase abgeschlossen | 2025-03-25 ---

**Status:** Alle Specs fertig, Corrigendum durchlaufen, keine offenen Punkte
**Nächster Schritt:** Code-Phase beginnen mit Auth-Middleware (siehe Arbeitsreihenfolge)
```

Das macht es einfach, im Log zu springen und den Phasen-Übergang zu finden.

---

## Speicherort

```
docs/tracking/session-log.md
```

Eine Datei pro Projekt. Nicht splitten (z.B. nach Monat) — das erschwert die Suche. Bei sehr langen Projekten (50+ Sessions) kann ein Archiv-Abschnitt am Ende sinnvoll sein.

---

## Häufige Fehler

| Fehler | Problem | Besser |
|--------|---------|--------|
| "An Feature X gearbeitet" | Kein konkretes Ergebnis | "User-Registration Spec geschrieben, DEC-004 getroffen" |
| Nächste Schritte vergessen | Nächste Session startet orientierungslos | Immer ausfüllen, auch wenn "nur" ein Review ansteht |
| Session-Log erst am nächsten Tag | Kontext fehlt, Details werden vergessen | Direkt am Ende der Session schreiben |
| Entscheidungen nur im Log | Nicht auffindbar ohne das gesamte Log zu lesen | Verweis auf DEC-XXX im Entscheidungs-Register |
