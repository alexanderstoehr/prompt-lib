# Anleitung: Dokumentations-Phase

> Regelwerk für die Konzept- und Dokumentationsphase eines Projekts.
> Wird eingesetzt **bevor Code geschrieben wird** — also während Specs, Architektur-Entscheidungen und Feature-Definitionen entstehen.

---

## Geltungsbereich

Diese Anleitung gilt für die Phase, in der:
- Projektstruktur und Architektur definiert werden
- Feature-Specs geschrieben oder erweitert werden
- Entscheidungen über Scope, Tech-Stack und Abhängigkeiten fallen

Sie ersetzt **nicht** die Code-Phase-Regeln (CLAUDE.md), sondern ergänzt sie für die vorgelagerte Konzeptarbeit.

---

## Skalierung: Was braucht mein Projekt?

Nicht jedes Projekt braucht alles. Die Anleitung skaliert mit der Komplexität:

| Projektgröße | Empfohlene Elemente |
|---|---|
| **Klein** (1-5 Specs, einfache Architektur) | Grundprinzipien, Explore-Check, Scope-Creep-Schutz, Session-Log |
| **Mittel** (5-15 Specs, mehrere Systeme) | Alles aus Klein + Adversarial Review, Projekt-Struktur-Datei, Scratchpad |
| **Groß** (15+ Specs, komplexe Abhängigkeiten) | Alles + Dependency Sequencing, Corrigendum-Sessions, Security-Review (Gesamtbild) |

**Faustregel:** Wenn du mehr als 10 Specs hast oder mehr als ein externes System anbindest, lohnt sich der volle Umfang. Darunter reichen die Kern-Elemente.

---

## Grundprinzipien

| # | Prinzip | Bedeutung |
|---|---------|-----------|
| 1 | **Nie ohne Rückfrage ändern** | Specs, Scope oder Entscheidungen nie eigenmächtig erweitern oder umschreiben. Immer erst fragen. |
| 2 | **Qualität vor Geschwindigkeit** | Lieber einmal mehr nachfragen als eine falsche Annahme in eine Spec schreiben. |
| 3 | **Jede Entscheidung begründen** | Keine Entscheidung ohne dokumentierte Begründung und verworfene Alternativen. |
| 4 | **Single Source of Truth** | Jede Information existiert genau einmal. Keine Doppel-Dokumentation. |
| 5 | **Messbare Grenzen statt offener Definitionen** | Jede Spec enthält konkrete Werte — Limits, Timeouts, Maximalwerte, Intervalle. Nichts bleibt "ungefähr" oder "nach Bedarf". |

---

## Dependency-Driven Sequencing

> Specs werden nicht in willkürlicher Reihenfolge geschrieben, sondern in der Reihenfolge ihrer Abhängigkeiten.

**Regeln:**

1. **Abhängigkeiten vor Abhängigen** — Eine Spec kann erst geschrieben werden, wenn alle Specs fertig sind, auf die sie sich stützt.
2. **Arbeitsreihenfolge explizit machen** — Die Reihenfolge wird in der Projekt-Struktur-Datei (siehe unten) dokumentiert, nicht im Kopf behalten.
3. **Keine Vorwärts-Referenzen** — Wenn eine Spec ein Konzept braucht, das noch nicht spezifiziert ist, wird zuerst dieses Konzept geschrieben.

**Beispiel einer typischen Abhängigkeitskette:**

```
DB-Entscheidungen → DB-Schema → Feature-Specs → Worker/API-Specs → UI-Specs → Testing
```

**Warum das wichtig ist:** Ohne diese Reihenfolge basieren Specs auf Annahmen über noch nicht definierte Konzepte. Das erzeugt Widersprüche die erst spät auffallen.

---

## Projekt-Struktur-Datei als lebender Index

> Jedes Projekt braucht eine zentrale Registratur — eine Datei die alle Specs, ihren Status und ihre Abhängigkeiten auflistet.

**Die Projekt-Struktur-Datei enthält:**

