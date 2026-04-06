# Anleitung: Explorations-Phase

> Regelwerk für die Phase vor der Spezifikation — wenn der Möglichkeitsraum noch offen ist.
> Wird eingesetzt **bevor Specs geschrieben werden** — also während Ideen entstehen, Annahmen getestet und Grenzen verschoben werden.

---

## Geltungsbereich

Diese Anleitung gilt für die Phase, in der:
- Eine Idee oder ein Problemfeld erkundet wird
- Noch keine Festlegungen getroffen werden sollen
- Der Möglichkeitsraum bewusst offen gehalten wird
- Recherche, Dialog und Experimente den Weg weisen

Sie endet wenn genug validierte Erkenntnisse vorliegen um in die Doku-Phase (Spezifikation) überzugehen.

---

## Skalierung: Was braucht mein Projekt?

| Projektgröße | Empfohlene Elemente |
|---|---|
| **Klein** (klare Idee, wenig Unbekanntes) | Explorations-Log, Werkzeugkasten bei Bedarf, Kurzform-Destillat |
| **Mittel** (mehrere Richtungen möglich) | Alles aus Klein + Ideen-Register, systematischer Werkzeugkasten-Einsatz, Validierung |
| **Groß** (viel Unbekanntes, neues Terrain) | Alles + vollständiges Erkenntnisse-Destillat, Rückkehr-Fähigkeit, Schutzebenen aktiv |

**Faustregel:** Wenn du nach 2 Sessions immer noch nicht weisst wohin das Projekt geht, lohnt sich der volle Umfang. Wenn die Richtung klar ist und nur Details fehlen, reicht die Kurzform.

---

## Grundprinzipien

| # | Prinzip | Bedeutung |
|---|---------|-----------|
| 1 | **Alles festhalten** | Jeder Gedanke, jede Sackgasse, jeder Sprung wird notiert. Nichts ist zu klein oder zu verrückt. |
| 2 | **Erst sammeln, dann filtern** | In der Exploration kein "das geht nicht". Bewertung kommt in der Validierung. |
| 3 | **Denkwege dokumentieren, nicht nur Ergebnisse** | "Wie sind wir darauf gekommen?" ist genauso wichtig wie das Ergebnis selbst. |
| 4 | **Sackgassen sind wertvoll** | Verworfene Pfade mit Begründung festhalten — spart beim nächsten Mal Zeit und öffnet beim Zurückkehren neue Perspektiven. |
| 5 | **Nicht zu früh festlegen** | Eine gute Idee ist noch keine Entscheidung. Erst explorieren, dann validieren, dann entscheiden. |

---

## Drei Ebenen

Die Explorations-Phase bewegt sich zwischen drei Ebenen. Sie sind nicht streng sequentiell — man springt zwischen ihnen, aber jede hat einen klaren Zweck.

### 1. Exploration — Möglichkeitsraum aufsprengen

> Hier geht es darum Grenzen zu verschieben und in neue Themengebiete reinzukommen. Dialogisch, spielerisch, ohne Ergebnis-Druck.

**Leitfragen zum Einstieg:**
- Was ist das eigentliche Problem das wir lösen wollen?
- Für wen lösen wir es — und warum jetzt?
- Was wäre die mutigste Version dieser Idee?
- Was würde sich ändern wenn wir eine Einschränkung aufheben?
- Welche Annahmen machen wir unbewusst?

**Regeln für diese Ebene:**
- Kein "das geht nicht" — wird als Idee notiert, nicht abgewürgt
- Quantität vor Qualität — lieber 20 halbgare Ideen als 3 durchdachte
- Aktiv nach dem Unerwarteten suchen — nicht nur das Naheliegende

### 2. Validierung — Stimmt das?

> Ideen gegen die Realität prüfen. Nicht um sie zu töten, sondern um zu verstehen was tragfähig ist.

