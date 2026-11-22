---
name: app-content
description: Use for any content work in this app - researching, writing, extending, correcting or reviewing its competencies, chapters, pages, rounds, questions, exercises, figures, terms or sources. This app's own content decisions; they take precedence over the generic lernapps content skills. Load it before you change any content.
---

# Content guide of this app

Explainer „Muster und Zählen“ (Issue lernapps/apps#386, Epic #402), Strang `mathematik/arithmetik`, Stufe 5–6. Gemeinsame
Regeln des Epics: `docs/mathe-epic/regeln.md` (Schreibweisen, Aufgaben, Quellen); sie gelten zusätzlich zu diesem Guide.

## Curriculum

- Deutschland, Hessen (Annahme), Sek I Gymnasium, Stufe 5–6. Die Reihenfolge gibt die Lernlandkarte Mathematik
  (`https://lernapps.net/apps/map/mathematik.json`, Grundlage KMK-Bildungsstandards ESA/MSA 2022); der Hessische Lehrplan
  wurde nicht geöffnet (nicht geprüft). Kein eigenes Material der Auftraggeber.
- Abgrenzung: Das Rechnen selbst steht in #385, Teiler und Primzahlen in #389, Potenzgesetze und Wurzeln in #392,
  Terme mit Variablen in #393, das Baumdiagramm des Zufalls in #401. Hier nicht behandeln.

## Competencies

Kapitel `muster` „Muster aus Plättchen“ (Seiten in dieser Reihenfolge):

- `muster/recap` (recap `mathematik/natuerliche-zahlen`, `mathematik/grundrechenarten-rechengesetze`): keine Übung.
- `muster-zahlenfolgen` – „Ich kann Zahlenfolgen fortsetzen und die Regel mit Worten und mit einem Term beschreiben.“
  Seiten `muster/folgen`, `muster/regel`.
- `potenzen` – „Ich kann Potenzen mit natürlichen Exponenten berechnen und Zehnerpotenzen zum Darstellen großer Zahlen
  nutzen.“ Seiten `muster/quadrat-kubik`, `muster/zehnerpotenzen`.
- `zaehlprinzip` – „Ich kann mit dem Zählprinzip und Baumdiagrammen die Anzahl von Möglichkeiten bestimmen.“ Seiten
  `muster/tabelle`, `muster/baum`.

Übungs-ids stehen in den Seiten (`src/muster/*.yaml`); jede Seite hat mindestens vier Übungen, jeder Baustein mindestens
drei mit steigender Schwierigkeit.

## Content structure

- Eine Seite = ein Schritt. Abschnitts-ids überall gleich: `einstieg` (leichte erste Aufgabe vor der Erklärung, mit
  Begründung), `darstellung` (Bild + Erklärung), `beispiel` (`example`-Box), `merke` (Fehlerhinweis), `uebung`,
  `weiter` (Belohnung und nächster Schritt). Nicht jede Seite hat alle; Titel sagen, was der Abschnitt tut.
- Höchstens 350 Wörter Lesetext je Seite, höchstens vier Textblöcke hintereinander, in den ersten vier Blöcken ein Bild
  oder eine Aufgabe.
- **Muster `regel`:** Nur diese Seite führt den Platzhalter („Nummer des Bildes“, Kästchen oder n) ein. Regeln in Worten
  mit Platzhalter; kein Termumformen, keine Unbekannte (Abgrenzung zu #393, vom Orchestrator bestätigt).
- **Geschichte:** gezeichnete Kinder Mira (11) und Ben (10) richten die Spielecke ihrer Klasse ein; jede Seite löst einen
  Schritt davon und endet mit dem nächsten. Namen, Alter und Ort bleiben so. Kein Kindchenschema, keine Marken.

## Terminology

- Wörter der Karte: „Zahlenfolgen und Muster“, „Potenzen und Zehnerpotenzen“, „Zählprinzip“. Darstellungen heißen überall
  gleich: **Plättchenbild**, **Rechteckmodell**, **Stellenwerttafel**, **Baumdiagramm**. „Zahlenstrahl“ nur falls ein
  Strahl vorkommt (keine negativen Zahlen, also nie „Zahlengerade“); nie auf einer Seite wechseln.
- Schreibweisen: `·` und `:` (nie `*`, `/`), Minus `−`, große Zahlen ab fünf Stellen mit schmalem geschütztem Leerzeichen
  (`1 000 000`), vierstellig ohne Lücke, Eingabefelder akzeptieren Komma und Punkt. Anrede „du“, kurze Sätze, kein „man“
  in Arbeitsaufträgen. Potenzen als `3^4` im Quelltext, gesetzt als 3⁴; sprich „3 hoch 4“.
- Neue Wörter (Potenz, Basis, Exponent, Zählprinzip) werden am Beispiel eingeführt und stehen bei erster Verwendung im
  Text; Glossar aus `definition`-Blöcken.

## Exercise patterns

| Muster | Baustein | Form | Beispiel |
|---|---|---|---|
| Folgenglied vorhersagen | muster-zahlenfolgen | `generated`, `given` Startwert und Differenz, `mistakes`: Differenz mit Faktor verwechselt, Bildnummer statt Anzahl | `muster/folgen` |
| Regel in Worten | muster-zahlenfolgen | `single-choice`, `generated` (Anzahl für Bild n), `number` | `muster/regel` |
| Potenz berechnen | potenzen | `generated`, `mistakes`: Basis·Exponent, Basis+Exponent, Exponent als Basis | `muster/quadrat-kubik` |
| Potenz deuten | potenzen | `matching` Potenz ↔ Faktoren, `true-false` mit Begründung | `muster/quadrat-kubik` |
| Zehnerpotenz | potenzen | `generated` (Nullen zählen, 10^n ausschreiben), `ordering` | `muster/zehnerpotenzen` |
| Möglichkeiten zählen | zaehlprinzip | `generated` (Produkt der Auswahlen, `mistakes`: addiert), `number`, `single-choice` | `muster/tabelle`, `muster/baum` |

Wertebereiche: Basen 2–10, Exponenten 2–4, Zehnerpotenzen bis 10⁹; Folgen mit Differenz 2–9, Startwert 1–20, bis
Bild 10; Zählaufgaben mit 2–4 Stufen, je 2–5 Auswahlen, höchstens 60 Möglichkeiten. Jede Aufgabe hat eine Rechenprobe in
der Musterlösung; kein `mistake` darf für gezogene Werte dieselbe Zahl wie die Antwort geben.

## Figures

- Eigene SVG als `image` (`src/images/`), Bild zeigt nur das Gegebene, nie die Antwort. Plättchen: Kreise, Quadrat- und
  Würfelmodell als Lagen; ab zwei Lagen mit Beschriftung der Lage, nie Farbe allein als Information. Baumdiagramm: Wurzel
  links, Stufen nach rechts, Äste beschriftet.
- Jedes Bild hat `alt` (nennt Zahlen und Struktur: „4 Reihen mit je 4 Plättchen“) und eine `caption`, die sagt, worauf
  man achtet. Eigene Zeichnung, Lizenz wie die App (CC BY 4.0 für Inhalte).
- Stellenwerttafel: Aufbau, Spaltenbeschriftung, Farben und Bündeln nach den Konventionen von #385, sobald der
  Orchestrator sie meldet.

## Sources

- Lernlandkarte Mathematik, KMK-Bildungsstandards Mathematik 2022 (Abschnitt Zahl und Operation, nicht im Wortlaut
  übernommen), eigene Herleitungen und Aufgaben. Keine Schulbuch- oder Arbeitsblatttexte, keine Dritt-Inhalte, keine
  Videos. Hessischer Lehrplan: nicht geprüft.

## Adding a chapter or round

1. Kompetenzen aus der Karte wählen (ids, „Ich kann …“ unverändert), Reihenfolge nach `requires`.
2. Ordner `src/<kapitel>/` mit `chapter.yaml`, Kapitel in `src/app.yaml` unter `chapters` eintragen.
3. Pro Kompetenz eine Seite nach Abschnitts-ids oben, Bild als SVG mit `alt`, mindestens vier Übungen aus den Mustern.
4. Voraussetzungen von außerhalb in einer Sammel-Wiederholung (`recap`) am Kapitelanfang.
5. `npx vp check --fix`, `npx vp build`, `npx --no -- lernapps check`, committen.

## Rules learned from mistakes

- Keine Wikipedia- oder anderen externen `links:` an Aufgaben (regeln.md §4, „Nachschlagen ist keine Quelle“); das Werkzeug verlangt einen Link, also zeigt er auf die Kartenseite des Bausteins (`https://lernapps.net/apps/map/mathematik/c/<baustein>/`). Fehler stammte aus der ersten Musterseite.
- Keine `$…$`-Formeln in Seiten von `matching`: der Test ohne JavaScript vergleicht den Quelltext. Unicode-Hochzahlen (2³) verwenden.
- Stellenwerttafel wie in #385: Spalten von rechts E, Z, H, T mit Kürzel und Namen im Kopf, Plättchen als runde Marke mit Kürzel, Bündeln = zehn Plättchen werden eines links, Zahl unter der Tafel mit schmalem Leerzeichen ab 5 Stellen.
