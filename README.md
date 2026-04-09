# prompt-lib

Strukturierte Anleitungen für KI-gestützte Softwareentwicklung — von der ersten Idee bis zum fertigen Produkt.

## Was ist das Problem?

Wer heute mit KI-Agenten wie Claude Software entwickelt, kennt das: Die KI ist mächtig, aber ohne Struktur passiert schnell Chaos. Entscheidungen gehen zwischen Sessions verloren, Features schleichen sich ein die niemand bestellt hat, und nach drei Wochen weiss keiner mehr warum etwas so gebaut wurde wie es gebaut wurde.

**prompt-lib** löst das. Es ist ein Playbook — eine Sammlung von Phasen-Anleitungen die definieren, wie Mensch und KI-Agent durch ein Softwareprojekt arbeiten. Nicht einzelne Prompts, sondern vollständige Workflows mit Schutzebenen, Werkzeugen und Dokumentationssystemen.

## Wie funktioniert das?

Die Anleitungen werden in ein neues Projekt kopiert und dort als Regeln für den KI-Agenten hinterlegt. Ab dann befolgt der Agent diese Regeln in jeder Session — er dokumentiert Entscheidungen, prüft auf Widersprüche, hält Fortschritt fest und schützt vor typischen Fehlern.

### Beispiel 1: Ein neues Produkt von Null starten

Du hast eine Idee für eine App, aber vieles ist noch unklar.

```
1. bootstrap.md durcharbeiten → Projektstruktur steht
2. Explorations-Phase starten → Ideen finden, Markt prüfen, Annahmen testen
   - Der KI-Agent nutzt den Werkzeugkasten (10 Techniken wie
     Perspektivwechsel, Jobs-to-be-Done, Analogie-Mining)
   - Alles wird im Explorations-Log festgehalten
   - Am Ende: Erkenntnisse-Destillat als Input für die Spezifikation
3. Doku-Phase starten → Features spezifizieren, DB-Design, Architektur
   - 6 Schutzebenen verhindern: Scope-Creep, Widersprüche, vergessene Abhängigkeiten
   - Entscheidungs-Register hält fest warum etwas so entschieden wurde
4. Weiter mit Code-Phase, Testing, Deployment...
```

Jede Phase produziert strukturierte Outputs die in die nächste Phase fliessen. Nichts geht verloren.

### Beispiel 2: Mitten in der Feature-Planung stecken

Du bist bereits am Spezifizieren und fragst den KI-Agenten: *"Was wäre noch ein gutes Feature?"*

Statt einer Standardantwort arbeitet der Agent systematisch den Werkzeugkasten durch:

- **Perspektivwechsel:** Was würde ein Investor fragen? Was nervt den Support?
- **Jobs-to-be-Done:** Welchen Job erledigt das Produkt *wirklich*?
- **Constraint-Flipping:** Was wenn wir kein Budget-Limit hätten?
- **Falsifizierung:** Warum könnte unser bestes Feature scheitern?

Jedes Ergebnis wird dokumentiert — auch Sackgassen und verworfene Ideen. So kann man Monate später zurückkommen und dort weitermachen wo man aufgehört hat.

### Beispiel 3: Session-Kontinuität über Wochen

Das grösste Problem bei KI-gestützter Entwicklung: Kontext geht zwischen Sessions verloren. prompt-lib löst das durch:

- **Session-Log** — Jede Arbeitssession wird protokolliert (Ergebnis, Entscheidungen, nächste Schritte)
- **Entscheidungs-Register** — Jede Entscheidung mit Begründung und verworfenen Alternativen
- **Scope-Creep-Schutz** — Vor jeder Änderung wird geprüft: Gehört das zum Plan? Widerspricht das einer bestehenden Entscheidung?

Das Ergebnis: Man kann nach zwei Wochen Pause eine neue Session starten und der KI-Agent weiss genau wo man steht, was offen ist und was als nächstes kommt.

## Phasen

```
exploration/  → Ideen finden, Möglichkeitsraum öffnen, validieren
doku-phase/   → Spezifizieren, Architektur festlegen, Abhängigkeiten klären
forms/        → Formulare & Wizards — Konzeption, UX, Tracking, Psychologie
code-phase/   → (geplant)
testing/      → (geplant)
deployment/   → (geplant)
maintenance/  → (geplant)
```

### Exploration

Für die Phase wenn noch nichts feststeht. Drei Ebenen: Exploration (Ideen generieren), Validierung (gegen Realität prüfen), Destillation (Erkenntnisse verdichten).

Enthält einen Werkzeugkasten mit 10 Techniken, 16 Denkprinzipien als Bewertungslinsen (Gamification, Loss Aversion, Progressive Disclosure u.a.), und ein Notiz-System das Rückkehr-Fähigkeit sicherstellt.

**[exploration/explorations-phase-anleitung.md](exploration/explorations-phase-anleitung.md)**

### Dokumentation / Spezifikation

Für die Phase wenn Specs geschrieben werden. 6-Schichten-Schutzmodell:

1. **Dependency Sequencing** — Specs in der richtigen Reihenfolge schreiben
2. **Explore-Check** — Vor jeder Änderung bestehende Docs prüfen
3. **Scope-Creep-Schutz** — Jede Erweiterung hinterfragen
4. **Adversarial Review** — Eigene Arbeit angreifen
5. **Corrigendum-Sessions** — Alle Specs gegeneinander prüfen
6. **Session-Log** — Lückenlose Nachvollziehbarkeit

**[doku-phase/doku-phase-anleitung.md](doku-phase/doku-phase-anleitung.md)**

### Formulare & Wizards

Operatives Regelwerk für mehrstufige Formulare — von der Konzeption (Wizard-Typ, Rendering-Modus, Feldstrategie) über UX-Design, Mobile-Regeln und Psychologie-Prinzipien bis zu Tracking-Architektur und Post-Submit.

**[forms/wizard-ruleset.md](forms/wizard-ruleset.md)**

### Phasenübergreifend

| Datei | Inhalt |
|-------|--------|
| [shared/git-konventionen.md](shared/git-konventionen.md) | Commit-Format, Branch-Strategie, Tags, PRs |
| [shared/session-log.md](shared/session-log.md) | Session-Log Regeln, Formate, Meilensteine |
| [shared/entscheidungs-log.md](shared/entscheidungs-log.md) | Entscheidungs-Register (ADR-light) |

## Schnellstart

1. [bootstrap.md](bootstrap.md) lesen — Schritt-für-Schritt Anleitung für ein neues Projekt
2. Relevante Templates ins Projekt kopieren und anpassen
3. Templates in die CLAUDE.md des Projekts einbinden
4. Loslegen — der KI-Agent befolgt ab sofort die Regeln

## Skalierung

Jedes Template enthält Empfehlungen für drei Projektgrössen:

| Grösse | Empfehlung |
|--------|-----------|
| **Klein** | Kern-Elemente nutzen, Rest weglassen |
| **Mittel** | Kern + Tracking + Reviews |
| **Gross** | Voller Umfang aller Schutzebenen |

Nicht jedes Projekt braucht alles. Ein Wochenend-Projekt braucht kein Entscheidungs-Register. Ein 6-Monats-Projekt schon.

## Sprache

Docs auf Deutsch, Dateinamen auf Englisch/Deutsch mit Bindestrichen.

## Status

Aktiv in Entwicklung. Exploration und Doku-Phase sind praxiserprobt, weitere Phasen folgen bei Bedarf.

## Lizenz

MIT