**Was geprüft wird:**
- **Markt/Wettbewerb** — Macht das schon jemand? Wenn ja: besser, anders oder gar nicht?
- **Technische Machbarkeit** — Geht das? APIs testen, Prototypen bauen, Proof of Concepts
- **Zielgruppe** — Will das jemand? Wer genau? Was ist der Hebel?
- **Gegenargumente** — Warum könnte das scheitern? Was spricht dagegen?
- **Riskanteste Annahme zuerst** — Was muss wahr sein damit alles andere Sinn macht? Das zuerst prüfen.

**Regeln für diese Ebene:**
- Bestätigung suchen ist menschlich — Widerlegung suchen ist nützlicher
- Eine widerlegte Idee ist kein Verlust, sondern eine Erkenntnis
- Validierungsergebnisse immer im Explorations-Log festhalten

### 3. Destillation — Was davon ist real?

> Erkenntnisse verdichten zu konkreten Inputs für die Doku-Phase.

**Output (Erkenntnisse-Destillat):**

```markdown
## Erkenntnisse-Destillat | [Projektname]

### Kern-Idee
[Ein Satz der das Projekt beschreibt]

### Leitprinzipien (wenn gewählt)
[1-3 gewählte Denkprinzipien die das Projekt prägen — mit Begründung. Auch bewusst ausgeschlossene Prinzipien notieren.]

### Validiert ✅
[Was wissen wir sicher — mit Quelle/Beweis]

### Annahmen (noch nicht validiert) ⚠️
[Was glauben wir, aber noch nicht bewiesen]

### Verworfen ❌
[Was haben wir geprüft und ausgeschlossen — mit Begründung]

### Offene Fragen
[Was muss in der Doku-Phase geklärt werden]

### Empfohlener Einstieg für die Doku-Phase
[Welche Spec zuerst? Welche Abhängigkeit zuerst klären?]
```

---

## Werkzeugkasten

> Das Herzstück der Exploration. Techniken die je nach Bedarf eingesetzt werden — nicht als Pflicht-Checkliste, sondern als Repertoire.

### Einsatz-Modi

**Modus 1: Generieren** — "Was könnte noch?"
Wenn neue Ideen, Features oder Richtungen gesucht werden. Claude arbeitet die passenden Techniken durch und dokumentiert alle Ergebnisse im Explorations-Log.

**Modus 2: Vertiefen** — "Was denkst du dazu?"
Wenn etwas Konkretes besprochen wird. Claude nutzt die Techniken um aktuell Besprochenes zu challengen, erweitern und von verschiedenen Seiten zu beleuchten.

### Techniken

#### Perspektivwechsel
Als verschiedene Stakeholder denken — nicht nur als Entwickler.

| Perspektive | Frage |
|-------------|-------|
| **Nutzer** | Was brauche ich wirklich? Was nervt mich? |
| **Kritiker** | Was ist der schwächste Punkt? Wo bricht das? |
| **Wettbewerber** | Was würde ich anders machen? Wo ist die Lücke? |
| **Investor** | Warum sollte ich hier Geld reinstecken? Was ist der Markt? |
| **Support** | Welche Fragen kommen am häufigsten? Wo ist es verwirrend? |
| **5 Jahre später** | Was bereuen wir dann, nicht bedacht zu haben? |

#### Jobs-to-be-Done
Nicht Features denken, sondern: Welchen Job erledigt das Produkt?

- "Wenn [Situation], will ich [Motivation], damit ich [Ergebnis]."
- Beispiel: "Wenn ich als KMU-Inhaber nach meiner Firma google, will ich dass KI-Assistenten korrekte Infos geben, damit ich keine Kunden durch falsche Angaben verliere."

Der Job bleibt stabil — die Lösung kann sich ändern.

#### Analogie-Mining
Gelöste Probleme aus anderen Branchen übertragen.

- "Welches Problem in einer anderen Branche ähnelt unserem?"
- "Wie hat [Branche X] das gelöst — und was können wir übernehmen?"
- Beispiel: Airbnb → Vertrauensproblem zwischen Fremden → Bewertungen + Verifizierung. Was ist unser Vertrauensproblem?

#### Constraint-Flipping
Bewusst Einschränkungen aufheben oder umkehren.