- Liste aller Spec-Dateien mit Kurzbeschreibung
- Status pro Datei (z.B. ✅ fertig, 🔄 in Arbeit, ⏳ blockiert)
- Abhängigkeiten pro Datei (welche anderen Specs Voraussetzung sind)
- Arbeitsreihenfolge (abgeleitet aus Abhängigkeiten)

**Pflicht-Regel:** Kein File wird hinzugefügt, umbenannt oder entfernt ohne diesen Index zu aktualisieren.

---

## Scratchpad für offene Fragen

> Nicht-finalisierte Gedanken gehören nicht in fertige Specs. Sie brauchen einen eigenen Ort mit klarem Status.

**Das Scratchpad (z.B. `notizen-offen.md`) trennt:**

| Status | Bedeutung |
|--------|-----------|
| ✅ Geklärt | Entscheidung getroffen — mit Begründung ins Archiv |
| 📌 Noch zu klären | Offene Frage — mit vollem Kontext, damit sie ohne Rückfragen bearbeitet werden kann |
| 📝 Notiz | Arbeitsnotiz — kein Entscheidungsbedarf, nur Gedankenstütze |

**Warum das wichtig ist:** Ohne diese Trennung werden halbfertige Gedanken als gesetzt behandelt, oder offene Fragen gehen verloren.

---

## Vor jeder Spec-Änderung: Explore-Check

> Inspiriert von Phase 2 des /wizard-Patterns: Annahmen gegen die Realität prüfen, bevor geschrieben wird.

**Bevor eine Spec geändert oder erweitert wird:**

1. **Betroffene Specs identifizieren** — Welche bestehenden Docs berührt diese Änderung?
2. **Begriffe prüfen** — Wird ein Begriff eingeführt oder verwendet, der woanders anders definiert ist?
3. **Abgrenzungen prüfen** — Wurde bewusst etwas ausgeschlossen, das jetzt wieder reinkommt?
4. **Entscheidungen prüfen** — Gibt es eine bestehende Entscheidung (DEC-XXX) die dieser Änderung widerspricht?
5. **Abhängigkeiten prüfen** — Erzeugt die Änderung eine neue Abhängigkeit zu einem anderen Feature oder System?

**Erst wenn alle fünf Punkte geprüft sind, wird geschrieben.**

---

## Scope-Creep-Schutz

> Inspiriert von Phase 4 des /wizard-Patterns: "Scope-Creep sieht aus wie Fortschritt — ist aber der teuerste Bug."

**Bei jeder Feature-Erweiterung oder neuen Anforderung:**

- [ ] Gehört das zum definierten Projektrahmen?
- [ ] Wurde das Feature bewusst ausgeklammert — und wenn ja, warum?
- [ ] Kann das Projekt ohne dieses Feature seinen Kernzweck erfüllen?
- [ ] Wie viel Komplexität fügt das hinzu (neue DB-Tabellen, APIs, UI-Seiten)?

**Wenn eines dieser Kriterien Zweifel auslöst:**
→ Als explizite Entscheidung dokumentieren (mit Begründung + Alternativen)
→ Nicht stillschweigend in die Spec aufnehmen

---

## Adversarial Review für Docs

> Inspiriert von Phase 7 des /wizard-Patterns: Die eigene Arbeit angreifen, bevor sie Probleme verursacht.

**Vor der Finalisierung einer Spec diese Fragen durchgehen:**

### Konsistenz
- Widerspricht das einer bestehenden Entscheidung?
- Verwendet das einen Begriff der woanders anders definiert ist?
- Passt das zu den Architektur-Grundsätzen des Projekts?

### Machbarkeit
- Ist das mit dem geplanten Tech-Stack umsetzbar?
- Gibt es externe Abhängigkeiten (APIs, Services) die das voraussetzt?
- Ist der Aufwand realistisch im Verhältnis zum Nutzen?

### Abhängigkeiten
- Erzeugt das eine Kopplung zwischen Features die unabhängig sein sollten?
- Muss ein anderes Feature zuerst fertig sein, damit dieses funktioniert?
- Was passiert, wenn dieses Feature später gestrichen wird — bricht anderes?

