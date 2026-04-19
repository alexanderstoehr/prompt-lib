---
name: Wizard Ruleset
command: wizard-ruleset
phase: forms
description: Operatives Regelwerk für die Konzeption und Umsetzung von mehrstufigen Formularen.
tags: [forms, wizard, ux]
inject: false
---

# Wizard Ruleset
**Operatives Regelwerk für die Konzeption und Umsetzung von mehrstufigen Formularen**

> Dieses Dokument ist eine Arbeitsgrundlage. Beim Erstellen eines neuen Wizards: zuerst die Klärungsfragen stellen, dann die Entscheidungsmatrizen durchlaufen, dann bauen.

---

## Inhaltsverzeichnis

1. [Klärungsfragen vor dem Start](#1-klärungsfragen-vor-dem-start)
2. [Wizard-Typ bestimmen](#2-wizard-typ-bestimmen)
3. [Rendering-Modus wählen](#3-rendering-modus-wählen)
4. [Struktur & Step-Anzahl](#4-struktur--step-anzahl)
5. [Fragen-Sequenz & Feldstrategie](#5-fragen-sequenz--feldstrategie)
6. [Input-Typen](#6-input-typen)
7. [UI/UX Design-Regeln](#7-uiux-design-regeln)
8. [Mobile-Regeln](#8-mobile-regeln)
9. [Psychologie-Prinzipien & ihre Anwendung](#9-psychologie-prinzipien--ihre-anwendung)
10. [Validation & Fehler](#10-validation--fehler)
11. [Trust & Datenschutz](#11-trust--datenschutz)
12. [LP-Integration: Form im Kontext der Landingpage](#12-lp-integration-form-im-kontext-der-landingpage)
13. [Tracking & Analytics](#13-tracking--analytics)
14. [Post-Submit](#14-post-submit)
15. [Accessibility](#15-accessibility)
16. [Konflikte & Trade-offs](#16-konflikte--trade-offs)
17. [Quick-Reference](#17-quick-reference)

---

## 1. Klärungsfragen vor dem Start

Vor jeder Wizard-Konzeption müssen diese Fragen geklärt sein. Ohne Antworten keine sinnvolle Entscheidung über Struktur, Modus oder Sequenz.

### Pflicht-Fragen

| # | Frage | Warum wichtig |
|---|---|---|
| 1 | Was ist das primäre Ziel? (Lead, Termin, Diagnose, Kauf, Onboarding) | Bestimmt Modus, Step-Anzahl, CTA |
| 2 | Wie viel Traffic kommt von Mobile? **Schwellenwert: unter 40% → Desktop-first. 40–60% → beide gleichwertig. Über 60% → Mobile-first, Conversational prüfen.** | Bestimmt Felder pro Step, Input-Typen, Modus |
| 3 | Was ist wichtiger: maximale Completion Rate oder maximale Lead-Qualität? | Bestimmt Email-Platzierung und Feldanzahl |
| 4 | Wie viele Informationen müssen abgefragt werden? (grobe Anzahl Felder – bei Branching: maximale Felder im längsten Pfad) | Bestimmt Step-Anzahl und ob Single-Step überhaupt sinnvoll ist |
| 5 | Gibt es Branching-Bedarf? (Antworten beeinflussen Folgefragen) | Bestimmt Wizard-Typ |
| 6 | Gibt es einen Action-Step? (API-Call, Analyse, Suche innerhalb des Wizards) | Bestimmt ob Hybrid-Typ nötig ist – unabhängig von Feldanzahl |
| 7 | Welchen Ton hat die Zielgruppe? (B2B/nüchtern vs. Consumer/emotional) | Bestimmt Modus und Copy-Stil |
| 8 | Gibt es eine Paywall, einen Gate oder einen Upsell am Ende? | Beeinflusst Step-Aufbau und Commitment-Aufbau |
| 9 | Wo wird der Wizard eingebettet? (LP, eigene Page, Fullscreen-Overlay, App) | Bestimmt Container-Format |
| 10 | Gibt es bestehende Brand-Guidelines (Farben, Fonts, Ton)? | Bestimmt visuelles System |
| 11 | Verlangt das Projekt ein spezifisches Tracking-Tool? (GA4, GTM, Meta Pixel, etc.) | Bestimmt ob Third-Party Events zusätzlich gesendet werden müssen |

### Optionale Fragen (wenn relevant)

- Gibt es Wiederkehrende User? → Progressive Profiling möglich
- Ist das ein B2B oder B2C Kontext? → Beeinflusst Feldanzahl und Qualifizierungstiefe
- Gilt für dieses Projekt eine Datenschutzverordnung? (DSGVO/EU, CCPA/USA, PDPA/Asien, etc.) → Falls ja: Consent-Placement und Follow-up-Regeln entsprechend anpassen. Falls nein: Standard-Datenschutzhinweis reicht. **Nicht jedes Projekt ist DSGVO-pflichtig – immer projektspezifisch klären.**
- Was passiert nach dem Submit? (CRM-Integration, Sales-Team, automatisierte Email?) → Beeinflusst welche Felder zwingend nötig sind

---

## 2. Wizard-Typ bestimmen

### Entscheidungsmatrix

```
Gibt es einen API/Analyse-Step innerhalb des Wizards?
(unabhängig von der Feldanzahl)
│
├── Ja → HYBRID WIZARD
│         (kann zusätzlich Linear oder Branching sein)
│
└── Nein → weiter zur Feldanzahl-Verzweigung
           │
           ├── Weniger als 5 Felder
           │   └── Gibt es Branching?
           │       ├── Nein → SINGLE-STEP FORM (kein Wizard nötig)
           │       └── Ja   → MINIMAL BRANCHING WIZARD (2-3 Steps)
           │
           ├── 5 bis 15 Felder
           │   └── Gibt es Branching?
           │       ├── Nein → LINEAR WIZARD
           │       └── Ja   → BRANCHING WIZARD
           │
           └── Mehr als 15 Felder
               └── BRANCHING WIZARD (mit Conditional Logic)
```

### Typ-Beschreibungen

**Single-Step Form**
Alle Felder auf einer Seite. Nur sinnvoll bei bis zu 5 Feldern ohne Branching. Für Newsletter, einfache Kontaktformulare, schnelle Anmeldungen.

**Linear Wizard**
Schritt für Schritt, jede Antwort führt zum nächsten Step, keine Verzweigungen. Ideal für Leadgen-Formulare mit klarem Funnel (Waxing-Studio, einfache Terminbuchung).

**Minimal Branching Wizard**
Wenige Felder (unter 5), aber Antworten beeinflussen den nächsten Step. Zwei bis drei Steps, einfache Verzweigung. Beispiel: Geschlecht → zwei verschiedene Folgefragen.

**Branching Wizard**
Antworten bestimmen den nächsten Step. Irrelevante Fragen werden übersprungen. Pflicht bei unterschiedlichen Zielgruppen innerhalb desselben Formulars (z.B. B2B vs. B2C → andere Qualifizierungsfragen).

**Hybrid Wizard**
Teils Dateneingabe, teils passiert etwas innerhalb des Wizards (API-Call, Suche, Analyse, Berechnung) – unabhängig davon wie viele Felder der Wizard hat. Der Action-Step ist ein eigener Step-Typ mit Loading State. Beispiel: Google-Bewertung suchen (3 Felder) → analysieren → Löschvorschlag → Paywall.

---

## 3. Rendering-Modus wählen

Der Modus bestimmt wie der Wizard aussieht und sich anfühlt – nicht was er abfragt. Gleiche Step-Config, unterschiedliche Darstellung. Alle drei sollten A/B-testbar sein.

> **Hinweis zur Terminologie:** Der mittlere Modus heißt hier "Standard" um Verwechslung mit dem Oberbegriff "Wizard" zu vermeiden.

### Entscheidungsmatrix

| Frage | Ergebnis |
|---|---|
| B2B, Power User, strukturierte Daten? | **Classic** |
| Consumer, Lifestyle, Gesundheit, Beauty, Privat-Finanzen (B2C)? | **Conversational** |
| B2B-Finanzen, Enterprise, professionelle Dienstleistungen? | **Classic** |
| Gemischte Zielgruppe, Standard-Leadgen? | **Standard** |
| Mobile-heavy Traffic (>60%) + emotionales Thema? | **Conversational** |
| Kalt-Traffic + wenig Zeit + einfaches Ziel? | **Standard** |
| Komplexe Diagnose, viele Folgefragen, hoher Erklärungsbedarf? | **Conversational** |

### Modus-Übersicht

**Classic**
Labels, Felder, Gruppen, Fortschrittsbalken. Funktional und klar. Wirkt nüchtern aber vertrauenswürdig. Ideal für Kontexte wo User schnell und effizient Daten eingeben wollen.
- Felder pro Step: bis zu 5 (Desktop), 2–3 (Mobile)
- Transition: keine oder subtiles Fade
- Ton: sachlich, direkt

**Standard**
Ein Step pro Screen, ein klarer Fokus, klare Navigation (Weiter/Zurück). Bekanntes Format, universell einsetzbar. Gut wenn Thema neutral und Zielgruppe gemischt ist.
- Felder pro Step: 2–3 (Desktop), 1–2 (Mobile, empfohlen 1, max. 2)
- Transition: Slide left/right
- Ton: freundlich, klar

**Conversational**
Chat-Style. Eine Frage, Antwort, nächste Frage. Wirkt wie ein Dialog, nicht wie ein Formular. Senkt die psychologische Hemmschwelle besonders bei sensiblen Themen. Kann vorherige Antworten in die nächste Frage einbauen ("Du hast Beine gewählt – hast du empfindliche Haut?").
- Felder pro Step: immer 1
- Transition: Fade in von unten
- Ton: persönlich, warm, auf Augenhöhe

> **Wichtig:** Der Modus ist kein kosmetisches Detail. Conversational kann bei emotionalen Themen (Haartransplantation, medizinische Qualifizierung, Finanzberatung B2C) Conversion deutlich steigern. Für strukturierte B2B-Daten und Power User erzeugt Conversational mehr Mental Load als Classic – KAIST-Studie 2023 bestätigt.

---

## 4. Struktur & Step-Anzahl

### Optimale Step-Anzahl

| Gesamte Felder | Empfehlung |
|---|---|
| 1–5 | Single-Step oder max. 2 Steps |
| 6–10 | 3–4 Steps |
| 11–20 | 4–5 Steps |
| 20+ | 5–6 Steps oder Conversational |

**Warum nicht mehr als 6 Steps (Standard/Classic)?**
Unter 3 Steps baut sich zu wenig psychologisches Commitment auf. Über 6 Steps beginnen User das Gefühl zu haben, gefangen zu sein. 3–5 ist der Sweet Spot für die meisten Lead-Formulare.

**Ausnahme Conversational:** Im Conversational Mode sind 8–12 Steps möglich, weil jeder Step minimal ist (1 Frage) und das Chat-Format keine Step-Zählung impliziert. Die "6 Steps"-Regel gilt nur für Standard- und Classic-Modus.

### Optional: Welcome Screen (Step 0)

Ein dedizierter Einleitungs-Screen vor Step 1 kann Completion Rate erhöhen weil er Erwartungen setzt und Anxiety reduziert.

Inhalt: "Was dich erwartet: 3 Fragen, ca. 2 Minuten. Du erhältst danach ein individuelles Angebot."

**Wann sinnvoll:** Kalter Traffic, komplexere Wizards (5+ Steps), medizinische oder sensible Themen.

**Wann weglassen:** Warmer Traffic der bereits informiert ist, einfache Wizards mit 2–3 Steps.

### Bewährte Step-Logik

```
Step 0  →  WELCOME SCREEN (optional)
           Erwartungen setzen, Anxiety reduzieren
           "3 Fragen, 2 Minuten, dein persönliches Angebot"

Step 1  →  EINSTIEG: Einfachste, unverfänglichste Frage
           Ziel: Commitment aufbauen, keine Friction
           Standardmäßig: keine sensitiven Felder (Email, Telefon)
           Ausnahme: Wenn Partial Lead Capture priorisiert wird
           (→ Sektion 5), kann Email in Step 1 als einziges
           Feld mit klarem Benefit-Text stehen
           Ideal: Multiple Choice, visuelle Auswahl

Step 2  →  QUALIFIZIERUNG: Das Problem / der Bedarf
           Branching beginnt hier wenn nötig
           Folgefragen basierend auf Step 1

Step 3  →  VERTIEFUNG: Spezifischere Informationen
           User ist bereits invested (Sunk Cost)
           Komplexere Fragen möglich

Step 4  →  SENSITIVE DATEN: Email, dann Telefon
           Erst hier – Sunk Cost Peak
           Name ist weniger sensitiv, kann früher stehen
           Telefon immer optional oder letzter Step
           Jedes sensitive Feld mit Erklärung warum nötig

Step 5  →  CTA: Abschluss, Termin, Paywall, Download
           Klare Bestätigung + Next Step
```

### Fragen-Reihenfolge nach NN/g

Diese Priorität gilt **innerhalb eines Steps** (Reihenfolge von Feldern), nicht zwischen Steps:

1. **Vertrautheit:** Bekannte Infos zuerst
2. **Komplexität:** Einfaches vor Komplexem
3. **Sensitivität:** Unkritisches vor Persönlichem
4. **Aufwand:** Was braucht der User zuerst um weiterzumachen?

### Browser-Back-Button

Der Browser-Zurück-Button ist in Multi-Step Wizards eine häufige Fehlerquelle. Drei Verhaltensweisen – eine muss bewusst gewählt werden:

1. **Back = Step zurück** *(empfohlen):* Über History API (`pushState`) jeden Step als eigenen History-Eintrag registrieren. Back navigiert einen Step zurück ohne Datenverlust.
2. **Back = LP zurück:** Wizard hat keinen eigenen History-Eintrag. Back verlässt den Wizard.
3. **Kein Browser-Back:** Fullscreen-Overlay blockiert Browser-Navigation. Nur interner Zurück-Button funktioniert.

**Empfehlung:** Option 1. User erwarten dass Back = zurückgehen bedeutet.

*Tracking-Hinweis: Jeden Step als `pushState`-Eintrag anlegen. So sind Step-Views auch in Server-Logs nachvollziehbar.*

---

## 5. Fragen-Sequenz & Feldstrategie

### Die Quantity vs. Quality Entscheidung

**Das ist die wichtigste Business-Entscheidung vor der Feldplanung:**

| Ziel | Strategie | Konsequenz |
|---|---|---|
| Maximale Lead-Anzahl (Top of Funnel) | Weniger Felder (3–4), Email früh | Mehr Leads, niedrigere Qualität |
| Maximale Lead-Qualität (Bottom of Funnel) | Mehr Felder (5–8), Qualifier tief | Weniger Leads, höhere Qualität |
| Beides balancieren | Progressive Profiling | Email früh, Rest später oder bei Wiederkehr |

> **Merksatz (HubSpot):** "Kürzere Forms = mehr Leads, längere Forms = bessere Leads. Beide können richtig sein – je nach Funnel-Position."

### Die Email-Platzierung

```
Ist Partial Lead Capture wichtig?
(= Auch ein Abbruch nach Step 2 ist ein wertvoller Lead)
│
├── Ja → Email in Step 1 oder 2 abfragen
│         Nur als einziges Feld dieses Steps
│         Mit klarem Benefit-Text darüber
│         → Wer abbricht hat trotzdem Email hinterlassen
│         → Follow-up möglich (wenn Datenschutz erlaubt)
│
└── Nein → Email im vorletzten oder letzten Step
           → Maximale Completion Rate durch Sunk Cost
           → Telefon immer NACH der Email
```

### Feldanzahl-Regeln

- **Jedes Feld muss sich rechtfertigen.** Nicht "nice to have", sondern "notwendig für Qualifizierung oder Zustellung".
- **Expedia-Warnung:** Ein einziges unnötiges Feld (Firmenname) kostete $12 Mio/Jahr.
- **Aagaard-Warnung:** Felder blind reduzieren kann Conversion senken. Felder die der User für die Leistung als logisch notwendig empfindet, dürfen bleiben. Nur *irrelevante* Felder entfernen.
- **Regel:** Felder die der User für die Leistung als logisch notwendig empfindet dürfen bleiben. Felder die nur dem Projekt nützen, kommen ans Ende oder weg.

### Funnel-Position und Feldtiefe

| Funnel-Position | Angebot | Empfohlene Felder |
|---|---|---|
| Top of Funnel | Newsletter, Guide, Whitepaper | 2–4 |
| Mid Funnel | Demo-Anfrage, Beratung | 4–6 |
| Bottom of Funnel | Kauf, konkretes Angebot | 5–8 |

### Sensitive Felder

Diese Felder erzeugen die meiste Friction und müssen strategisch platziert werden:

| Feld | Conversion-Effekt | Empfehlung |
|---|---|---|
| Telefonnummer | −5% bis −18.7% | Letzter Step, immer optional oder mit Erklärung |
| Geburtsdatum | Hohe Friction | Nur wenn wirklich nötig, mit Erklärung |
| Budget/Gehalt | −15.3% | Nur Bottom-of-Funnel, nach Commitment |
| Firmenname (ohne Kontext) | Expedia: −$12M/Jahr | Nur wenn direkt relevant |

**Immer bei sensitiven Feldern:** Direkt darunter in 1–2 Sätzen erklären warum diese Information benötigt wird.

### Progressive Profiling

Bei wiederkehrenden Usern (z.B. zweiter LP-Besuch): bereits bekannte Felder ausblenden, neue Qualifier-Fragen zeigen um das Lead-Profil zu vertiefen. Setzt voraus dass der User identifizierbar ist (Cookie, Login, Email-Match).

*Tracking-Hinweis: Separate Felder tracken ob sie "prefilled" oder "user-entered" waren. Nur so ist erkennbar ob Progressive Profiling korrekt funktioniert.*

---

## 6. Input-Typen

### Entscheidungs-Hierarchie

Immer den Typ mit der geringsten Friction wählen:

```
1. Visuelle Kacheln / Image Choice Cards
   → Ein Tap, Auto-Advance bei Single Choice (Maus/Touch)
   → Beste UX, höchste Completion
   → Wenn Optionen visuell unterscheidbar sind
   → Nicht geeignet für 6+ Optionen

2. Radio Buttons / Checkboxes
   → Klar sichtbar, kein Extra-Klick
   → Radio: mutually exclusive
   → Checkbox: multiple Auswahl möglich
   → Vertikal stapeln, nicht horizontal

3. Segmented Control / Button Group
   → Gut für 2–4 Optionen
   → Platzsparender als Radio Buttons

4. Dropdown
   → Erst ab 6+ Optionen sinnvoll
   → Immer mit Search-Funktion wenn mehr als 10 Optionen
   → Häufigste Optionen oben
   → Immer "Sonstiges" als letzte Option

5. Slider / Stepper
   → Slider für Ranges (Budget: 100–10.000€)
   → Stepper für kleine Mengen (Anzahl Personen)

6. Freitext (Einzeiler)
   → Nur wenn keine Auswahl möglich ist
   → Email, Telefon, Name

7. Freitext (Mehrzeiler)
   → So selten wie möglich
   → Erhöht Cognitive Load stark
   → Wenn, dann optional und ganz am Ende
   → Im Conversational Mode: Folgefrage statt Freitext
```

### Auto-Advance

Wenn ein User eine Single-Choice-Auswahl trifft (Kachel, Radio Button per **Maus oder Touch**), kann der Wizard automatisch zum nächsten Step weiterrücken.

**Ausnahme Keyboard-Navigation:** Auto-Advance muss bei Keyboard-Input deaktiviert sein. User die mit Tab/Enter navigieren müssen die Auswahl bestätigen können ohne ungewollt weiterzuspringen. Der Weiter-Button bleibt aktiv und muss angesteuert werden können.

**Gilt nicht für:** Multi-Choice, Freitext, Sensitive Felder.

*Tracking-Hinweis: Auto-Advance-Klicks tracken (welche Option wurde gewählt). Bei Dropdowns: Zeit bis zur Auswahl loggen – lange Zeiten zeigen unklare Optionen.*

### Mobile-spezifische Input-Typen

```html
<input type="email">    → Keyboard mit @-Symbol
<input type="tel">      → Numpad
<input type="number">   → Zahlen-Keyboard
<input type="date">     → Nativer Date Picker
                          (nur für Terminwahl/nahe Daten,
                          NICHT für Geburtsdatum – siehe unten)
<input type="search">   → Keyboard mit Suchen-Button
```

**Geburtsdatum-Ausnahme:** `type="date"` erfordert rückwärts durch Jahrzehnte zu klicken – auf Mobile besonders mühsam. Besser: drei separate Dropdowns (Tag / Monat / Jahr) oder Freitext mit Formathinweis (TT.MM.JJJJ).

---

## 7. UI/UX Design-Regeln

### Typografie

| Element | Größe | Gewicht | Notizen |
|---|---|---|---|
| Step-Frage / Heading | 22–28px | Bold | Dominiert den Screen |
| Sub-Label / Erklärtext | 14–16px | Regular | Direkt unter der Frage |
| Input-Label | 16px | Medium | Über dem Feld, nie als Placeholder-Ersatz, min. 16px auch Mobile |
| Placeholder-Text | 14px | Regular, gedimmt | Nur Formatbeispiel ("z.B. name@mail.de") |
| Helper-Text | 12–13px | Regular | Direkt unter sensitive Felder |
| Button-Text | 16–18px | Bold | Immer benefit-orientiert |

**3-Größen-Regel (NN/g):** Drei Font-Größen reichen für einen Wizard. Mehr erzeugt visuelle Verwirrung.

**Line Height:** 1.5× Schriftgröße (16px Text → 24px Line Height).

**Wichtig:** Placeholder-Text verschwindet beim Tippen. Labels müssen permanent sichtbar bleiben – nie Placeholder als Label-Ersatz verwenden.

### Layout

- **Single Column immer** – Ausnahme: Classic Mode mit 13+ Feldern auf einmal (HubSpot: Double-Column +57% bei 13 Feldern weil Single-Column zu einschüchternd wirkte). Auf Mobile immer Single Column.
- **Maximale Inhaltsbreite:** 580–640px für den Wizard-Container
- **Keine Horizontal-Navigation** wenn Wizard aktiv ist

### Progress Bar

| Regel | Begründung |
|---|---|
| Startet bei ~15%, nicht bei 0% | Endowed Progress Effect |
| Zeigt Nähe zum Ziel, nicht nur Fortschritt | Goal Gradient Effect |
| Am letzten Step: "Fast geschafft!" | Motivations-Peak nutzen |
| Immer im Viewport sichtbar | Auch wenn Mobile Keyboard offen ist |
| Zwei Varianten testbar | Prozentbalken (fließend) oder Step-Dots (1 von 4) |

### Buttons & CTAs

| Schlecht | Gut |
|---|---|
| Weiter | Zum nächsten Schritt |
| Absenden | Kostenloses Angebot erhalten |
| Submit | Termin anfragen |
| OK | Analyse starten |

**Button-Sizing:**
- Desktop: Volle Breite des Form-Containers oder mindestens 200px
- Mobile: Immer volle Breite
- Mindesthöhe: 48px

### Farben

| Element | Empfehlung | Grund |
|---|---|---|
| Primary CTA | Markenfarbe oder Blau | Blau > Rot (+15–20% in Studien) – wenn kein Brand-Color vorhanden |
| Success State | Grün | Universelle Assoziation |
| Error State | Rot + Icon + Text | Nie nur Farbe allein (Colorblindness) |
| Progress Bar | Markenfarbe oder Blau | |
| Aktives Feld | Blau oder Markenfarbe border | Fokus-Indikator |

**Farbkontrast:** Mindestens 4.5:1 für normalen Text, 3:1 für große Schrift (WCAG AA).

### Animationen & Transitions

Animationen haben eine klare Aufgabe: **räumliche Orientierung und Systemfeedback** – nicht Dekoration.

| Kontext | Animation | Timing |
|---|---|---|
| Step vorwärts | Slide left | 300ms |
| Step zurück | Slide right | 300ms |
| Conversational: neue Frage | Fade in von unten | 250ms |
| Button-Klick | Scale down + Color Change | 100ms |
| Inline Validation OK | Grüner Haken Fade In | 150ms |
| Inline Validation Error | Shake + Rot | 200ms |
| Action-Step Loading | Skeleton Screen oder Spinner | sofort |
| Letzter Step Abschluss | Check-Animation | 400ms |

**Timing-Regel für Transitions und Micro-Interactions:**
- Micro-Interactions (Klick, Hover, Validation): 100–200ms
- Step-Transitions: 300–400ms
- Alles über 500ms bei Transitions → User denkt es ist kaputt

**Diese 500ms-Regel gilt nicht für Loading States** – dort gelten eigene Regeln (→ Loading States).

Immer `prefers-reduced-motion` CSS-Query berücksichtigen.

### Loading States (Action Steps)

```
< 1 Sekunde    → Kein Indicator nötig
1–3 Sekunden   → Spinner mit kurzem Text ("Analysieren...")
3–10 Sekunden  → Progress Bar + erklärender Text
                 ("Wir prüfen deine Bewertung... ca. 5 Sekunden")
> 10 Sekunden  → Skeleton Screen + klare Kommunikation was passiert
```

*Tracking-Hinweis: Loading-Dauer von Action-Steps loggen. Lädt ein Step >10s regelmäßig → API-Performance-Problem das Conversion kostet.*

### Form Container

| Container | Wann | Vorteil | Nachteil |
|---|---|---|---|
| **Embedded (Inline)** | LP mit Content davor, natürlicher Flow | Kein Extra-Klick | Umgeben von LP-Ablenkungen |
| **Two-Step (Button → Fullscreen-Overlay)** | Wenn LP-Eindruck wichtig ist | +1375% in Aweber-Studie, hohes Initial-Commitment | Extra Klick nötig |
| **Full-Page Wizard** | Wizard ist einziger Zweck der Seite | Maximale Fokussierung | User verlässt LP |
| **Sticky Widget** | Niedrigschwelliger Einstieg | Jederzeit verfügbar | Kann stören |

> **Begriffserklärung:**
> **Fullscreen-Overlay** = öffnet über die gesamte Seite, LP verschwindet im Hintergrund → empfohlen für Two-Step.
> **Klassisches Modal** (zentriertes Popup, scrollbare LP dahinter) → **nicht** für mehrstufige Wizards geeignet. Keyboard-Probleme, schlechte Mobile-UX, User verliert Kontext.

---

## 8. Mobile-Regeln

### Die Wahrheit über Mobile

"Single-Step ist besser auf Mobile" gilt **nur für unter 5 Felder**. Ab 6 Feldern eliminiert Multi-Step das Scrollen komplett – das ist auf Mobile besser. Multi-Step speichert Daten nach jedem Step → schützt vor Verbindungsabbruch, besonders relevant auf Mobile.

### Mobile-spezifische Regeln

| Regel | Begründung |
|---|---|
| 1–2 Felder pro Step (empfohlen 1, max. 2) | Weniger Viewport, mehr Cognitive Load |
| Buttons immer full-width | Daumen-Navigation |
| Touch Targets min. 48×48px | Google/Material Design |
| Kein Horizontal Scrolling | Absolutes No-Go |
| Progress Bar immer im Viewport | Auch wenn Keyboard offen ist |
| `autocomplete` Attribute setzen | Autofill beschleunigt Completion um ~30% |
| Kein Dropdown wenn vermeidbar | Zu viele Taps |
| Schrift min. 16px | Verhindert Auto-Zoom auf iOS |

### Conversational auf Mobile

Chat-Style Forms fühlen sich auf Mobile natürlicher an. Bei Mobile-heavy Traffic (>60%) und emotionalen Themen immer Conversational testen.

### Performance

1 Sekunde zusätzliche Ladezeit = −7% Conversion (allgemeiner Web-Wert, auf Mobile mit schlechten Verbindungen noch kritischer):
- Wizard-Assets lazy laden
- Step-Content erst laden wenn benötigt
- Keine schweren Bilder im Wizard (außer Image Choice Cards, diese optimieren)

---

## 9. Psychologie-Prinzipien & ihre Anwendung

### Sunk Cost Fallacy

**Prinzip:** Sobald jemand Zeit investiert hat, möchte er diesen Aufwand nicht "verlieren". Je mehr Steps ausgefüllt, desto schwerer fällt der Abbruch. *Zeitbasierter Mechanismus.*

**Anwendung:** Sensitive Felder ans Ende – der Sunk-Cost-Peak ist am letzten Step am höchsten. Progress Bar macht den investierten Aufwand sichtbar.

---

### Commitment & Consistency (Cialdini)

**Prinzip:** Menschen verhalten sich konsistent zu ihren früheren Entscheidungen. Wer Step 1 ausfüllt, widerspricht sich selbst beim Abbruch. *Identitätsbasierter Mechanismus.*

> **Abgrenzung zu Sunk Cost:** Sunk Cost = "Ich habe Zeit investiert, die verliere ich beim Abbruch." Commitment = "Ich habe mich als jemand definiert der dieses Formular ausfüllt." Beide wirken gleichzeitig, verstärken sich gegenseitig. Sunk Cost Peak = letzter Step. Commitment baut sich ab Step 1 auf.

**Anwendung:** Jeden Step als vollständige Micro-Conversion behandeln. Auto-Save nach jedem Step. Partial Leads reaktivieren.

---

### Foot in the Door (FITD)

**Prinzip:** Wer einem kleinen Request zugestimmt hat, stimmt einem größeren mit höherer Wahrscheinlichkeit zu. Freedman & Fraser 1966: 76% Compliance nach kleinem Commitment vs. <20% ohne.

**Anwendung:** Erste Frage immer die einfachste, unverfänglichste. Visuelle Kacheln mit einem Tap sind der beste Einstieg. Nie mit Email oder persönlichen Daten beginnen (Ausnahme: Partial Lead Capture, → Sektion 5).

---

### Endowed Progress Effect

**Prinzip:** Menschen werden motivierter wenn sie das Gefühl haben, bereits Fortschritt gemacht zu haben – selbst wenn dieser Fortschritt künstlich ist.

**Anwendung:** Progress Bar startet bei ~15%, nicht bei 0%. Step-Bezeichnung "Schritt 1 von 4" statt leere Bar.

---

### Goal Gradient Effect

**Prinzip:** Die Motivation steigt mit der Nähe zum Ziel. "Nur noch 1 Step" motiviert stärker als "du hast 3 Steps gemacht".

**Anwendung:** Progress Bar kommuniziert Nähe zum Ende. Copy am letzten Step: "Fast geschafft – nur noch deine Kontaktdaten."

---

### Quid Pro Quo

**Prinzip:** User teilen Daten lieber wenn sie einen klaren Gegenwert sehen. Je mehr Felder, desto klarer muss der Gegenwert kommuniziert werden.

**Anwendung:** CTA immer benefit-orientiert. Value Proposition am Anfang: "In 2 Minuten zu deinem persönlichen Angebot."

---

### BJ Fogg's Behavior Model

**Prinzip:** Eine Conversion passiert wenn **Motivation × Ability × Trigger** gleichzeitig hoch genug sind.
- **Motivation** = Relevanz des Angebots, emotionale Ansprache auf der LP
- **Ability** = Einfachheit des Wizards (FITD, Single Column, kurze Steps)
- **Trigger** = CTA-Button, Exit-Intent, Scroll-Trigger, Timer

Selbst ein perfekter Wizard scheitert ohne Trigger. Selbst ein schlechter Wizard kann bei hoher Motivation konvertieren (erklärt warum manche langen Forms trotzdem funktionieren).

---

### Zeigarnik Effect

**Prinzip:** Unvollendete Aufgaben bleiben stärker im Gedächtnis als vollendete. Erzeugt psychologische Spannung die zur Completion drängt.

**Anwendung:** Wizard sichtbar starten lassen – entweder embedded above fold oder Step 1 bereits im Viewport wenn User auf den CTA-Button klickt. Beim Abbruch: "Du hast deinen Fortschritt noch nicht gespeichert."

---

## 10. Validation & Fehler

### Timing der Validation

| Zeitpunkt | Einsatz | Beispiel |
|---|---|---|
| **On Blur** (nach Verlassen des Feldes) | Standard für die meisten Felder | Name, Telefon, Email |
| **On Key Press** (während des Tippens) | Nur für Längen-Checks | Passwort-Stärke (nicht für Email – zu aggressiv beim Tippen) |
| **On Submit** | Als Fallback, nie als Ersatz | Pflichtfeld-Check |

**Nicht validieren während der User tippt** außer für Längen-Feedback. Sofortige Fehlermeldungen beim Tippen wirken aggressiv.

Studie (Luke Wroblewski): Inline Validation = **+22% Success Rate, −22% Fehler, −42% Completion Time.**

*Tracking-Hinweis: Jeden Validation-Fehler als Event loggen mit Feld-ID und Fehlertyp. Felder mit >15% Error Rate müssen überarbeitet werden.*

### Error Message Qualität

```
❌ Schlecht:
"Ungültige Eingabe"
"Fehler"
"Pflichtfeld"

✅ Gut:
"Sieht aus als fehlt eine Ziffer – Telefonnummern haben 10 Stellen"
"Bitte gib eine gültige E-Mail-Adresse ein (z.B. name@mail.de)"
"Damit wir dich erreichen können, brauchen wir deine Email"
```

### Error State Design

- Nie **nur mit Farbe** kommunizieren
- Immer: Farbe (Rot) + Icon (⚠) + Text
- Fehlermeldung **direkt am Feld**, nicht oben auf der Seite
- Auf Mobile: Feld und Fehlermeldung müssen im Viewport sichtbar sein

### Validation-Toleranz

Telefonnummern in verschiedenen Formaten akzeptieren und im Backend normalisieren. Gilt auch für internationale Nummern – kein hartes Format erzwingen. Formathinweis im Placeholder reicht.

### Submit-Fehler (Server Error)

Wenn die Übermittlung fehlschlägt:
- State lokal im Browser speichern (localStorage) damit Daten nicht verloren gehen
- Klare Fehlermeldung: "Etwas ist schiefgelaufen – deine Eingaben wurden gespeichert. Bitte versuch es nochmal."
- Retry-Button direkt sichtbar
- Bei wiederholtem Fehler: alternatives Kontaktangebot (Email, WhatsApp)

*Tracking-Hinweis: Submit-Fehler mit Zeitstempel und Step-Zustand loggen. Gehäufte Server-Errors sind ein technisches Problem das direkte Conversion-Verluste verursacht.*

### CAPTCHA

Vermeiden. CAPTCHAs haben nachweislich stark negative Auswirkungen auf Completion Rates und blockieren Assistive Technology. Alternativen: Honeypot-Felder, serverseitiges Rate-Limiting, reCAPTCHA v3 (unsichtbar).

---

## 11. Trust & Datenschutz

### Trust-Signale: Platzierung

Trust Signals im Wizard sind **dezente, inline platzierte Elemente direkt an Friction-Punkten** – keine visuellen Blöcke die um Aufmerksamkeit konkurrieren. Testimonial-Blöcke, Logos-Sektionen und längere Trust-Inhalte gehören auf die LP, nicht in den Wizard.

| Friction-Punkt | Trust-Signal |
|---|---|
| Erster Step (kalter Traffic) | "Bereits X Projekten geholfen" – einzeilig, dezent |
| Email-Feld | "Kein Spam. Nur relevante Updates." |
| Telefon-Feld | "Wir rufen nur für die Terminbestätigung an." |
| Letzter Step vor Submit | Datenschutz-Link + kurze Erklärung |
| Medizinische/Finanz-Themen | Zertifizierungen dezent eingebunden |

### Erklärungen bei Sensitive Feldern (direkt unter dem Feld)

```
Telefon:
"Wir rufen dich nur an um deinen Termin zu bestätigen."

Geburtsdatum:
"Wird benötigt für die medizinische Erstbeurteilung."
```

### Datenschutz & Consent

**Ob und welche Datenschutzregeln gelten, ist projektspezifisch und muss in Klärungsfrage 1.11 geklärt werden.** Nicht jedes Projekt unterliegt der DSGVO.

Wenn eine Datenschutzverordnung gilt:
- Consent-Checkbox **direkt vor dem Submit-Button** – nicht getrennt, nicht irgendwo unten
- **Voreingestellt: nicht aktiviert**
- Klare Sprache, kein Juristendeutsch
- Datenschutz-Link öffnet in neuem Tab (User verlässt Wizard nicht)

Wenn keine Pflicht besteht: Standard-Datenschutzhinweis ohne Opt-in reicht.

---

## 12. LP-Integration: Form im Kontext der Landingpage

### Grundprinzip

```
LP-Zone:     Überzeugen
             → Navigation, Hero, Benefits, Social Proof,
               Testimonials, FAQ, Vertrauen aufbauen
             → Endet mit einem prominenten CTA-Button

Übergang:    Der Klick = erstes Commitment (FITD aktiviert)

Wizard-Zone: Abfragen
             → Navigation weg, alles andere ausgeblendet
             → Ein Step, ein Fokus
             → Kein Ablenken mehr

Post-Wizard: Bestätigen
             → Thank You Page mit Next Step
```

### Konflikte LP vs. Wizard

| Konflikt | LP | Wizard | Lösung |
|---|---|---|---|
| Navigation | Nav-Bar für Vertrauen | Nav killt Conversion (+100% ohne Nav) | Wenn Wizard startet → Nav ausblenden oder Fullscreen-Overlay |
| Visual Density | Hero, Features, Testimonials parallel | Ein Element dominiert pro Step | LP-Content endet visuell wenn Wizard beginnt |
| Scrollen | Gewünscht, Content baut auf | Kein Scrollen per Step | Wizard nie mid-scroll embedded. Entweder above fold, nach LP-Abschluss, oder als Overlay |
| Multiple CTAs | Mehrere CTAs verteilt | Genau ein CTA pro Step | Sobald Wizard aktiv: alle anderen CTAs ausblenden |
| Layout | Two-Column oft für Balance | Single Column | Wizard hat eigenes Layout-System |

### Container-Empfehlung

**Empfehlung für die meisten LPs: Two-Step (Button → Fullscreen-Overlay)**

1. LP-User sieht CTA-Button ("Jetzt Angebot erhalten")
2. Klick = erstes Commitment (FITD aktiviert)
3. Fullscreen-Overlay öffnet sich, LP verschwindet im Hintergrund
4. User ist voll fokussiert auf den Wizard

Aweber-Studie: Two-Step konvertierte **+1375%** gegenüber direktem Embedded-Form. (Kontextabhängiger Richtwert – eigene Tests sind Pflicht.)

### Message Match

Der Text auf dem LP-CTA-Button muss direkt mit dem ersten Step des Wizards korrespondieren:

```
✅ Konsistent:
LP Button:     "Jetzt Haaranalyse starten"
Wizard Step 1: "Wie würdest du deinen Haarausfall beschreiben?"

❌ Bruch:
LP Button:     "Kostenlos anfragen"
Wizard Step 1: "Was ist dein Geschlecht?"
```

*Tracking-Hinweis: CTA-Position auf der LP tracken (Hero vs. Mitte vs. Footer). Welcher CTA konvertiert und welcher erzeugt nur Hover ohne Klick (`cta_hover` ohne `cta_click`) zeigt Unsicherheit – Copy-Problem.*

---

## 13. Tracking & Analytics

### 13.1 Grundprinzip

> **Wizard-Tracking ist Optimierungs-Infrastruktur – kein Add-on.**

Das Tracking hat zwei gleichwertige Aufgaben:

**Conversion Tracking** – was liefert der Wizard?
Jede abgeschlossene Submission = Macro-Conversion.
Jeder abgeschlossene Step = Micro-Conversion.
Beide müssen messbar und voneinander trennbar sein.

**Verhaltens-Tracking** – wo liegt das Optimierungspotenzial?
Das Tracking muss so aufgesetzt sein dass folgende Fragen jederzeit beantwortbar sind:
- Wo brechen User ab? (Step-Level Drop-off)
- Welches war das letzte aktive Feld vor dem Abbruch? (Last Active Field)
- Welche Felder erzeugen Fehler oder Zögern? (Field-Level Friction)
- Gibt es Unterschiede zwischen Traffic-Quellen?
- Gibt es Unterschiede zwischen Geräten?
- Wie lange brauchen User pro Step?
- Wo kommen User zurück nach Abbruch?

**Regel:** Ein Wizard ohne vollständiges Step-Level Tracking ist nicht optimierbar.

---

### 13.2 Tracking-Philosophie: Server-First by Default

Das Standard-Setup ist eigenes Server-Side Tracking – keine Third-Party Tools werden standardmäßig eingebunden:

- Behaviour, Funnel, Fehler, Conversions → **eigene DB via sendBeacon**
- Keine GA4, kein GTM, kein Meta Pixel by default
- Volle Datenkontrolle, keine externe Datenschutz-Exposition, keine Ad-Blocker-Anfälligkeit

**Wenn das Projekt es explizit verlangt** (GA4, GTM, Google Ads Conversion, Meta Pixel, etc.):
- Tool wird eingebunden
- Die relevanten Events werden **zusätzlich** dorthin gesendet
- Das eigene Server-Side Tracking läuft **parallel weiter** – es wird nie ersetzt, nur ergänzt
- Was an Third-Party Tools geht: nur was für den jeweiligen Zweck nötig ist

---

### 13.3 Zwei-Phasen-Architektur

Tracking ist in zwei Phasen aufgeteilt die über eine gemeinsame `visit_id` verknüpft sind:

```
Phase 1: Landing Page          Phase 2: Wizard
─────────────────────          ───────────────
visit_events Tabelle           session_events Tabelle
       │                              │
       └──────── visit_id ────────────┘
```

Sobald der User den Wizard startet, stoppt Phase 1 und Phase 2 übernimmt. Die Verknüpfung über `visit_id` ermöglicht Kohorten-Analyse: Wer hat die LP gesehen aber den Wizard nie gestartet? Wer hat welchen Step abgebrochen?

**Attribution-Verknüpfung:** `gclid`, `utm_*`, `device_type`, `referrer` werden von der LP-Phase auf die Wizard-Session vererbt. Damit ist jeder Lead bis zum Traffic-Ursprung zurückverfolgbar.

---

### 13.4 Phase 1: LP-Tracking Events

| Event | Daten | Warum |
|---|---|---|
| `section_visible` | section_name | Welche Sektionen sieht der User überhaupt? |
| `section_duration` | section, duration_ms | Wo bleibt er hängen, wo scrollt er durch? |
| `scroll_depth` | 25/50/75/100% | Kommt er überhaupt zum CTA? |
| `cta_click` | cta_id, location | Welcher CTA konvertiert? (Hero vs. unten) |
| `cta_hover` | hover_ms | Interesse ohne Klick = Unsicherheit/Copy-Problem |
| `wizard_interaction` | field, value | User interagiert mit Wizard VOR Session-Erstellung |
| `wizard_no_interaction` | visible_duration_ms | Wizard sichtbar >10s ohne Aktion = Einstiegs-Problem |
| `performance` | fcp_ms, dom_ready_ms, cta_above_fold | Ladezeit-Impact auf Conversion |
| `page_leave` | total_time, active_time, max_scroll, sections_seen | Exit-Summary: Was hat der User gesehen bevor er ging? |

---

### 13.5 Phase 2: Wizard-Tracking Events

| Event | Daten | Warum |
|---|---|---|
| `step_enter` | step | Funnel: Wo steigen User ein? |
| `step_complete` | step | Funnel: Welche Steps werden abgeschlossen? |
| `step_back` | from_step, to_step | Unsicherheit: Wer geht zurück und wohin? |
| `step_time` | step, duration_ms, fields_touched | Friction-Indikator pro Step |
| `field_focus` | step, field | Welche Felder werden angefasst? |
| `field_change` | step, field, has_value | Welche Felder werden ausgefüllt? |
| `field_error` | step, field, error_type | Welche Felder erzeugen Fehler? (>15% = überarbeiten) |
| `field_correction` | step, field | Wie oft wird eine Antwort geändert? (Mehrdeutigkeit) |
| `field_hesitation` | field, step, hesitation_ms | Fokus >5s ohne Eingabe = Verwirrung/Unsicherheit |
| `answer_selected` | step, field, value | Welche Optionen werden wie oft gewählt? (Answer Distribution) |
| `page_leave` | current_step, time_in_step, fields_touched_in_step, last_active_field | Wo genau wird abgebrochen? Last Active Field = letztes berührtes Feld |
| `submit_attempt` | step | Submit wurde ausgelöst |
| `submit_success` | — | Macro-Conversion |
| `submit_error` | error_type, step_state | Server-Fehler beim Absenden |

**Last Active Field:** Das Feld in `fields_touched_in_step` das zuletzt interagiert wurde. Zeigt präzise wo die Abbruch-Ursache liegt – nicht nur welcher Step, sondern welches Feld im letzten Step.

---

### 13.6 Conversion-Architektur: Abgestufte Werte

Nicht alle Conversions sind gleich viel wert. Abgestufte Conversion-Werte erlauben Ad-Plattformen auf den richtigen Lead-Typ zu optimieren – nicht nur auf Volumen.

**Generisches Schema (projektspezifisch anpassen):**

| Conversion | Relativer Wert | Trigger | Warum |
|---|---|---|---|
| Partial Lead (nur Email) | Niedrig | Abbruch nach Email-Step | Minimaler Lead-Wert, Retargeting möglich |
| Partial Lead (Email + Telefon) | Mittel | Abbruch nach Telefon-Step | Telefonisch erreichbar |
| Vollständiger Lead | Hoch | Alle Pflichtfelder ausgefüllt + Submit | Qualifizierter Lead |
| Höchster Intent | Sehr hoch | Termin gebucht / Kauf / Qualifikation bestätigt | Höchste Conversion-Wahrscheinlichkeit |

---

### 13.7 Technische Tracking-Regeln

| Entscheidung | Regel | Begründung |
|---|---|---|
| **sendBeacon** für Events | Immer für Abandon- und Submit-Events | Garantiert Zustellung auch bei Tab-Close/Navigation |
| **Batching** | LP: ~10s, Wizard: ~5s | Weniger Requests, weniger Server-Last |
| **Immediate Flush** | Für kritische Events (Abandon, Submit, Error) | Dürfen nie verloren gehen |
| **Doppel-Send Schutz** | Flag-Variable vor `page_leave` Events | React Cleanup + sendBeacon feuern sonst beide |
| **Delta statt Timestamp** | `duration_ms` muss Differenz sein | Unix-Timestamp als Duration ist ein häufiger Bug |
| **visit_id Vererbung** | gclid, utm_*, device_type von LP auf Session | End-to-End Attribution ohne GA4 |
| **State in URL** | Nur Step-Nummer, keine Antworten | Antworten in URL landen in Server-Logs |

---

### 13.8 A/B-Testing Regeln

**Visits pro Variante abhängig von der Conversion Rate:**

| Conversion Rate | Benötigte Visits pro Variante |
|---|---|
| ~20%+ | ~1.000 |
| 5–15% (typisch) | 5.000–10.000 |
| Unter 5% | 10.000+ |

**Faustregel:** Min. 100 tatsächliche Conversions pro Variante bevor eine Entscheidung getroffen wird.

- Min. **1 Woche** laufen lassen (Wochentag-Varianz ausgleichen)
- **Immer nur eine Variable** gleichzeitig testen
- A/B-Test-Variante als Dimension in **alle** Wizard-Events schreiben – nur so ist der Test auf Step-Ebene auswertbar, nicht nur auf Gesamt-Conversion

**Test-Reihenfolge (Priorität):**
1. Fragen-Reihenfolge, Email-Platzierung
2. CTA-Text, Step-Anzahl
3. Modus (Standard vs. Conversational)
4. Progress Bar Stil

---

### 13.9 Drop-off Ursachen-Framework

```
Abbruch in Step 1 / Welcome Screen
→ Mismatch zwischen LP-Versprechen und erster Frage
→ Erster Eindruck des Wizards nicht einladend
→ Erste Frage zu sensitiv für den Einstieg
→ Ladezeit zu hoch (performance Event prüfen)

Abbruch in der Mitte
→ Frage ist zu komplex oder unerwartet (hesitation_ms prüfen)
→ Zu viele Felder pro Step
→ Validierungsfehler frustriert User (field_error Rate prüfen)
→ step_back Events häufen sich → vorheriger Step unklar

Abbruch am letzten Step (last_active_field prüfen)
→ Email/Telefon-Abfrage wirkt wie Falle
→ Fehlende Erklärung warum Kontaktdaten nötig sind
→ Kein klarer Gegenwert kommuniziert
→ Submit-Button nicht im Viewport (Mobile Keyboard)

Abbruch über alle Steps gleichmäßig
→ Grundsätzliches Vertrauen-Problem → Trust Signals fehlen
→ Modus falsch gewählt für die Zielgruppe
```

---

### 13.10 Known Pitfalls

Diese Fehler sind in der Praxis aufgetaucht und müssen beim Setup aktiv vermieden werden:

| # | Problem | Symptom | Lösung |
|---|---|---|---|
| 1 | Enhanced Conversions kommen nie bei Ad-Plattform an | User-Daten werden gesendet aber nicht gematcht | `window.gtag('set', 'user_data', {...})` statt `dataLayer.push` – falsches Format killt Enhanced Conversions lautlos |
| 2 | Health-Check zerstört aktive Sessions | Alle laufenden Sessions werden als abandoned markiert | Health-Check darf nur `SELECT COUNT(*)` ausführen – nie schreiben |
| 3 | `page_leave` wird doppelt gesendet | Doppelte Events in DB, verfälschte Metriken | Flag-Variable (`pageLeafSent`) verhindert Doppel-Sends aus React Cleanup + sendBeacon |
| 4 | `step_time` enthält Unix-Timestamp statt Dauer | Duration-Werte im Millionen-Bereich | Delta-Berechnung: `Date.now() - stepStartTime`, nicht `Date.now()` direkt |
| 5 | Abbruch-Step zeigt falschen Wert | "Abgebrochen bei Feld X" obwohl User auf Step 4 war | `page_leave` Event muss `current_step` + `fields_touched_in_step` direkt aus State lesen, nicht aus DB-Zustand |
| 6 | Feld-Name Frontend ≠ DB-Spalte | Felder werden nicht gespeichert, Partial Leads unvollständig | Explizites Mapping Frontend-Feldname → DB-Spaltenname dokumentieren und testen |
| 7 | OAuth-Token-Request für externe API schlägt fehl | API-Calls laufen ins Timeout | `Content-Type: application/x-www-form-urlencoded` für Token-Requests, nicht `application/json` |
| 8 | API liefert unsinnige Werte | Negative Preise, invertierte Ranges werden als Erfolg behandelt | Immer serverseitige Validierung der API-Response mit definierten Grenzwerten + Error-Logging |

---

## 14. Post-Submit

Der am häufigsten vergessene Teil – genauso wichtig wie der Wizard selbst.

### Was direkt nach Submit passieren muss

1. **Klare Bestätigung** was passiert: "Wir melden uns innerhalb von 24h per Email" – kein generisches "Formular gesendet"
2. **Erwartungsmanagement:** Wie, wann und über welchen Kanal kommt Rückmeldung?
3. **Nächster Schritt:** Was kann/soll der User jetzt tun?
4. **Conversion-Events** feuern – nach dem Submit, nicht davor

*Tracking-Hinweis: Thank-You-Page-Aufrufe als separate Macro-Conversion tracken. Wenn Thank-You-Page-Views deutlich unter Submit-Events liegen: technisches Problem.*

### Thank-You Page als Conversion-Tool

```
Mögliche Next Steps:
├── Termin direkt buchen (Calendly, etc.)
├── WhatsApp öffnen ("Schreib uns direkt")
├── Guide / PDF herunterladen
├── Weitere Qualifizierung (optionale Fragen)
├── Social Sharing
└── Upsell / Cross-Sell (nur wenn passend)
```

### Partial Lead Follow-up

Wenn User die Email hinterlassen aber nicht abgeschlossen haben:

**Datenschutz-Check zuerst:** Follow-up per Email ist nur erlaubt wenn der User bereits einen Consent gegeben hat (falls das Projekt einer Datenschutzverordnung unterliegt). Hat der User vor dem Consent-Step abgebrochen: kein Email-Follow-up. Nur anonymes Retargeting via Pixel möglich.

Wenn Follow-up erlaubt:
- Automatisiertes Follow-up nach 24h
- Betreff: "Du warst fast fertig..."
- Link direkt zum Step wo sie abgebrochen haben

---

## 15. Accessibility

Accessibility ist kein optionales Feature – es wird von Anfang an mitgedacht, nicht nachträglich ergänzt.

### Pflicht-Regeln

| Regel | Standard | Warum |
|---|---|---|
| Keyboard-Navigation | Tab, Enter, Esc muss funktionieren | Screen Reader, Motor-Impairments |
| Labels immer sichtbar | Nie nur Placeholder | Screen Reader liest Placeholder nicht vor |
| Fehler nicht nur in Farbe | Immer Farbe + Icon + Text | Colorblindness (~8% der Männer) |
| Farbkontrast Text | Min. 4.5:1 (WCAG AA) | Sehbehinderungen |
| Farbkontrast Buttons | Min. 3:1 | |
| Focus-State sichtbar | Deutlicher Rahmen um aktives Element | Keyboard-Navigation |
| ARIA-Labels | Für Icons und nicht-beschriftete Elemente | Screen Reader |
| prefers-reduced-motion | Animationen deaktivieren wenn eingestellt | Vestibuläre Störungen |
| Auto-Advance + Keyboard | Auto-Advance nur bei Maus/Touch | Keyboard-User dürfen nicht ungewollt weiterspringen |

### Häufige Fehler

- Placeholder als Label-Ersatz (verschwindet beim Tippen)
- Fehler nur mit roter Farbe markieren
- Kein sichtbarer Focus-State
- CAPTCHA (blockiert Assistive Technology)
- Auto-Advance bei Keyboard-Navigation aktiv

---

## 16. Konflikte & Trade-offs

Diese Punkte haben keine universell richtige Antwort. Jeder muss bewusst entschieden werden.

### Conflict 1: Email früh vs. spät

| Früh (Step 1–2) | Spät (letzter Step) |
|---|---|
| Partial Lead auch bei Abbruch | Höhere Completion Rate |
| Weniger Completions | Kein Partial Lead bei Abbruch |
| Gut bei Nurture-fokussiertem Funnel | Gut wenn Completion primäres Ziel |

**→ Klärungsfrage:** Ist ein unvollständiger Lead mit Email wertvoller als eine höhere Completion Rate?

---

### Conflict 2: Weniger Felder vs. bessere Lead-Qualität

| Weniger Felder | Mehr Felder |
|---|---|
| Mehr Leads | Weniger Leads |
| Niedrigere Lead-Qualität | Höhere Lead-Qualität |
| Mehr Nachqualifizierungsaufwand | Weniger Aufwand |
| Gut für Top-of-Funnel | Gut für Bottom-of-Funnel |

**Aagaard-Warnung:** Felder blind reduzieren kann Conversion senken wenn die "guten" Felder entfernt werden.

**→ Klärungsfrage:** Was ist das Ziel – Lead-Volumen oder Lead-Qualität?

---

### Conflict 3: Conversational vs. Schnelligkeit

| Conversational | Classic/Standard |
|---|---|
| Höhere Completion (emotionale Themen) | Schneller ausgefüllt |
| Bessere Datenqualität | Effizienter für bekannte Abläufe |
| Mobile-friendly | Besser für B2B Power User |
| Mehr Entwicklungsaufwand | Einfacher zu bauen |

**→ Klärungsfrage:** Wer ist die Zielgruppe und wie emotional/sensibel ist das Thema?

---

### Conflict 4: Single Column vs. Double Column

| Single Column | Double Column |
|---|---|
| Immer die sicherere Wahl | Kann bei 13+ Feldern besser konvertieren |
| Besser für Mobile | Weniger gut auf Mobile |
| Eye-Tracking: linear, weniger Fehler | Eye-Tracking: komplexer, mehr Fehler möglich |
| Wizard/Standard: immer | Classic mit vielen Feldern: testen |

**→ Faustregel:** Single Column als Default. Double Column nur im Classic Mode mit 10+ Feldern testen.

---

## 17. Quick-Reference

### Vor dem Start: Checkliste

**Konzeption**
- [ ] Wizard-Typ bestimmt (Single-Step / Linear / Minimal Branching / Branching / Hybrid)?
- [ ] Rendering-Modus gewählt (Classic / Standard / Conversational)?
- [ ] Quantity vs. Quality entschieden?
- [ ] Email-Platzierung entschieden (früh oder spät)?
- [ ] Alle Felder gerechtfertigt?
- [ ] Sensitive Felder mit Erklärung versehen?
- [ ] Container-Format gewählt (Embedded / Two-Step Fullscreen-Overlay / Full-Page)?
- [ ] Welcome Screen nötig?
- [ ] Browser-Back-Verhalten definiert?

**Tracking**
- [ ] Step-View und Step-Complete Events für jeden Step definiert?
- [ ] Field-Level Error Tracking definiert?
- [ ] Last Active Field in page_leave Event enthalten?
- [ ] Traffic-Source als Dimension in Events vorhanden?
- [ ] Device-Type als Dimension vorhanden?
- [ ] Bei Branching: Branch-Pfad als Dimension definiert?
- [ ] Abgestufte Conversion-Werte definiert?
- [ ] Submit-Fehler werden geloggt?
- [ ] Verlangt das Projekt Third-Party Tracking? → Welches, für welchen Zweck?
- [ ] A/B-Test Variante als Dimension vorgesehen (wenn relevant)?

**Technisch**
- [ ] Server Error Handling implementiert?
- [ ] State-Save (localStorage) bei Submit-Fehler implementiert?
- [ ] Auto-Advance bei Keyboard-Navigation deaktiviert?
- [ ] Accessibility geprüft (Keyboard, Kontrast, Labels, Focus-States)?
- [ ] Post-Submit-Erlebnis definiert?
- [ ] Datenschutz-Anforderungen geklärt (projektspezifisch)?

---

### Die wichtigsten Zahlen

| Fakt | Quelle |
|---|---|
| Multi-Step vs. Single-Step: +86% Conversion | HubSpot |
| Multi-Step Completion Rate: 13.9% vs. 4.5% | Formstack |
| Conversational vs. Multi-Step: deutlich mehr Qualified Leads | Verschiedene Marketing-Automation-Studien (kein verifizierter Einzelwert) |
| Progress Bar: +25% Completion | FormAssembly |
| Inline Validation: +22% Success Rate | Luke Wroblewski |
| Telefon-Feld: −5% bis −18.7% Conversion | IvyForms / Brixon |
| Nav entfernen von LP: +100% Conversion | Studie |
| Two-Step Button → Fullscreen: +1375% | Aweber (Kontextabhängig, eigene Tests nötig) |
| Social Proof im Wizard: +26% | Reform |
| Felder 11→4: +120% | Imagescape |
| Expedia extra Feld: −$12 Mio/Jahr | Venture Harbour |
| Abandonment Time: 1 Minute 43 Sekunden | IvyForms |

### Psychologie auf einen Blick

| Prinzip | Anwendung |
|---|---|
| Sunk Cost Fallacy | Sensitive Daten ans Ende (zeitbasiert) |
| Commitment & Consistency | Auto-Save, Partial Leads reaktivieren (identitätsbasiert) |
| Foot in the Door | Einfachste Frage zuerst |
| Endowed Progress Effect | Progress Bar startet bei ~15% |
| Goal Gradient Effect | "Fast geschafft" am letzten Step |
| Quid Pro Quo | Benefit-orientierte CTAs |
| BJ Fogg | Motivation × Ability × Trigger müssen alle stimmen |
| Zeigarnik | Wizard sichtbar starten lassen |

### Input-Hierarchie

```
Visuelle Kacheln (bis 5 Optionen)
> Radio Buttons / Checkboxes
> Segmented Control
> Dropdown (ab 6 Optionen, mit Search ab 10)
> Slider / Stepper
> Freitext (Einzeiler)
> Freitext (Mehrzeiler) – so selten wie möglich
```

### Felder pro Step

| Modus | Desktop | Mobile |
|---|---|---|
| Conversational | 1 | 1 |
| Standard | 2–3 | 1–2 (empfohlen 1, max. 2) |
| Classic | 4–5 | 2–3 |

### Animation Timing

```
Micro-Interaction (Klick, Hover, Validation): 100–200ms
Step-Transition:                              300–400ms
Loading States:                               sofort anzeigen,
                                              eigene Regeln (→ Sektion 7)
Transitions über 500ms:                       wirkt kaputt
```

---

*Version 2.0 – April 2026*
*Basierend auf: HubSpot, Formstack, Venture Harbour, NN/g, Baymard Institute,*
*Luke Wroblewski, Freedman & Fraser, Cialdini, BJ Fogg, KAIST Study 2023, Aweber,*
*IvyForms, Zuko Analytics, Intercom, ConversionXL, Reform, Leadformly,*
*sowie eigenem Battle-Tested Tracking Playbook*