| Constraint | Flip |
|-----------|------|
| "Wir haben kein Budget" | "Was wenn Geld keine Rolle spielt?" |
| "Wir können nur X" | "Was wenn wir alles könnten?" |
| "Das muss schnell gehen" | "Was wenn wir ein Jahr Zeit hätten?" |
| "Nur für Schweiz" | "Was wenn es weltweit funktionieren müsste?" |
| "Braucht Login" | "Was wenn alles öffentlich wäre?" |

Nicht um realistisch zu planen — sondern um den Denkraum zu öffnen.

#### How Might We
Probleme als Chancen umformulieren.

- Problem: "KMUs wissen nicht was LLM-Sichtbarkeit ist"
- HMW: "Wie könnten wir KMUs den Wert von LLM-Sichtbarkeit zeigen, ohne dass sie verstehen müssen wie es technisch funktioniert?"

Öffnet den Lösungsraum statt ihn einzuengen.

#### Empathy Map
Den Nutzer wirklich verstehen — über Features hinaus.

```
        DENKT / FÜHLT
    (Sorgen, Wünsche, Ängste)
              │
   HÖRT ──── NUTZER ──── SIEHT
(Berater,     │        (Markt,
 Medien,      │         Wettbewerb,
 Kollegen)    │         Angebote)
              │
        SAGT / TUT
    (Verhalten, Aussagen)
```

#### Crazy 8s
Viele Ideen in kurzer Zeit generieren — Quantität schlägt Qualität.

- 8 Ideen zu einem Thema, je 1 Minute pro Idee
- Kein Filter, kein "aber"
- Danach: Welche 2-3 verdienen eine Vertiefung?

#### Hypothesen formulieren
Annahmen explizit machen und testbar formulieren.

```
Wir glauben dass [Annahme],
weil [Beobachtung/Grund].
Wir können das prüfen indem [Test/Experiment].
Ergebnis: [bestätigt / widerlegt / unklar]
```

#### Falsifizierung
Die eigene beste Idee aktiv angreifen.

- "Warum könnte das scheitern?"
- "Unter welchen Umständen funktioniert das nicht?"
- "Was müsste passieren damit wir das aufgeben?"

Wenn die Idee den Angriff überlebt, ist sie stärker. Wenn nicht, war es gut das jetzt rauszufinden.

#### Smoke Test
Idee testen bevor man sie baut.

- Kann man die Nachfrage prüfen ohne das Produkt zu bauen?
- Kann man einen minimalen Prototypen in Stunden statt Wochen erstellen?
- Fake Door: Feature ankündigen und messen ob jemand klickt

---

## Denkprinzipien

> Der Werkzeugkasten hilft Ideen zu **finden**. Die Denkprinzipien helfen Ideen zu **bewerten, schärfen und auszurichten**. Man kann ein Projekt bewusst auf 1-3 Leitprinzipien aufbauen und jede Entscheidung daran messen.

### Leitprinzipien wählen (optional)

Nicht alle Prinzipien passen zu jedem Projekt — und nicht jedes Projekt braucht explizite Leitprinzipien. Manche Prinzipien passen nicht zur Zielgruppe, manche fühlen sich falsch an, manche sind für den konkreten Fall irrelevant. Das ist okay.

**Mögliche Wege:**

1. **Bewusst wählen** — 1-3 Prinzipien als Leitprinzipien festlegen und das Projekt daran ausrichten
2. **Explorativ nutzen** — In einer Session gemeinsam durchgehen: Welche Prinzipien kommen in Frage? Welche schliessen wir bewusst aus? Warum?
3. **Als Impulsgeber** — Einzelne Prinzipien punktuell einsetzen wenn sie gerade passen, ohne sich festzulegen
4. **Gar nicht** — Das Projekt braucht keine Leitprinzipien. Die Techniken aus dem Werkzeugkasten reichen.

**Wenn Leitprinzipien gewählt werden:**

```markdown
## Leitprinzipien für [Projektname]

1. [Prinzip] — Warum dieses Prinzip für unser Projekt zentral ist
2. [Prinzip] — ...

Bewusst ausgeschlossen:
- [Prinzip] — Warum nicht (z.B. "Lock-in passt nicht zu unseren Werten")
```