### Scope
- Löst das ein echtes Problem oder ist es "nice to have"?
- Wurde das Feature vom Projektinhaber gewünscht oder hat es sich eingeschlichen?
- Macht das den Projektumfang signifikant größer?

### Security
- Wo liegen die Vertrauensgrenzen? (User-Input vs. interne Daten vs. externe APIs)
- Wie wird authentifiziert und autorisiert? Gibt es Rollen/Rechte?
- Werden API-Keys und Secrets sicher verwaltet (nicht im Code, nicht in der DB im Klartext)?
- Werden Webhooks verifiziert (Signaturen) oder blind vertraut?
- Gibt es Rate Limiting gegen Missbrauch?
- Was wird in Fehlermeldungen nach außen gegeben? (Keine Stack-Traces, DB-Strukturen, interne Pfade)
- Werden sensitive Felder in der DB verschlüsselt gespeichert (Tokens, Passwörter)?
- Ist Verschlüsselung in Transit (TLS) und at Rest berücksichtigt?

---

## Geplante Corrigendum-Sessions

> Dedizierte Sessions nur für Gegenprüfung — kein neuer Content, nur Validierung.

**Wann einplanen:**
- Nach Abschluss eines thematischen Blocks (z.B. alle Kern-Feature-Specs fertig)
- Vor dem Übergang von Doku-Phase zur Code-Phase
- Bei Verdacht auf Inkonsistenzen nach größeren Änderungen

**Was geprüft wird:**
- [ ] Alle Specs gegen die DB-Schema-Spec: Stimmen Tabellen, Spalten, Beziehungen?
- [ ] Alle Specs gegeneinander: Widersprüchliche Aussagen zum gleichen Konzept?
- [ ] Projekt-Struktur-Datei gegen tatsächliche Files: Stimmt der Index?
- [ ] Scratchpad: Gibt es offene Fragen die inzwischen geklärt sein müssten?
- [ ] Entscheidungs-Register: Sind alle getroffenen Entscheidungen eingetragen?

**Security-Review (Gesamtbild):**
- [ ] Datenfluss-Analyse: Wo kommt User-Input rein → wo wird er verarbeitet → wo wird er ausgegeben? (XSS/Injection-Ketten über mehrere Specs hinweg)
- [ ] API-Angriffsfläche: Welche Endpoints sind öffentlich, welche authentifiziert? Gibt es ungeschützte Pfade?
- [ ] Secret-Management: Werden Tokens, API-Keys und Passwörter durchgehend sicher gehandhabt?
- [ ] Fehler-Exponierung: Geben Fehlermeldungen an irgendeiner Stelle interne Strukturen preis?
- [ ] Externe Abhängigkeiten: Werden alle externen APIs und Webhooks verifiziert, nicht blind vertraut?

**Ergebnis:** Corrigendum-Einträge am Ende der betroffenen Specs + Session-Log-Eintrag mit gefundenen Problemen und Korrekturen.

---

## Session-Log-Pflicht

> Jede Doku-Session wird protokolliert — nicht erst beim Coden, sondern ab der ersten Session.

**Format (reverse-chronologisch, neueste oben):**

```markdown
### Session N | YYYY-MM-DD | Thema

**Ergebnis:** Was wurde erreicht
**Geänderte Files:** Liste aller bearbeiteten Dateien
**Entscheidungen:** Welche Entscheidungen wurden getroffen (mit Verweis auf DEC-XXX)
**Offene Punkte:** Was muss noch geklärt werden
**Nächste Schritte:** Konkrete nächste Aktion für die Folgesession
```

**Regeln:**
- Jede Session bekommt einen Eintrag — auch wenn "nur" gelesen oder geprüft wurde
- Session-Einträge werden nie rückwirkend geändert (Append-Only)
- Nächste Schritte sind konkret genug um ohne Kontext weiterzuarbeiten

**Warum das wichtig ist:** Ohne Session-Log geht der rote Faden zwischen Sessions verloren. Man weiß nicht mehr wo man war, was offen ist, und warum etwas so entschieden wurde.

---

## Konsistenz-Checkliste (pro Doku-Session)

Am Ende jeder Dokumentations-Session durchgehen:

