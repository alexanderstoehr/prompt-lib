# Landing Page Playbook
**Operatives Regelwerk für die Konzeption, Copy und Tracking von Lead-Generation Landingpages**

> Dieses Playbook führt durch den gesamten Prozess — vom Briefing bis zum fertigen Konzept inkl. Tracking-Spec.
> Beim Start eines neuen LP-Projekts: zuerst die Klärungsfragen stellen, dann Schritt für Schritt durcharbeiten.

---

## Inhaltsverzeichnis

1. [Klärungsfragen vor dem Start](#1-klärungsfragen-vor-dem-start)
2. [Awareness-Level bestimmen](#2-awareness-level-bestimmen)
3. [Struktur-Entscheidung](#3-struktur-entscheidung)
4. [Copy-Regeln](#4-copy-regeln)
5. [Section Build Guide](#5-section-build-guide)
6. [Formular-Strategie](#6-formular-strategie)
7. [Message Match](#7-message-match)
8. [Psychologie & Social Proof](#8-psychologie--social-proof)
9. [Tracking & Analytics](#9-tracking--analytics)
10. [QA-Checkliste](#10-qa-checkliste)
11. [Quick-Reference](#11-quick-reference)

---

## 1. Klärungsfragen vor dem Start

Vor jeder LP-Konzeption müssen diese Fragen geklärt sein. Ohne Antworten keine sinnvolle Entscheidung über Struktur, Copy oder Formular.

### Pflicht-Fragen

| # | Frage | Warum wichtig |
|---|---|---|
| 1 | Was ist das primäre Conversion-Ziel? (Lead/Formular, Anruf, Download, Termin) | Bestimmt CTA-Typ, Formular-Tiefe und Erfolgs-Definition |
| 2 | Was ist das Angebot / der Offer? Was bekommt der Besucher konkret? | Bestimmt Headline-Winkel und Formular-Intro |
| 3 | Welches Thema / welche Suchabsicht bringt den Traffic? | Bestimmt Awareness-Level und Message Match |
| 4 | Wer ist die Zielgruppe? (Demografie, Rolle, Kontext) | Bestimmt Ton, Sprache, Vertrauenssignale |
| 5 | Was ist das primäre Traffic-Medium? (Google Ads, Meta, Email, Organic) | Bestimmt Awareness-Level und Message Match |
| 6 | Was ist wichtiger: maximale Lead-Anzahl oder maximale Lead-Qualität? | Bestimmt Formular-Länge und Qualifizierungstiefe |
| 7 | Welche Einwände hat die Zielgruppe? (Top 3) | Bestimmt FAQ, Trust-Elemente und Subheadline |
| 8 | Welche Social Proof Assets sind vorhanden? (Testimonials, Logos, Zahlen, Videos) | Bestimmt Glaubwürdigkeits-Architektur |
| 9 | Handelt es sich um einen Vertrauensberuf? (Anwalt, Arzt, Berater, Finanzen) | Bestimmt Struktur-Variante (→ Abschnitt 3) |
| 10 | Welches Tracking-Tool ist im Einsatz? (GA4, GTM, Meta Pixel, eigenes System, keins) | Bestimmt Third-Party Event-Layer |

### Design-Briefing (Pflicht für Build)

| # | Input | Format |
|---|---|---|
| 1 | Primärfarbe, Akzentfarbe, Hintergrundfarbe | Hex-Codes oder Beschreibung |
| 2 | Font (Headline / Body) | Name oder "kein Vorgabe" |
| 3 | Logo | URL, File oder "noch nicht vorhanden" |
| 4 | Design-Ton | minimal/clean · warm/persönlich · corporate/seriös · bold/modern |
| 5 | 2–3 Referenz-URLs | Seiten die vom Stil her passen — müssen inhaltlich nicht verwandt sein |
| 6 | Screenshot-Referenzen einzelner Sections | Optional, aber sehr hilfreich für spezifische Elemente |

### Optionale Fragen (wenn relevant)

- Gibt es eine bestehende LP die als Basis dient oder abgelöst wird?
- Gibt es saisonale oder zeitkritische Elemente? (Countdown, limitierte Plätze)
- Gibt es eine DSGVO-Anforderung? → Beeinflusst Formular-Consent und Datenschutz-Placement
- Gibt es eine Telefonnummer die prominent sein soll? → Click-to-Call als parallele Conversion
- Was passiert nach der Conversion? (CRM, manuelles Follow-up, automatisierte Email)

---

## 2. Awareness-Level bestimmen

Das Awareness-Level bestimmt Winkel, Länge und Einstieg der gesamten Copy. Es ergibt sich aus dem Traffic-Medium und der Suchabsicht — nicht aus einem einzelnen Keyword.

### Framework (nach Eugene Schwartz)

```
PROBLEM AWARE
├── Besucher kennt sein Problem, weiss aber nicht dass es Lösungen gibt
├── Traffic: Broad Searches, kalte Social Ads, Display
├── Copy-Aufgabe: Problem benennen → Lösungskategorie einführen → Angebot positionieren
└── Copy-Länge: Lang — der Besucher muss erst überzeugt werden, dass eine Lösung existiert

SOLUTION AWARE
├── Besucher kennt Lösungsoptionen, vergleicht Anbieter
├── Traffic: Kategoriesuchen ("Steuerberater Zürich"), warme Social Ads
├── Copy-Aufgabe: Differenzierung → Warum du → Beweis
└── Copy-Länge: Mittel

PRODUCT AWARE
├── Besucher kennt dein Angebot, braucht den letzten Anstoss
├── Traffic: Brand Searches, Retargeting, Email
├── Copy-Aufgabe: Zusammenfassung → Vorteil vs. Alternative → Anreiz jetzt zu handeln
└── Copy-Länge: Kurz

MOST AWARE
├── Besucher ist kaufbereit, braucht nur Details und einfachen Weg
├── Traffic: Direct, Branded Keywords mit hohem Intent
├── Copy-Aufgabe: Gutes Angebot + klarer Weg zur Conversion
└── Copy-Länge: Sehr kurz
```

### Bestimmungs-Fragen

1. Weiss der Besucher bereits dass es für sein Problem eine Lösung gibt? → Wenn nein: Problem Aware
2. Vergleicht der Besucher aktiv verschiedene Anbieter? → Wenn ja: Solution Aware
3. Hat der Besucher bereits Kontakt mit meiner Marke gehabt? → Wenn ja: Product Aware oder Most Aware

### Wichtig: Awareness ≠ Textwüste

Mehr Copy bei Problem Aware bedeutet nicht beliebig langen Text. Jeder Abschnitt muss einen konkreten Job erledigen. Wer seinen Job nicht hat, wird gestrichen.

---

## 3. Struktur-Entscheidung

### Standard-Struktur (Universal)

Gilt für alle Branchen ausser Vertrauensberufe:

```
1.  NAVBAR
    ✅ Logo (oben links)
    ✅ Primärer Kontakt-CTA (oben rechts) — Telefon oder Button
    ❌ Keine Navigationslinks

2.  HERO
    ✅ Headline (descriptive, benefit-focused)
    ✅ Subheadline (1–2 Sätze)
    ✅ Experten- oder Produktbild (real, kein Stock)
    ✅ Social Proof above-the-fold (Sterne-Rating + Testimonial-Snippet oder Logos)
    ✅ Primärer CTA-Button

3.  PRIMÄRES FORMULAR / CTA
    ✅ Formular-Headline + Subtext
    ✅ So wenige Felder wie möglich
    ✅ Descriptiver CTA-Button
    ✅ Direktkontakt-Alternative (Telefon) wenn vorhanden
    ✅ Trust-Subtext ("Vertraulich", "Kostenlos", "2 Minuten")
    ❌ Nur EIN primärer CTA auf der gesamten Seite

4.  ZAHLENBLOCK (optional)
    ✅ 3–4 Kennzahlen (Jahre Erfahrung, Volumen, Bewertungen, Reaktionszeit)
    ✅ Nur wenn Zahlen belegbar und glaubwürdig sind

5.  PROBLEM-TEXT
    ✅ Emotionaler Einstieg: Was steht auf dem Spiel?
    ✅ Spricht den Hauptschmerzpunkt direkt an
    ✅ Max. 2 kurze Absätze

6.  TRUST-LOGOS
    ✅ Zertifikate / Verbände / Medien / Partner / bekannte Kunden
    ✅ Mit kurzer erläuternder Überschrift
    ✅ In Graustufen oder dezent

7.  HOW IT WORKS (1-2-3)
    ✅ Schritt 1: Was tut der Besucher?
    ✅ Schritt 2: Was tut das Unternehmen?
    ✅ Schritt 3: Welches Ergebnis bekommt der Besucher?

8.  ÜBER DEN EXPERTEN / DAS UNTERNEHMEN
    ✅ Persönliche, authentische Sprache
    ✅ Pull Quote mit Akzentfarbe
    ✅ ~80–100 Wörter

9.  LEISTUNG A — Text + Bild
    ✅ Kernleistung
    ✅ Bild links, Text rechts

10. LEISTUNG B — Bild + Text
    ✅ Ergänzende Leistung
    ✅ Text links, Bild rechts (alternierend)

11. TRUST SECTION
    ✅ "Warum Kunden auf [Name/Unternehmen] setzen"
    ✅ 5 Bullet Points mit Checkmarks (ungerade Zahl!)
    ✅ Dunkler Hintergrund, helle Schrift

12. VITA / CREDENTIALS
    ✅ Ausbildung, Zulassungen, Besonderheiten
    ✅ Nur wenn für diese Branche relevant

13. TESTIMONIALS
    ✅ 3 kurze Reviews (Name, Ort, Sterne, Zitat)
    ✅ 1 Featured Review (längeres Zitat, prominent)
    ✅ Echte Namen, keine Stock-Fotos
    ✅ Spezifische Ergebnisse, kein allgemeines Lob

14. FAQ
    ✅ 5 häufigste Fragen mit Antworten
    ✅ Accordion-Format
    ✅ Letzte Frage mit CTA-Hinweis abschliessen

15. FINAL CTA
    ✅ Social Proof wiederholen (Sterne)
    ✅ Klare Headline (Handlungsaufforderung)
    ✅ Primärer CTA-Button
    ✅ Telefonnummer als Alternative wenn vorhanden
    ✅ Dunkler Hintergrund

16. FOOTER
    ✅ Adresse
    ✅ Datenschutz + Impressum (als Modals, nicht neue Seiten)
    ✅ Copyright
    ❌ Keine zusätzlichen Links
    ❌ Keine Navigation
```

---

### Ausnahme: Vertrauensberufe

Gilt für: Anwälte, Ärzte, Steuerberater, Finanzberater, Therapeuten, Notare.

**Formular auf Position 6** (nach Problem-Text und Trust-Logos, nicht nach Hero).

Begründung: Vertrauen muss erst aufgebaut werden bevor der Besucher persönliche Daten eingibt. Bei Vertrauensberufen senkt ein zu frühes Formular die CR — der Besucher will erst prüfen ob dieser Anbieter überhaupt in Frage kommt.

```
1.  Navbar
2.  Hero
3.  Zahlenblock
4.  Problem-Text
5.  Trust-Logos
6.  Kontaktformular  ← verschoben
7.  How it Works
8.  Über den Experten
9.  Leistung A
10. Leistung B
11. Trust Section
12. Vita / Credentials
13. Testimonials
14. FAQ
15. Final CTA
16. Footer
```

---

### Was sich pro Nische ändert

| Element | Dienstleister | SaaS / Tech | Lokal / Handwerk |
|---|---|---|---|
| Zahlenblock | Jahre Erfahrung, Fälle | User, Uptime, Integrationen | Projekte, Bewertungen, km Radius |
| Problem-Text | Situation, Risiken | Workflow-Problem | Alltagsproblem |
| Trust-Logos | Verbände, Zertifikate, Presse | Press, G2/Trustpilot, Partner | Google-Bewertungen, lokale Referenzen |
| Leistungen | Beratungsthemen | Feature A / Feature B | Handwerksleistungen |
| FAQ | Kosten, Ablauf, Datenschutz | Pricing, Setup, Support | Preise, Termine, Garantie |
| CTA | Beratung / Formular | Free Trial / Demo | Jetzt anrufen / Formular |

### Was immer gleich bleibt

- Reihenfolge der Sections (ausser Vertrauensberufe-Ausnahme)
- Genau EIN primärer CTA auf der gesamten Seite
- Keine Navigation
- Social Proof above-the-fold (im Hero)
- Ungerade Bullet-Anzahl (3, 5 oder 7)
- Mobile-first (Sticky CTA, kein überladenes Layout)

---

## 4. Copy-Regeln

### Headline

**Der einzige Test der zählt:**
> "Wenn der Besucher ausschliesslich die Headline liest — weiss er genau was er bekommt?"

Wenn nicht: neu schreiben.

**Regeln:**
- Descriptiv und spezifisch — keine Slogans
- Benefits, nicht Features
- Einfache Sprache (Leseniveau: 5.–7. Klasse)
- Keine vagen Versprechen ("besser", "professionell", "revolutionär")
- Keine übertriebenen Claims die unglaubwürdig klingen

**Headline-Entwicklungsprozess:**
1. Was tut der Besucher heute OHNE dein Angebot? (die schlechte Alternative)
2. Was ist dein konkreter Vorteil dagegen?
3. In eine Aussage bringen — mit spezifischer Zahl wenn möglich
4. Objection einbauen wenn die Zielgruppe einen grossen Einwand hat

**Bewährte Formeln:**

| Formel | Beispiel |
|---|---|
| Direkte Aussage + spezifisches Ergebnis | "Immobilienbewertung in 3 Minuten — kostenlos und verbindlich" |
| Problem lösen ohne Hürde | "Steuererklärung erledigt. Ohne Termin, ohne Warterei." |
| Vergleich mit schlechter Alternative | "Kein Makler. Trotzdem Bestpreis." |
| Zeitversprechen mit Glaubwürdigkeits-Anker | "Anwaltliche Erstberatung innerhalb von 24h" |
| Zielgruppe + Job + Ergebnis | "Für KMU: Buchhaltung die läuft — ohne eigene Buchhalterin" |

### Subheadline

- 1–2 Sätze, nicht mehr
- Erklärt: Wie funktioniert das? Oder: Was macht den Bold Claim glaubwürdig?
- Formel: [Was es ist] + [Wie der Claim möglich ist]

### Copy-Länge

Keine feste Wortzahl. Die richtige Länge ergibt sich aus dem Awareness-Level:

| Awareness | Richtlinie |
|---|---|
| Problem Aware | Lang — Problem elaborieren, Lösung einführen, Angebot rechtfertigen |
| Solution Aware | Mittel — Differenzierung und Beweis im Fokus |
| Product Aware | Kurz — Zusammenfassung + Anreiz |
| Most Aware | Sehr kurz — Angebot + einfacher Weg |

**Regel:** Jeder Abschnitt muss einen Job haben. Wer keinen hat, wird gestrichen — unabhängig von der Länge.

### Bullet Points

- Immer ungerade Anzahl: 3, 5 oder 7 (gerade Zahlen konvertieren schlechter)
- Ausschliesslich Benefits (nicht Features)
- Schlüsselwörter fett
- Kurz und konkret — kein Satz der länger als eine Zeile ist

### CTA-Button Text

| ❌ Schlecht | ✅ Gut |
|---|---|
| Absenden | Jetzt kostenlos anfragen |
| Weiter | Angebot anfordern |
| Anmelden | Kostenlose Bewertung starten |
| Kontakt | Rückruf vereinbaren |

**Regel:** Der CTA-Text setzt die Headline fort. Er sagt was passiert wenn man klickt — nicht was der Button "tut".

**Emoji im CTA:** Hilfreich für Consumer und Mid-Market. Weglassen bei Vertrauensberufen und hochpreisigem B2B (wirkt unprofessionell).

### Direktionale Cues (Formular)

Unter dem CTA-Button oder vor dem Formular:
- "Kostenlos, unverbindlich, 2 Minuten"
- "Wir melden uns innerhalb von 24h"
- "Ihre Daten werden vertraulich behandelt und nicht weitergegeben"

---

## 5. Section Build Guide

Für jede Section: was Claude beim Build produziert und worauf zu achten ist.

### Section 1 — Navbar

- Logo links, CTA rechts (Telefon oder Button)
- Bei Urgency/Scarcity: Text in der Mitte oder unter dem Logo
- Kein weiteres Element
- Auf Mobile: Sticky Navbar mit CTA immer sichtbar

### Section 2 — Hero

Die wichtigste Section. Entscheidet ob der Besucher bleibt oder geht.

**Aufbau:**
- Headline (nach Copy-Regeln)
- Subheadline (1–2 Sätze)
- Hero-Bild: Experte, Produkt in Verwendung oder Ergebnis — real, kein Stock
- Social Proof: Sterne-Rating + kurzes Testimonial-Snippet ODER Logo-Bar mit bekannten Marken/Medien
- Primärer CTA oder erster Schritt des Formulars

**Mobile:** CTA muss above-the-fold sichtbar sein ohne zu scrollen.

### Section 3 — Primäres Formular / CTA

Direkt nach dem Hero — maximale Aufmerksamkeit.

**Aufbau:**
- Formular-Headline: "Jetzt [Offer] erhalten" oder ähnlich
- Subtext: Was passiert nach dem Ausfüllen?
- Formular (Feld-Strategie → Abschnitt 6)
- CTA-Button
- Trust-Subtext darunter

**Alternativ wenn Formular unten:** Grosser CTA-Button der zum Formular ankert.

### Section 4 — Zahlenblock

3–4 Kennzahlen in visuell hervorgehobenen Blöcken.

- Nur verwenden wenn Zahlen belegbar sind
- Format: Grosse Zahl + kurze Beschreibung ("15 Jahre Erfahrung", "4.9/5 Sterne", "500+ Kunden")
- Kein Zahlenblock wenn keine überzeugenden Zahlen vorhanden → Section weglassen

### Section 5 — Problem-Text

Emotionaler Einstieg — spricht den Schmerzpunkt direkt an.

- Beginnt mit der Situation des Besuchers, nicht mit dem Unternehmen
- Max. 2 Absätze, max. ~80–100 Wörter
- Endet mit einer Aussage die den Übergang zur Lösung einleitet

### Section 6 — Trust-Logos

- Überschrift: "Bekannt aus" / "Zertifiziert durch" / "Vertrauen von" — nie nur "Partner"
- Logos in Graustufen (wirkt professioneller, kein visuelles Chaos)
- Minimum 3, idealerweise 5–8 Logos

**Daten:** Client-Logo-Bar erhöht CR in Tests um bis zu 69%.

### Section 7 — How it Works

Drei Schritte, visuell klar getrennt:
- Schritt 1: Was tut der Besucher? (niedrige Einstiegshürde kommunizieren)
- Schritt 2: Was passiert dahinter?
- Schritt 3: Was bekommt der Besucher am Ende?

Kein Step darf länger als 2 Sätze sein.

### Section 8 — Über den Experten / das Unternehmen

- Authentische, persönliche Sprache — kein Unternehmens-Blurb
- Bild des Experten oder Teams (real)
- Pull Quote in Akzentfarbe: das stärkste Zitat aus dem Text herausnehmen
- ~80–100 Wörter

### Sections 9 + 10 — Leistungen

- Jeweils: Headline + 2–3 Sätze + Bild/Visual
- Sections alternieren: Bild links / Bild rechts
- Visuals: echte Bilder oder GIFs in Verwendung, keine Stock-Fotos
- Running Narrative: jede Leistung bezieht sich zurück auf die Hero-Value-Prop

### Section 11 — Trust Section

- Überschrift: "Warum Kunden [Unternehmen] wählen"
- 5 Bullet Points mit Checkmark-Icon (ungerade!)
- Jeder Punkt: 1 fette Kernaussage + 1 Erklärungssatz
- Dunkler Hintergrund, helle Schrift

### Section 12 — Vita / Credentials

- Ausbildung, Zulassungen, Mitgliedschaften, Auszeichnungen
- Sprachen falls relevant
- Nur bei Vertrauensberufen oder wenn Credentials ein Differenzierungsmerkmal sind
- Sonst: Section weglassen

### Section 13 — Testimonials

**Anforderungen an Testimonials:**
- Echter Name + Ort (nicht "M.S. aus Zürich")
- Echtes Foto (kein Avatar, kein Stock)
- Spezifisches Ergebnis — nicht "Toller Service" sondern "Wohnung innerhalb von 3 Wochen verkauft"

**Format:**
- 3 kurze Reviews (2–3 Sätze) + Sterne
- 1 Featured Review prominent herausgehoben (4–6 Sätze)

**Daten:**
- Ab 10 Reviews: erste echte Glaubwürdigkeit
- Ab 50 Reviews: +4.6% CR vs. <10 Reviews
- 0.1 Sterne mehr = +4.4% CR (Uberall-Studie)
- 4.5 Sterne mit 100 Reviews > 5.0 Sterne mit 10 Reviews (wirkt echter)

### Section 14 — FAQ

- 5 häufigste echte Fragen (aus Sales-Gesprächen, Support, Kundenemails)
- Accordion-Format
- Jede Antwort 2–4 Sätze
- Letzte Frage = letzter Einwand vor der Conversion ("Was kostet das?" / "Wie schnell geht es?") — endet mit CTA-Hinweis

### Section 15 — Final CTA

- Dunkler Hintergrund (Kontrast zum Rest der Seite)
- Social Proof wiederholen: Sterne-Rating + kurze Zahl ("von 500+ Kunden")
- Klare Handlungsaufforderung als Headline
- Primärer CTA-Button
- Telefonnummer als Alternative wenn vorhanden

### Section 16 — Footer

- Adresse
- Datenschutz + Impressum als Modals (nicht neue Seiten — vermeidet Navigation weg von der LP)
- Copyright
- Nichts sonst

---

## 6. Formular-Strategie

### Entscheidung: Single Form vs. Multi-Step

```
Anzahl benötigter Felder?
│
├── 1–5 Felder
│   └── Single Form (direkt im Playbook geregelt)
│
└── 6+ Felder
    └── Multi-Step → Wizard-Ruleset (forms/wizard-ruleset.md)
```

**Daten:** Multi-Step Forms konvertieren bei 6+ Feldern deutlich besser als Single Forms.
Fallbeispiel: Single Form 0.96% → Multi-Step 8.1% (+743%) (Venture Harbour).

### Single Form — Regeln

**Feldstrategie:**
- So wenige Felder wie möglich — jedes zusätzliche Feld kostet CR
- Reihenfolge: einfachste Felder zuerst (Name, Thema/Interesse) → Email → Telefon zuletzt
- Email früh abfragen: wenn der Besucher vorher abbricht, hat man trotzdem eine Kontaktmöglichkeit

**Telefonnummer:**
- Grösster einzelner Conversion-Killer im Formular
- Datenpunkte: -5% bis -47% CR je nach Studie
- Wenn möglich: optional machen oder in Multi-Step nach hinten schieben
- Wenn Pflicht: im letzten Schritt nach allem anderen

**Anzahl Felder:**
- Maximale Lead-Anzahl: 3 Felder (Name, Email, ggf. Thema)
- Maximale Lead-Qualität: 5–7 Felder (inkl. Qualifizierungsfragen) → dann Multi-Step prüfen

**Qualifizierungsfragen:**
- Nur wenn Sales-Team auf Qualität angewiesen ist
- Als Auswahl-Buttons (nicht Freitext) — weniger Reibung
- Vor den Kontaktdaten platzieren

**Trust-Elemente beim Formular:**
- Privacy Statement direkt beim CTA-Button: "Ihre Daten werden vertraulich behandelt und nicht weitergegeben"
- Ggf. Garantie oder Risikoentlastung: "Kostenlos und unverbindlich"

### Click-to-Call als parallele Conversion (Mobile)

Bei lokalem Traffic oder wenn die Zielgruppe Telefon bevorzugt:
- Telefonnummer prominent neben oder unter dem Formular
- Auf Mobile: als klickbarer Link (`tel:`) der direkt wählt
- Separat tracken — Click-to-Call ist eine vollwertige Conversion, kein Fallback

---

## 7. Message Match

### Was Message Match bedeutet

Der Besucher klickt ein Ad und landet auf der LP. In den ersten 3 Sekunden prüft er unbewusst: "Bin ich am richtigen Ort?"

Message Match stellt sicher dass die Antwort immer "Ja" ist — auf drei Ebenen:

| Ebene | Beschreibung | Fehler-Beispiel |
|---|---|---|
| **Textuell** | Kernaussage und Formulierungen aus dem Ad spiegeln sich in der LP-Headline | Ad: "Steuererklärung für Selbständige" → LP: "Willkommen bei [Firma]" |
| **Visuell** | Farben, Bildstil und Tonalität aus dem Ad finden sich auf der LP | Professionelles Ad-Visual → generisches Stock-Foto auf der LP |
| **Intent** | Das Angebot auf der LP entspricht dem was der Besucher aus dem Ad erwartet | Ad verspricht "kostenlose Bewertung" → LP zeigt nur allgemeinen Service |

### Praktische Umsetzung

1. **Headline** muss die Kernaussage des Ads aufnehmen — nicht wortwörtlich, aber erkennbar
2. **Offer** muss identisch sein: Was im Ad versprochen wird, muss auf der LP sofort sichtbar sein
3. **Tone** muss übereinstimmen: Wenn das Ad direkt und schnörkellos ist, darf die LP nicht corporate sein
4. **Visual** muss eine ähnliche Atmosphäre haben: nicht notwendigerweise das gleiche Bild, aber die gleiche Welt

### Bei mehreren Ads / Zielgruppen

Wenn verschiedene Ads auf dieselbe LP laufen:
- LP auf den breitesten gemeinsamen Nenner ausrichten (nicht auf ein einzelnes Ad)
- Oder: separate LP-Varianten pro Ad-Gruppe (höherer Aufwand, bessere CR)

### Direkte Check-Frage vor dem QA

> "Wenn ich das Ad sehe und dann auf die LP komme — merke ich sofort dass ich am richtigen Ort bin?"

Wenn nicht: Headline oder Offer stimmt nicht überein.

---

## 8. Psychologie & Social Proof

### AIDA-Journey auf der LP

Die gesamte LP-Struktur folgt einer psychologischen Reise:

| Phase | Section | Aufgabe |
|---|---|---|
| **Attention** | Hero | Sofort klar machen: "Das bin ich, das ist für dich" |
| **Interest** | How it Works + Leistungen | Wie funktioniert es, was bekomme ich? |
| **Desire** | Testimonials + Trust Section | Andere haben es getan und es hat funktioniert |
| **Action** | Final CTA | Letzter Anstoss, alle Einwände ausgeräumt |

### FOMO & Urgency

Nur einsetzen wenn real und glaubwürdig:
- Limitierte Plätze: "Noch 3 freie Termine im April"
- Deadline: "Angebot gilt bis Freitag"
- Soziale Bestätigung: "Über 500 Anfragen diesen Monat"

**Platzierung:** Navbar rechts, beim CTA, im Final CTA.

**Regel:** Fake-Urgency wird erkannt und zerstört Vertrauen — nur einsetzen wenn es stimmt.

### Social Proof — Hierarchie

Von stärkster zu schwächster Wirkung für Lead Gen:

1. **Fallstudie mit messbarem Ergebnis** — Named client + konkretes Ergebnis
2. **Video-Testimonial** — deutlich überzeugender als Text, besonders für höherpreisige Angebote
3. **Text-Testimonial mit echtem Foto** — Name, Ort, Rolle, spezifisches Ergebnis
4. **Client-Logo-Bar** — +69% CR in A/B Tests, schnell zu implementieren
5. **Zahlen** — "500+ Kunden", "4.9/5 bei 200 Bewertungen"
6. **Review-Badges** (Google, Trustpilot) — besonders wirkungsvoll für lokale Services

**Platzierung:**
- Above-the-fold: Logo-Bar oder Sterne-Rating — reduziert initiale Skepsis
- Beim Formular: 1 starkes Testimonial — reduziert letzte Zweifel vor der Conversion
- Beide Positionen gleichzeitig übertreffen jeweils eine alleine

### Trust-Elemente

| Element | Wirkung | Platzierung |
|---|---|---|
| Privacy Statement | Reduziert Formular-Abbruch deutlich | Direkt unter CTA-Button |
| Garantie-Badge | +32.5% in Tests bei digitalem Angebot | Beim Formular |
| SSL / Sicherheits-Badge | Hygiene-Faktor — Abwesenheit kostet | Footer, ggf. beim Formular |
| Zertifikate / Verbände | Vertrauensberufe: wichtig | Section 6 (Trust-Logos) |

**Regel:** Bei Lead Gen ist ein klares Privacy-Statement neben dem Formular wirksamer als ein Security-Badge. Besucher wollen wissen was mit ihren Daten passiert — nicht ob die Verbindung verschlüsselt ist.

---

## 9. Tracking & Analytics

> **LP-Tracking ist Optimierungs-Infrastruktur — kein Add-on.**
> Eine LP ohne vollständiges Tracking ist nicht optimierbar.

### Grundprinzip: Server-First by Default

**Empfehlung:** Eigenes Server-Side Tracking (eigene DB) als Primärsystem.

**Warum:**
- Kein Ad-Blocker kann es blockieren
- Volle Datenkontrolle
- Ermöglicht Multi-Session Tracking (Wiederkehrende Besucher)
- Grundlage für Hypothesen-System und A/B-Tests
- Enhanced Conversions für Google Ads ohne Third-Party-Abhängigkeit

**Third-Party Tools** (GA4, GTM, Meta Pixel, Google Ads Conversion):
- Werden **zusätzlich** eingebunden wenn das Projekt es verlangt
- Ersetzen nie das eigene Tracking — nur ergänzen
- Was an Third-Party geht: nur das was für den jeweiligen Zweck nötig ist

**Wenn kein eigenes Server-Side Tracking:** GTM als Minimum-Setup, alle Events als Custom Events dokumentiert.

---

### Zwei-Phasen-Architektur

```
Phase 1: LP (jeder Besucher)        Phase 2: Formular (Formular gestartet)
─────────────────────────           ──────────────────────────────────────
visit_events Tabelle                form_events / session_events Tabelle
        │                                         │
        └──────────── visit_id ───────────────────┘
```

Beide Phasen sind über eine `visit_id` verknüpft die bei Seitenaufruf generiert wird. So ist jeder Lead am Ende einem Besuchsverhalten zuordenbar.

---

### Phase 1: LP-Events (jeder Besucher)

| Event | Daten | Warum |
|---|---|---|
| `page_view` | utm_source, utm_medium, utm_campaign, utm_content, gclid, fbclid, device_type, referrer | Attribution: woher kommt der Traffic, von welcher Kampagne? |
| `section_visible` | section_name, viewport_percent | Welche Sections sieht der Besucher tatsächlich? |
| `section_duration` | section_name, duration_ms | Wo bleibt er, wo scrollt er durch? Engagement-Qualität pro Section |
| `scroll_depth` | 25 / 50 / 75 / 100% | Kommt er überhaupt zum Formular oder Final CTA? |
| `cta_visible` | cta_id, location | Sieht der Besucher den CTA (above fold?) |
| `cta_hover` | cta_id, hover_ms | Interesse ohne Klick = Copy-Problem oder Unsicherheit |
| `cta_click` | cta_id, location (hero / mid / final) | Welcher CTA konvertiert? |
| `phone_click` | location | Click-to-Call als separate Conversion — besonders Mobile |
| `form_visible` | above_fold, time_to_visible_ms | Wird das Formular sofort gesehen? |
| `form_no_interaction` | visible_duration_ms | Formular >10s sichtbar ohne Interaktion = Einstiegs-Problem |
| `attention_ping` | active: bool | Alle 5s: ist der Besucher wirklich aktiv? (Maus/Touch) |
| `performance` | fcp_ms, lcp_ms, dom_ready_ms, cta_above_fold | Ladezeit-Impact — jede Sekunde kostet ~7% CR |
| `page_leave` | total_time_ms, active_time_ms, max_scroll_pct, sections_seen, last_section | Exit-Zusammenfassung: was hat der Besucher gesehen? |

---

### Phase 2: Formular-Events

#### Single Form

| Event | Daten | Warum |
|---|---|---|
| `form_start` | timestamp | Erste Formular-Interaktion — Funnel-Einstieg |
| `form_field_focus` | field_name | Welche Felder werden berührt? |
| `form_field_complete` | field_name, duration_ms | Welche Felder werden abgeschlossen, wie lange dauert es? |
| `form_field_error` | field_name, error_type, attempt_n | Felder mit >15% Error-Rate müssen überarbeitet werden |
| `form_submit_attempt` | fields_filled | Button geklickt — inkl. Validation-Fehler davor |
| `form_submit_success` | — | Macro-Conversion — feuert nach erfolgreichem Submit, nie davor |
| `form_submit_error` | error_type | Technische Fehler die direkte CR-Verluste verursachen |
| `form_abandon` | last_active_field, fields_touched, time_in_form_ms | Abbruch nach form_start — welches Feld war zuletzt aktiv? |

#### Multi-Step Form

→ Wizard-Ruleset (`forms/wizard-ruleset.md`) Section 13

Das Wizard-Ruleset enthält das vollständige Step-Level Tracking inkl. field_hesitation, step_back, autocomplete-Tracking und korrekter Abbruch-Erkennung per `current_step` statt letztem `field_focus`.

---

### Google Ads / Third-Party Layer

Wenn Google Ads im Einsatz:

**Primary Conversion:** Formular erfolgreich abgesendet
```
event: 'conversion'
send_to: [Conversion Label]
value: [definierter Lead-Wert in CHF/EUR]
currency: 'CHF'
user_data: { email, phone_number, address } ← Enhanced Conversions
```

**Secondary Conversion (optional):** Besucher hat Kontaktdaten eingegeben aber nicht abgesendet
```
event: 'conversion'
send_to: [Sekundärer Conversion Label]
value: [~30% des primären Werts]
```

**Enhanced Conversions:** user_data (Email, Telefon, Name, PLZ) wird von gtag.js automatisch SHA-256-gehasht. Muss einmalig in Google Ads aktiviert werden. Verbessert Matching-Rate erheblich.

**Regel:** Enhanced Conversions Setup immer dokumentieren — sie scheitern lautlos wenn das Format falsch ist.

---

### Abgeleitete Metriken (berechnet, nicht direkt getrackt)

| Metrik | Berechnung | Erkenntnis |
|---|---|---|
| Aufmerksamkeitszeit | Summe active attention_pings × 5s | Echter Engagement vs. Tab offen lassen |
| Section Engagement Score | (sections_seen / total_sections) × (active_time / total_time) | Qualität des Besuchs |
| Bounce ohne Scroll | page_leave mit max_scroll < 10% | Hero oder Ladezeit ist das Problem |
| Formular-CR | form_submit_success / page_view | Kern-KPI der LP |
| Formular-Completion-Rate | form_submit_success / form_start | Formular-Qualität |
| CTA-Efficiency | cta_click / cta_visible | Schwacher Wert = Copy-Problem |

---

### Konfidenz-Schwellen

Bei kleinen Traffic-Volumen führen Daten schnell zu falschen Schlüssen. Jede Erkenntnis braucht eine Konfidenz-Einschätzung:

| Stufe | Bedeutung | Kommunikation |
|---|---|---|
| 🔴 Insufficient | Unter Minimum — keine Aussage möglich | "Zu wenig Daten" |
| 🟡 Minimum | Tendenz erkennbar, aber noch unsicher | "Tendenz sichtbar (X%), aber am Minimum" |
| 🟢 Optimum | Belastbare Aussage | "Belastbar: n=X, Y% der Besucher..." |

| Aussage-Typ | Minimum n | Optimum n |
|---|---|---|
| Section-Sichtbarkeit | 30 Visits | 100 Visits |
| Scroll-Tiefe | 30 Visits | 100 Visits |
| Formular-Start-Rate | 30 Visits | 100 Visits |
| Feld-Abbruchrate | 15 Abbrecher am Feld | 40 Abbrecher |
| Converter vs. Abbrecher Vergleich | 10 Converter + 20 Abbrecher | 30 + 60 |
| A/B-Test signifikant | 50 pro Variante | 200 pro Variante |

**Regel:** Hypothesen werden erst bei `minimum`-Konfidenz als bestätigt/widerlegt gewertet — nie bei `insufficient`.

---

### A/B-Testing

**Vorbereitung:** Jeder Visit bekommt eine Variante (`A` oder `B`) zugewiesen — deterministisch basierend auf `visit_id` (kein Cookie nötig). Variante wird auf alle Events geschrieben.

**Test-Reihenfolge (Priorität):**
1. Headline (grösster Hebel)
2. CTA-Text und Position
3. Hero-Bild
4. Formular-Länge und Feldsequenz
5. Social Proof Platzierung
6. Einzelne Section-Reihenfolge

**Regeln:**
- Immer nur eine Variable gleichzeitig testen
- Mindestens 1 Woche laufen lassen (Wochentag-Varianz)
- Variante als Dimension in alle Events schreiben — nur so ist der Test auf LP-Ebene auswertbar

---

### Typische Diagnose-Muster

**Viele Besucher, wenig Formular-Starts:**
→ Hero oder CTA ist das Problem
→ cta_hover ohne cta_click prüfen (Unsicherheit / Copy)
→ form_no_interaction prüfen (Formular gesehen aber ignoriert)
→ Scroll Depth: kommen Besucher überhaupt zum Formular?

**Formular-Starts, wenig Submits:**
→ form_abandon → last_active_field zeigt den Blocker
→ Telefonnummer als last_active_field = klassischer Conversion-Killer → optional machen
→ form_field_error Rate > 15% = Feld unklar → überarbeiten

**Hoher Bounce (page_leave mit max_scroll < 10%):**
→ Message Match prüfen: stimmt Headline mit Traffic-Quelle überein?
→ Ladezeit prüfen: performance Event → lcp_ms
→ Hero-Bild: irrelevant oder Stock-Foto?

---

## 10. QA-Checkliste

Vor der Übergabe / vor dem Go-Live:

### Struktur
- [ ] Standard- oder Vertrauensberufe-Struktur korrekt angewendet?
- [ ] Genau EIN primärer CTA auf der gesamten Seite
- [ ] Keine Navigationslinks vorhanden
- [ ] Social Proof above-the-fold (Hero)
- [ ] FAQ vorhanden (5 Fragen)
- [ ] Datenschutz/Impressum als Modals (nicht neue Seiten)

### Copy
- [ ] Headline besteht Litmus-Test: Besucher weiss nach der Headline genau was er bekommt?
- [ ] Subheadline max. 2 Sätze
- [ ] Keine Slogans, kein Corporate Speak
- [ ] Alle Bullet-Listen: ungerade Anzahl (3, 5, 7)
- [ ] CTA-Text descriptiv (nicht "Absenden" oder "Weiter")
- [ ] Direktionale Cues unter dem CTA vorhanden

### Message Match
- [ ] Headline nimmt Kernaussage des Ads auf
- [ ] Offer auf der LP = Offer im Ad
- [ ] Tonalität konsistent (Ad ↔ LP)

### Formular
- [ ] So wenige Felder wie möglich
- [ ] Feldsequenz: einfach → sensitiv (Telefon zuletzt)
- [ ] Privacy Statement direkt beim CTA
- [ ] Bei 6+ Feldern: Multi-Step eingesetzt?

### Social Proof
- [ ] Echte Fotos (kein Stock, kein Avatar)
- [ ] Echte Namen (kein "M.S. aus Zürich")
- [ ] Spezifische Ergebnisse (kein allgemeines Lob)
- [ ] Client-Logo-Bar vorhanden?
- [ ] Rating-Score und Anzahl sichtbar?

### Mobile
- [ ] CTA above-the-fold sichtbar ohne zu scrollen
- [ ] Sticky CTA implementiert
- [ ] Click-to-Call verlinkt (`tel:`) wenn Telefonnummer vorhanden
- [ ] Formular-Felder tap-friendly

### Tracking
- [ ] page_view mit UTM-Parametern und visit_id implementiert?
- [ ] section_visible für alle relevanten Sections?
- [ ] cta_click für alle CTAs?
- [ ] form_start, form_submit_success, form_abandon implementiert?
- [ ] sendBeacon für Abandon- und Submit-Events?
- [ ] Phone-Click getrackt?
- [ ] Google Ads Conversion Event implementiert (wenn Ads im Einsatz)?
- [ ] Enhanced Conversions konfiguriert (user_data Format korrekt)?
- [ ] Datenschutz: werden Tracking-Daten konform behandelt?

---

## 11. Quick-Reference

### Awareness → Copy-Länge

| Awareness | Traffic | Copy |
|---|---|---|
| Problem Aware | Kalt, Broad | Lang: Problem → Lösung → Angebot |
| Solution Aware | Kategorie-Suche | Mittel: Differenzierung + Beweis |
| Product Aware | Retargeting, Brand | Kurz: Zusammenfassung + Anreiz |
| Most Aware | Direct, Brand-Intent | Sehr kurz: Angebot + Weg |

### CR-Benchmarks (Google Ads, Referenzwerte)

| Industrie | Durchschnitt | Top 10% |
|---|---|---|
| Lokale Dienstleister | 7–10% | 15%+ |
| Legal / Anwälte | 5–10% | 15%+ |
| Finance & Insurance | 2–3% | 8%+ |
| B2B SaaS | ~4% | 10%+ |
| Alle Branchen (Median) | 6.6% | 11.5%+ |

Quelle: Unbounce Q4 2024 (464 Mio. Visits), WordStream 2025

### Formular-Entscheidung

```
1–5 Felder → Single Form
6+ Felder  → Multi-Step → forms/wizard-ruleset.md
```

### Kritische Zahlen

| Fakt | Zahl | Quelle |
|---|---|---|
| Telefonnummer-Feld Conversion-Kosten | −5% bis −47% | Mehrere CRO-Studien |
| Client-Logo-Bar Uplift | +69% in A/B Test | KlientBoost |
| Multi-Step Uplift (Fallbeispiel) | +743% (0.96% → 8.1%) | Venture Harbour |
| Ladezeit-Kosten | −7% CR pro Sekunde | Mehrere Quellen |
| Sticky CTA Mobile Uplift | +15–25% | Branchen-Konsens |
| Guarantee Badge Uplift | +32.5% | Unbounce Case Study |
| Rating: 0.1 Stern mehr | +4.4% CR | Uberall-Studie |

### Struktur-Entscheidung

```
Vertrauensberuf? (Anwalt, Arzt, Berater, Finanz)
├── Ja  → Formular auf Position 6 (nach Problem + Trust-Logos)
└── Nein → Formular auf Position 3 (direkt nach Hero)
```

### Tracking-Minimum

Kein LP-Launch ohne:
- `page_view` (mit UTM + visit_id)
- `cta_click`
- `form_start`
- `form_submit_success`
- `form_abandon` (via sendBeacon)

---

*Entstehungskontext, Implementierungsreferenzen und weiterführende Notizen → `notes/lp-playbook.notes.md`*