Die Leitprinzipien werden im Explorations-Log festgehalten und können sich ändern — aber bewusst, nicht schleichend. Auch bewusste Ausschlüsse sind eine wertvolle Erkenntnis.

### Katalog

#### Verhaltens-Prinzipien

| Prinzip | Kernidee | Frage an jedes Feature |
|---------|----------|----------------------|
| **Gamification** | Progression, Belohnung, Status, Levels | Macht das süchtig? Gibt es einen Fortschrittsbalken? |
| **Loss Aversion** | Verlust wiegt schwerer als Gewinn | Zeigen wir was der User *verliert* wenn er nicht handelt? |
| **Social Proof** | Menschen folgen anderen Menschen | Sehen User dass andere das auch tun/nutzen? |
| **Endowment Effect** | Was man hat, gibt man ungern her | Geben wir erstmal viel, und nehmen dann weg (Upgrade-Anreiz)? |
| **Variable Rewards** | Unvorhersagbare Belohnungen binden stärker als konstante | Gibt es Überraschungsmomente, nicht nur planbare? |
| **Reciprocity** | Wer etwas bekommt, will etwas zurückgeben | Geben wir zuerst Wert bevor wir etwas verlangen? |

#### Produkt-Prinzipien

| Prinzip | Kernidee | Frage an jedes Feature |
|---------|----------|----------------------|
| **Progressive Disclosure** | Komplexität stückweise enthüllen | Sieht der Anfänger nur das Nötige? Kommt der Rest wenn er bereit ist? |
| **Teaser-Prinzip** | Den Vorteil zeigen, nicht das Feature | Kommunizieren wir das Ergebnis oder die Mechanik? |
| **Defaults Matter** | Die Voreinstellung gewinnt fast immer | Was ist unser Default — und ist er der richtige? |
| **Friction Design** | Bewusst Reibung einbauen oder entfernen | Wo wollen wir es einfach machen (Signup) und wo bewusst schwer (Löschen)? |
| **Network Effects** | Wird das Produkt besser je mehr es nutzen? | Profitiert User A davon dass User B auch da ist? |
| **Ikea-Effekt** | Selbst Aufgebautes wird höher geschätzt | Kann der User etwas selbst gestalten/aufbauen? |

#### Strategie-Prinzipien

| Prinzip | Kernidee | Frage an jedes Feature |
|---------|----------|----------------------|
| **Pareto (80/20)** | 20% der Features liefern 80% des Werts | Gehört das zu den 20% oder zu den 80%? |
| **Lock-in vs. Lock-out** | Wechsel erschweren (Retention) vs. Einstieg erschweren (Akquise) | Machen wir den Einstieg leicht und den Abschied schwer — oder umgekehrt? |
| **Commoditization** | Ist das Feature in 2 Jahren Standard? | Differenziert uns das jetzt — oder bald nicht mehr? |
| **First-Mover vs. Fast-Follower** | Erster sein oder besser sein? | Müssen wir das als Erste haben, oder reicht es besser zu sein? |

### Einsatz der Prinzipien

**Bei neuen Features:** "Prüfe dieses Feature gegen unsere Leitprinzipien" → Passt es, verstärkt es, widerspricht es?

**Bei Entscheidungen:** "Welches Prinzip spricht für Option A, welches für Option B?" → Macht Trade-offs sichtbar.

**Bei Reviews:** "Geh alle Prinzipien durch und sag mir wo wir Potenzial liegen lassen" → Systematisch blinde Flecken finden.

**Wichtig:** Prinzipien können sich widersprechen (z.B. Friction Design vs. Progressive Disclosure). Das ist normal — die Leitprinzipien geben die Richtung vor, der Rest sind Impulse.

---

## Notiz-System

> Die Notizen sind nicht Beiwerk — sie sind der halbe Wert der Explorations-Phase. Ohne Notizen gehen Erkenntnisse verloren und die Rückkehr-Fähigkeit ist zerstört.

### Explorations-Log

Chronologisches Protokoll aller Explorations-Sessions. **Alles wird festgehalten.**