- [ ] Alle geänderten Specs sind in sich konsistent
- [ ] Keine Widersprüche zu bestehenden Specs eingeführt
- [ ] Neue Begriffe sind definiert und konsistent verwendet
- [ ] Scope-Erweiterungen sind als Entscheidung dokumentiert
- [ ] Abhängigkeiten zwischen Features sind explizit benannt
- [ ] Kein Feature stillschweigend hinzugefügt oder entfernt
- [ ] Entscheidungen haben Begründung + verworfene Alternativen
- [ ] Projekt-Struktur-Datei ist aktuell
- [ ] Session-Log-Eintrag geschrieben

---

## Exit-Kriterium: Wann ist die Doku-Phase fertig?

> Die Doku-Phase endet nicht "wenn nichts mehr einfällt", sondern wenn definierte Kriterien erfüllt sind.

**Die Doku-Phase ist abgeschlossen wenn:**

- [ ] Alle geplanten Specs sind geschrieben und als ✅ markiert
- [ ] Keine offenen Punkte mehr im Scratchpad (alle 📌 → ✅ oder bewusst gestrichen)
- [ ] Mindestens eine Corrigendum-Session wurde durchgeführt (bei mittleren/großen Projekten)
- [ ] Security-Review (Gesamtbild) ist durchgelaufen (bei Projekten mit externen APIs oder User-Input)
- [ ] Die Projekt-Struktur-Datei ist vollständig und aktuell
- [ ] Es gibt einen klaren Einstiegspunkt für die Code-Phase (welcher Handler/welche Komponente zuerst?)

**Abschluss dokumentieren:** Expliziter Session-Log-Eintrag mit "Konzeptphase abgeschlossen ✅" und empfohlenem erstem Implementierungsschritt.

---

## Zusammenfassung: Sechs Schutzebenen

```
┌──────────────────────────────────────────────────┐
│  1. DEPENDENCY SEQUENCING (Reihenfolge)          │
│     → Specs in Abhängigkeitsreihenfolge schreiben│
│     → Keine Vorwärts-Referenzen                  │
├──────────────────────────────────────────────────┤
│  2. EXPLORE-CHECK (vor dem Schreiben)            │
│     → Bestehende Docs prüfen                     │
│     → Widersprüche identifizieren                │
├──────────────────────────────────────────────────┤
│  3. SCOPE-CREEP-SCHUTZ (während des Schreibens)  │
│     → Jede Erweiterung hinterfragen              │
│     → Explizit entscheiden, nicht schleichen     │
├──────────────────────────────────────────────────┤
│  4. ADVERSARIAL REVIEW (nach dem Schreiben)      │
│     → Eigene Arbeit angreifen                    │
│     → Konsistenz, Machbarkeit, Scope prüfen      │
├──────────────────────────────────────────────────┤
│  5. CORRIGENDUM-SESSIONS (regelmäßig)            │
│     → Dedizierte Validierungs-Sessions           │
│     → Alle Files gegeneinander prüfen            │
├──────────────────────────────────────────────────┤
│  6. SESSION-LOG (durchgehend)                    │
│     → Lückenlose Nachvollziehbarkeit             │
│     → Roter Faden zwischen Sessions              │
└──────────────────────────────────────────────────┘
```

---

## Entstehung & Weiterentwicklung

Dieses Template entstand aus drei Quellen:
1. **Bestehende Code-Phase-Regeln** — Grundprinzipien (Rückfrage-Pflicht, Qualität vor Geschwindigkeit) auf die Doku-Phase übertragen
2. **dev.to /wizard-Artikel** — Phasen 2 (Explore), 4 (Minimal Implementation) und 7 (Adversarial Review) auf Dokumentationsarbeit adaptiert
3. **Archiv-Analyse eines realen Projekts** — 41 Sessions reine Dokumentation ergaben fünf bewährte Muster (Dependency Sequencing, Corrigendum-Sessions, Scratchpad, messbare Grenzen, lebender Index)

Ausführlicher Entstehungskontext und Weiterentwicklungs-Hinweise → `notes/doku-phase-anleitung.notes.md`