```markdown
### Session N | YYYY-MM-DD | Thema

**Ebene:** Exploration / Validierung / Destillation
**Genutzte Techniken:** [aus Werkzeugkasten]
**Genutzte Prinzipien:** [aus Denkprinzipien, falls angewendet]

**Denkweg:**
[Wie sind wir auf die Ideen gekommen? Welche Frage hat wohin geführt?]

**Ergebnisse:**
[Ideen, Erkenntnisse, Fakten — alles]

**Prinzipien-Check:**
[Falls Leitprinzipien gewählt: Wie passen die heutigen Ergebnisse dazu?]

**Sackgassen:**
[Was haben wir verfolgt und verworfen — und warum?]

**Offene Fäden:**
[Was lohnt sich weiterzuverfolgen?]
```

**Regeln:**
- Append-Only — Einträge nie rückwirkend ändern
- Auch "nur geredet, nichts Konkretes" ist ein Eintrag wert
- Denkwege explizit machen, nicht nur Ergebnisse
- Bei jeder genutzten Technik: was kam raus?

### Ideen-Register

Alle Ideen an einem Ort, mit klarem Status.

```markdown
## Ideen-Register

| # | Idee | Status | Herkunft | Notiz |
|---|------|--------|----------|-------|
| I-001 | [Idee] | frisch | Session N, Technik X | [Kontext] |
| I-002 | [Idee] | validiert | Session N | [Beweis/Quelle] |
| I-003 | [Idee] | verworfen | Session N | [Warum nicht] |
| I-004 | [Idee] | geparkt | Session N | [Warum geparkt, wann revisiten] |
```

**Status-Definitionen:**

| Status | Bedeutung |
|--------|-----------|
| 🆕 frisch | Neu, noch nicht bewertet |
| ✅ validiert | Geprüft, hält stand — geht ins Destillat |
| ❌ verworfen | Geprüft, hält nicht — Begründung dokumentiert |
| ⏸️ geparkt | Interessant aber nicht jetzt — Kontext festhalten für spätere Rückkehr |

### Erkenntnisse-Destillat

Das Übergabe-Dokument an die Doku-Phase. Entsteht am Ende der Exploration (oder iterativ während der Destillations-Ebene). Format siehe oben unter "Drei Ebenen → 3. Destillation".

---

## Schutzebenen

### 1. Zu-früh-festlegen-Schutz

> "Das ist die Lösung!" nach 10 Minuten ist fast immer falsch.

**Warnsignale:**
- Sofort an Implementierung denken statt weiter zu explorieren
- Nur eine Option sehen
- "Das ist offensichtlich" — meistens ist es das nicht

**Gegenmittel:** Mindestens 3 Alternativen generieren bevor eine Richtung gewählt wird. Wenn nur eine Idee da ist, wurde zu wenig exploriert.

### 2. Lieblings-Ideen-Kill

> Die eigene beste Idee ist der grösste blinde Fleck.

**Vorgehen:** Bevor eine Idee als "validiert" markiert wird:
- Falsifizierung durchführen (siehe Werkzeugkasten)
- Mindestens 3 Gründe finden warum sie scheitern könnte
- Wenn sie das überlebt: gut. Wenn nicht: noch besser — jetzt statt später.

### 3. Endlos-Schweben-Schutz

> Exploration ohne Ende ist Prokrastination.

**Gegenmittel:**
- **Timeboxing:** Vor Beginn festlegen: "Wir explorieren N Sessions, dann destillieren wir."
- **Exit-Frage:** "Haben wir genug validierte Erkenntnisse um Specs zu schreiben?" Wenn ja → Destillation. Wenn nein → gezielt die Lücken füllen.
- **Diminishing Returns erkennen:** Wenn die letzten 2 Sessions keine neuen Erkenntnisse gebracht haben, ist es Zeit aufzuhören.

### 4. Sackgassen-Dokumentation

> Verworfene Pfade sind die teuerste Information die man verlieren kann.

**Pflicht:** Jede verworfene Idee bekommt einen Eintrag im Ideen-Register mit:
- Was war die Idee?
- Warum verworfen?
- Unter welchen Umständen könnte sie doch relevant werden?

### 5. Rückkehr-Fähigkeit

> Die Exploration ist nie wirklich "fertig" — man kann immer zurückkommen.

**Voraussetzung:** Das Explorations-Log und Ideen-Register sind so geschrieben, dass jemand (du selbst, Monate später) ohne Kontextwissen den Denkweg nachvollziehen und dort weitermachen kann, wo aufgehört wurde.

**Test:** Lies den ältesten Eintrag im Explorations-Log. Verstehst du warum du das damals so gedacht hast? Wenn nicht, fehlt Kontext.

---

## Exit-Kriterium: Wann ist die Explorations-Phase fertig?

> Die Explorations-Phase endet nicht "wenn keine Ideen mehr kommen", sondern wenn definierte Kriterien erfüllt sind.

**Die Explorations-Phase ist abgeschlossen wenn:**

- [ ] Die Kern-Idee kann in einem Satz beschrieben werden
- [ ] Die Zielgruppe ist identifiziert (wer, warum, Hebel)
- [ ] Mindestens die riskanteste Annahme wurde validiert
- [ ] Wesentliche Sackgassen sind dokumentiert (was nicht und warum)
- [ ] Ein Erkenntnisse-Destillat liegt vor
- [ ] Es gibt genug Material um die Doku-Phase zu starten (nicht genug um sie zu beenden — das ist okay)

**Abschluss dokumentieren:** Expliziter Eintrag im Explorations-Log mit "Exploration abgeschlossen" und Verweis auf das Erkenntnisse-Destillat.

---

## Zusammenfassung: Struktur für Chaos

```
┌──────────────────────────────────────────────────┐
│  EXPLORATION (divergent)                         │
│  → Möglichkeitsraum öffnen                       │
│  → Werkzeugkasten einsetzen                      │
│  → Alles festhalten                              │
├──────────────────────────────────────────────────┤
│  VALIDIERUNG (konvergent)                        │
│  → Ideen gegen Realität prüfen                   │
│  → Riskanteste Annahme zuerst                    │
│  → Sackgassen dokumentieren                      │
├──────────────────────────────────────────────────┤
│  DESTILLATION (verdichtend)                      │
│  → Erkenntnisse zu Inputs für Doku-Phase         │
│  → Validiert / Annahme / Verworfen / Offen       │
│  → Klarer Einstiegspunkt für Spezifikation       │
├──────────────────────────────────────────────────┤
│  NOTIZ-SYSTEM (durchgehend)                      │
│  → Explorations-Log: Denkwege + Ergebnisse       │
│  → Ideen-Register: frisch / validiert / geparkt  │
│  → Erkenntnisse-Destillat: Übergabe an Doku      │
├──────────────────────────────────────────────────┤
│  SCHUTZEBENEN (durchgehend)                      │
│  → Nicht zu früh festlegen                       │
│  → Lieblings-Ideen angreifen                     │
│  → Nicht endlos schweben                          │
│  → Sackgassen festhalten                         │
│  → Rückkehr ermöglichen                          │
└──────────────────────────────────────────────────┘
```

---

## Entstehung & Weiterentwicklung

Dieses Template entstand aus:
1. **Erfahrung mit aili.ch** — Die Explorations-Phase (Sessions 001–003) passierte unstrukturiert. Marktrecherche, LLM-Visibility-Konzept, sameAs-Quellen testen — alles ad-hoc, ohne systematische Dokumentation. Erkenntnis: Der divergente Teil vor der Spezifikation braucht eigene Regeln.
2. **Design Thinking** — Empathy Map, How Might We, Perspektivwechsel als bewährte Techniken für den divergenten Denkraum.
3. **Lean Startup** — "Riskanteste Annahme zuerst", Smoke Tests, Hypothesengetriebenes Arbeiten.
4. **Jobs-to-be-Done** — Features ≠ Nutzen. Der "Job" den das Produkt erledigt bleibt stabil.
5. **Wissenschaftliche Methode** — Hypothesen formulieren und falsifizieren statt bestätigen.

Ausführlicher Entstehungskontext und Weiterentwicklungs-Hinweise → `notes/explorations-phase-anleitung.notes.md`
