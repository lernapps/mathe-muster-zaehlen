---
# Read by the hooks, the review, the evals. Schema: @lernapps/tooling/guidance/plan-front-matter.v1.schema.json
# Written by `lernapps plan` and the hooks. Never change a key or a value by hand.
# Archetype, null until chosen in Explore. Allowed values: explainer, interactive, quiz.
archetype: explainer
# Current phase. Allowed values: explore, plan, code, commit.
phase: commit
# prePushFailures: failed pre-push runs, written by the hook.
prePushFailures: 0
# failedChecks: failed rules and runs, written by lernapps check and the hooks.
failedChecks: { checks-pass: 6 }
---

# Plan: mathe-muster-zaehlen, first version

<!--
For you, the assistant. The process is in AGENTS.md; this plan holds the method.
- `npx --no -- lernapps plan next` prints the task to do now, `plan done` ticks it and prints the next one.
- You write only below Goal, Key decisions, Notes, Answers, Entry draft, Content method and Retrospective, in the
  creator's language. Delete the comment of a section once the section is filled.
- Work on the branch `work`, locally: push nothing before Commit.
-->

*Started 2026-11-22. Explore, Plan, Code, Commit.*

## Goal

Kinder der Stufe 5–6 legen Plättchenmuster, setzen sie fort und beschreiben die Regel; sie deuten Potenzen als wiederholtes Malnehmen (Quadrat, Würfel, Zehnerpotenzen) und zählen Möglichkeiten systematisch (Plättchenfeld → Tabelle → Baum). Auftrag: lernapps/apps#386, Strang `mathematik/arithmetik`, ein Kapitel, drei Bausteine.

## Key decisions

- Archetyp `explainer` (Format 2, `strand: mathematik/arithmetik`): Seiten erklären, Übungen dazwischen; Issue verlangt es. Kein Spiel, keine Zeitnahme nötig.
- Selbsteinschätzung im Kapitel `muster` (12 Aufgaben, 3 Schritte mit je 4, je Seite 2 ohne Seitenkontext verständliche `generated`/`number`/`single-choice`-Aufgaben; Recap ausgenommen), nach Skill.
- Kein `scope` in `src/app.yaml` (guess): die App hat keine `open-task` und folgt keinem fremden Material, nur der Karte.
- Matching-Seiten ohne `$…$` (Unicode-Hochzahlen wie 2³): der Runtime-Test der Seite ohne JavaScript vergleicht sonst den Quelltext mit dem gesetzten Text (Fund fürs Plattform-Team, nicht selbst behoben).
- Der Auftrag (Issue #386, vom Orchestrator geliefert) ersetzt das Interview: Goal, Learners, Content, Amount stehen dort. Languages, Look, Terms, Finding (guess), siehe Answers.

## Notes

**Strang:** `mathematik/arithmetik`, Stufe 5–6, ein Kapitel „Muster aus Plättchen“. Karte `mathematik.json` gelesen (KMK-Bildungsstandards 2022, Status draft).

**Bausteine der Karte (alle `practisedBy` leer = Lücken, alle Schritt 4, Band 5-6):**
- `muster-zahlenfolgen` – „Ich kann Zahlenfolgen fortsetzen und die Regel mit Worten und mit einem Term beschreiben.“ (opens 0)
- `potenzen` – „Ich kann Potenzen mit natürlichen Exponenten berechnen und Zehnerpotenzen zum Darstellen großer Zahlen nutzen.“ (opens 44)
- `zaehlprinzip` – „Ich kann mit dem Zählprinzip und Baumdiagrammen die Anzahl von Möglichkeiten bestimmen.“ (opens 6)

**Voraussetzungen von außen:** alle drei `requires: grundrechenarten-rechengesetze` (#385, Schritt 3, requires `schriftliche-verfahren`). Zehnerpotenzen knüpfen laut Issue an die Stellenwerttafel an (`natuerliche-zahlen`, #385). Beides wiederholt eine Sammel-Wiederholung am Kapitelanfang (`recap: [mathematik/natuerliche-zahlen, mathematik/grundrechenarten-rechengesetze]`), kompakt, ohne Übung. Keine Verlinkung in die App von #385.

**Nachfolger (Abgrenzung, nicht hier):** `primfaktoren-ggt-kgv` (#389), `quadratwurzeln`, Potenzgesetze (#392), `zufall-baumdiagramm` (#401), Terme mit Variablen (#393).

**Didaktik:** Rechteckmodell mit Plättchen trägt alles: Muster Bild für Bild, Quadratzahlen als Quadrate, Kubikzahlen als Würfel, Zehnerpotenzen als Stellenwerttafel, Zählen als Feld → Tabelle → Baum. Lernende sagen das nächste Bild voraus, bevor es erscheint.

**Seitenentwurf (ein Kapitel, vorläufig; Plan konkretisiert):**
0. Recap „Das brauchst du hier“ (natuerliche-zahlen, grundrechenarten-rechengesetze)
1. Muster fortsetzen (muster-zahlenfolgen): Plättchenbilder, Folge, Regel in Worten
2. Regel als Term (muster-zahlenfolgen): Rechenvorschrift für das n-te Bild
3. Quadrat- und Kubikzahlen (potenzen): Potenz als wiederholtes Malnehmen
4. Zehnerpotenzen (potenzen): Stellenwerttafel, große Zahlen
5. Zählen mit Tabelle (zaehlprinzip): Plättchenfeld, Outfits aus 3 Shirts und 2 Hosen
6. Zählen mit Baum (zaehlprinzip): Baumdiagramm, Zählprinzip als Malnehmen

**Funde für den Orchestrator (nicht selbst beheben):**
- Karte: `muster-zahlenfolgen` verlangt „mit einem Term beschreiben“ in Stufe 5-6; Variablen stehen aber erst in #393. Wir führen *n* nur als „Nummer des Bildes“ am Beispiel ein, mit Rechenvorschrift in Worten und einfachem Term; kein Termumformen.
- Karte: `quadratwurzeln` requires `potenzen`; Quadratzahlen hier sind die Umkehr-Grundlage, Wurzeln selbst nicht hier.

**Wie Lernende ans Ziel kommen (Herleitung) und welcher Fehlvorstellung die Rückmeldung begegnet:**
- `muster-zahlenfolgen`: sie sagen das nächste Plättchenbild voraus, zählen die neuen Plättchen, finden die Regel („+3 je Bild“, „Bild n hat 2·n + 1 Plättchen“) und prüfen sie am Bild. Fehlvorstellung: Differenz mit Verhältnis verwechseln; Regel nur für das letzte Paar statt für die ganze Folge; Bildnummer mit Plättchenzahl verwechseln.
- `potenzen`: sie legen 3·3 als Quadrat, 3·3·3 als Würfel, 10·10·10 als Stellenwert; Potenz = gleiche Faktoren. Fehlvorstellung: 3⁴ = 3 · 4 = 12; 10³ = 30; Exponent als Anzahl Nullen falsch gelesen; Basis und Exponent vertauscht.
- `zaehlprinzip`: sie legen ein Plättchenfeld (3 Shirts × 2 Hosen), lesen es als Tabelle, dann als Baum; Anzahl = Produkt der Auswahlen je Stufe. Fehlvorstellung: addieren statt multiplizieren; Stufe vergessen; Reihenfolge-Verwechslung (hier noch kein Fakultät, nur Stufen mit unabhängiger Auswahl).

**Baustein → Seite (Kapitel 1 „Muster aus Plättchen“), Voraussetzungen, die die App nicht übt:**
- Seite 0 `recap` (Wiederholung): natuerliche-zahlen, grundrechenarten-rechengesetze – übt nichts.
- Seite 1 Muster fortsetzen → `muster-zahlenfolgen`; extern: grundrechenarten-rechengesetze (im Recap).
- Seite 2 Regel als Term → `muster-zahlenfolgen` (zweite Seite desselben Bausteins, groß genug für zwei Seiten).
- Seite 3 Quadrat- und Kubikzahlen → `potenzen`; extern: grundrechenarten-rechengesetze.
- Seite 4 Zehnerpotenzen → `potenzen`; extern: natuerliche-zahlen (Stellenwerttafel, im Recap).
- Seite 5 Zählen mit Tabelle → `zaehlprinzip`; extern: grundrechenarten-rechengesetze.
- Seite 6 Zählen mit Baum → `zaehlprinzip`.
Abhängigkeiten der Veröffentlichung: #385 (grundrechenarten-rechengesetze) zuerst veröffentlicht oder Freigabe des Orchestrators.

**Lernenden-Check der Musterseite (Sub-Agent, 360 und 1280 px, Tastatur) und was ich geändert habe:** unklare Wörter Reihe/Faktor/„Ergebnis“ → im Text erklärt; Würfelbild „nebeneinander“ vs. „übereinander“ → Bildunterschrift und Text benennen es, Exponent = Zahl der Lagen gesagt, Kubikzahl erklärt; doppelte Rechnung im Beispielkasten entfernt; Wahr-Falsch-Aufgabe verriet sich durch das Merke → andere Zahlen (2⁵); Zuordnung zählte Faktoren mit → Anzahl-Hinweise aus den Antworten gestrichen, Ablenker 3 · 4 zugefügt; keine Aufgabe „als Potenz schreiben“ → `single-choice` ergänzt; Tipp gab Lösung fast preis → gestuft; Rückmeldungen ohne Grund → mehr `mistakes`, Würfelantwort ohne Begriff Basis. Nicht von mir behebbar (Runtime, Fund für den Orchestrator): „Neue Aufgabe“-Knopf nur Symbol und Zähler „Aufgabe Nr.“ läuft unregelmäßig; Meldung „Antworte zuerst: Wähle, tippe oder ordne alles zu“ auch bei falscher Eingabeform im Zahlenfeld; `definition`-Box sieht aus wie ein Link; Exponent bei 360 px klein (13 px); Zuordnung markiert falsche Einträge nur mit rotem Rand und „×“. Nicht geprüft: Bildschirmleser.

**Quellen (erlaubt):** Lernlandkarte, KMK 2022, eigene Herleitungen und Aufgaben. Nicht geöffnet: Hessischer Lehrplan (offen, nur Annahme der Schreibweisen aus regeln.md Abschnitt 2). Keine Schulbuchinhalte, keine Dritt-Inhalte.

**Übungsmuster (Skill exercise-patterns, mathematics):** `generated` mit festem Seed und `mistakes` (z. B. „Du hast 3 · 4 statt 3⁴ gerechnet“, „Exponent mit Basis multipliziert“), `number` für Folgenglieder und Anzahlen, `ordering`/`true-false`/`single-choice` für Regeln und Deutungen, `image` (SVG, eigene Plättchenbilder) mit Textalternative; Komponente (Plättchenfeld) nur falls ein Block nicht reicht, mit statischer Form zuerst.

**Umfang:** drin: natürliche Exponenten, Zehnerpotenzen bis 10⁹ (Anzahl Nullen), Folgen mit konstanter Differenz, Quadrat-/Dreieckszahlen, Zählprinzip mit 2–3 Stufen. Raus: negative Exponenten, Potenzgesetze, Wurzeln, Kombinatorik mit Fakultät, Wahrscheinlichkeit. Wertebereich: Basen 2–10, Exponenten 2–4 (Zehnerpotenzen bis 10⁹, Zahlen bis 1 000 000 000); Folgen mit Differenz 2–9 und Startwert 1–20, bis Bild 10; Zählaufgaben mit 2–4 Stufen und je 2–5 Auswahlen (höchstens 60 Möglichkeiten). Gründe: Plättchenbild bleibt lesbar auf 360 px; Fakultät und Wahrscheinlichkeit gehören zu #401. Sprache: nur Deutsch.

## Explore

<!--
- Find out what the app teaches, for whom, how much and how it looks. Ask; write no code, run no `create`.
- An answer counts only in the creator's words under "Answers". At most 2 questions per message, one topic each.
-->

### Tasks

- [x] Check the start: the folder `.agents/skills/lernapps-app` exists (else stop and tell the creator that the folder
      was not started with `init`), and `git branch --show-current` prints `work` (else `git switch -c work`).
- [x] Load skill `lernapps-app`. Tell the creator in two sentences what a lernapps app is and where it will live: at
      their own address, free and public, and once listed as a copy on lernapps.net. Say that the technical part
      (GitHub) comes at the end and that you do it.
- [x] Interview: ask the topics "Goal" and "Learners" of "Answers".
- [x] Load skill `lernapps-map-assignment` and read the learning map of the subject as it says. The creator brings
      the content themselves (material, a word list, the pages): note under "Notes" which competencies of the map it
      covers. Else write the skill's assignment, with its story; the creator's yes answers the topics Content and
      Amount. A subject without a map: skip this task and say so.
- [x] Load skill `lernapps-exercise-patterns` and read its reference for the subject. Note under "Notes" how learners
      will practise what the goal names.
- [x] Choose the archetype as skill `lernapps-app` says: read the README of each archetype in question, then tell the
      creator in plain words what the chosen one can and cannot do. Write the archetype and its reason under "Key
      decisions".
- [x] Run `npx --no -- lernapps skills --archetype <name>` with the chosen archetype. It installs the archetype's
      skills and adds the archetype's tasks to this plan.
- [x] Load skill `lernapps-explainer-design`. An explainer has the look of the runtime: write "fixed by the
      archetype" under the topic "Look and feel" of "Answers".
- [x] Interview: ask every other topic of "Answers", in order. Leave out only a topic that an answer of the creator
      already covers, and note which answer. A topic nobody answered is asked once before you write an assumption
      with "(guess)".
- [x] Load skill `lernapps-content-research` and research as it says. Write under "Notes": the strand or subject, the
      competencies by chapter with their ids, the sources you opened.
- [x] Write under "Notes" which competency goes on which page and which pages form a chapter, as "Map the content" of
      skill `lernapps-explainer-design` says. Per page, name the prerequisites the app does not practise.
- [x] Write under "Notes", one line per competency: how learners get there (they derive it, they do not only read it
      off), and which misconception the feedback catches.
- [x] Write under "Notes" the scope: what is in, what is out and why, the data range (for example "all main-group
      elements", never a silent "1–20"), the languages.
- [x] **Checkpoint:** research. Show in plain words: the strand or why none, the competencies by chapter, the didactic
      approach, the scope, every "(guess)", the sources and what is unchecked, the archetype and its reason. Stop and
      wait. Changes: change them, then ask again.
      Creator: Orchestrator (in Vertretung): Recherche freigegeben; Term-Fund bestätigt (Regel in Worten mit Platzhalter, kein Termumformen); Musterseite = Quadrat- und Kubikzahlen

### Answers

<!-- The interview: per topic the creator's answer, in their words. Keep the topics. -->

- Goal: laut Issue #386 (Leitidee): „Ich verstehe, dass Zahlen eine innere Struktur haben, die man in Plättchenmustern sieht, und kann Zahlenfolgen, Potenzen als wiederholtes Malnehmen und das systematische Zählen von Möglichkeiten nutzen.“ (Auftragstext, nicht Gespräch)
- Learners: Mathematik, Stufe 5–6; Vorwissen laut Karte: schriftliche Verfahren, Vorrangregeln (#385). (Issue)
- Model and focus: an app of the catalog (https://lernapps.net/apps/llms.txt) as model; what matters most (exercises,
  visualisations, game feel).
- Hurdles: misconceptions and mistakes of the learners; the creator's examples and experiments.
- Content: Session schreibt aus Karte und eigenen Herleitungen; kein Fremdmaterial. (Issue, regeln.md Abschnitt 4)
- Amount: ein Kapitel, sechs Seiten plus Recap, mind. drei Aufgaben je Baustein. Später: #392/#393/#389/#401 in eigenen Explainern. (Issue, regeln.md 3.1)
- Languages: nur Deutsch (guess; Epic nennt nichts anderes).
- Look and feel: calm like a worksheet, or like a game (colours, praise, effects); dark mode.
  → fixed by the archetype (Look der Runtime, ruhig wie ein Arbeitsblatt, Dark Mode folgt dem Gerät).
- Terms: Wörter der Karte: Zahlenfolgen und Muster, Potenzen und Zehnerpotenzen, Zählprinzip; Darstellung „Plättchen“, „Rechteckmodell“, „Baumdiagramm“ (regeln.md 1.5, 2).
- Finding the app: what teachers and parents would search for.

## Plan

<!--
- Map the confirmed content onto the archetype. No new content questions: a gap in the content goes back to Explore.
- The creator confirms the plan in one read. After the yes you work on your own.
-->

### Tasks

- [x] Map the content as "Map the content" of skill `lernapps-explainer-design` says, and write the result under
      "Content method".
- [x] Choose a pattern per competency as skill `lernapps-exercise-patterns` says, and add it to "Content method".
- [x] Add to "Content method" one line per page, as "Engagement" of skill `lernapps-explainer-design` says: the
      opening task, the change of activity, the reward, the story.
- [x] Add the tasks of Code, each one a piece of work that ends in a commit. First the pattern: one complete page or
      screen, `npx --no -- lernapps plan add --at pattern "<task>"`. Then the others, one call each:
      `npx --no -- lernapps plan add --at pages "<task>"`. Each task says what it builds and what it shows.
- [x] Draw a sketch of each screen, component or interactive exercise: a static SVG or image, or the steps with what
      learners see after each. Keep the files in `.vibe/sketches/`.
- [x] Show the creator, short: goal, competencies by chapter, the Code tasks, the sketches, and the content method in
      plain words (what learners see and do, what the app cannot do). At most 2 questions.
- [x] **Checkpoint:** confirm the plan and the content method. Stop and wait for an explicit yes. Changes: change
      them, then ask again.
      Creator: Orchestrator (in Vertretung): Plan und Content-Methode bestätigt; Mira und Ben ok; SVG mit alt statt Komponente ok; Selbsteinschätzung nach Skill

### Content method

<!-- One line each: the patterns and where; the figures and how they are made; the data files; each component, what it
checks and what it cannot; how a later agent adds a chapter. It becomes the content guide in Code. -->
<!-- An explainer: per figure, model and component its learning action in two to four sentences
(`explainer-representation-explained`); per page its prerequisites the app does not practise, and which get a recap
page, which a link. -->

**Geschichte (Schüler bis Klasse 6: gezeichnete Kinder, ein Ort):** Mira (11) und Ben (10) richten die Spielecke ihrer Klasse ein und legen dafür Plättchen aus. Jede Seite löst einen Schritt: Muster für die Wandbilder, Quadrate und Würfel für die Bauecke, Zehnerpotenzen für das Zählen der Plättchendose, Outfits für das Faschingsfest. Namen frei erfunden, einmal im Content-Guide festgelegt. Kein Kindchenschema.

**Seiten, Dateien, Muster (Kapitel `muster`):**

| Seite | Datei | Baustein | Muster |
|---|---|---|---|
| Das brauchst du hier | `muster/recap` | recap natuerliche-zahlen, grundrechenarten-rechengesetze | Selbsttest im Text, keine Übung; nennt beide Bausteine mit `name.de` |
| Muster fortsetzen | `muster/folgen` | muster-zahlenfolgen | `generated` nächstes/n-tes Folgenglied (`mistakes`: Differenz als Faktor, Bildnummer statt Anzahl); `ordering`; `true-false` mit Begründung |
| Die Regel finden | `muster/regel` | muster-zahlenfolgen | Regel in Worten mit Platzhalter („Nummer des Bildes“, Kästchen oder n): `single-choice`, `generated` (Anzahl für Bild n), `number`. **Diese Seite führt den Platzhalter ein; kein Termumformen, keine Unbekannte** (vom Orchestrator bestätigt) |
| Quadrat- und Kubikzahlen | `muster/quadrat-kubik` | potenzen | **Musterseite.** `image` SVG (Quadrat, Würfel aus Plättchen), `generated` (b^e mit `mistakes`: b·e, b+e), `number`, `matching` (Potenz ↔ Faktoren), `true-false` |
| Zehnerpotenzen | `muster/zehnerpotenzen` | potenzen | `table` Stellenwerttafel, `generated` (10^n ausschreiben, Anzahl Nullen), `ordering`, `number` |
| Zählen mit der Tabelle | `muster/tabelle` | zaehlprinzip | `image` Plättchenfeld/Tabelle, `generated` (a·b Möglichkeiten, `mistakes`: a+b), `number`, `single-choice` |
| Zählen mit dem Baum | `muster/baum` | zaehlprinzip | `image` Baumdiagramm (SVG), `generated` 2–3 Stufen, `number`, `true-false`; Rückblick „Was du jetzt kannst“ |

**Voraussetzungen, die die App nicht übt:** grundrechenarten-rechengesetze und natuerliche-zahlen → eine Sammel-Wiederholung am Kapitelanfang (kein Link je Seite). Zweite Voraussetzung von potenzen→primfaktoren liegt in #389, nicht hier.

**Figuren (Lernhandlung):** Plättchenbild (SVG): Lernende zählen die Plättchen je Bild und sagen das nächste voraus; die Bildunterschrift sagt, worauf sie achten (neue Plättchen je Schritt). Quadrat/Würfel: die Kantenlänge ist gegeben, sie ermitteln die Anzahl und lesen die Potenz als gleiche Faktoren. Stellenwerttafel: jede Stelle mal zehn. Plättchenfeld/Baum: Zeilen mal Spalten bzw. Äste je Stufe; das Bild zeigt nur das Gegebene, nie die Antwort. Alle mit `alt`.

**Engagement je Seite:** Einstieg = leichte Aufgabe vor der Erklärung mit Begründung; Wechsel schauen–tun–lesen, höchstens 4 Textblöcke in Folge; Belohnung = „Du kannst jetzt …“ und Ausblick; Wiederholung nur in anderer Form.

**Darstellungen (regeln.md 1.5):** „Plättchenbild“ und „Rechteckmodell“ heißen überall gleich; Stellenwerttafel als `table`; Baumdiagramm ab `muster/baum`.

**Regeländerungen (Orchestrator, regeln.md §2):** „Zahlenstrahl“ (ab 0 nach rechts) gilt, falls ein Strahl vorkommt; „Zahlengerade“ in dieser App nicht (keine negativen Zahlen); nie wechseln auf einer Seite. Brüche gesetzt, nicht `3/4` (hier nicht nötig). Stellenwerttafel: Darstellungs-Konventionen von #385 (Aufbau, Spaltenbeschriftung, Farben, Bündeln) kommen über den Orchestrator; die Seite `zehnerpotenzen` richtet sich danach.

**Komponenten:** keine (guess; kein Block fehlt, `prefer-built-in-block`).

**Schreibweisen:** `·` und `:`, große Zahlen mit schmalem geschütztem Leerzeichen ab 5 Stellen, Eingaben akzeptieren Komma und Punkt, keine Brüche nötig.

**Mindestens drei Aufgaben je Baustein, steigend; mindestens vier Übungen je Seite** (`explainer-interaction`).

**Engagement je Seite (Einstieg · Wechsel · Belohnung · Geschichte):**
- `recap`: Einstieg 3 Kurzfragen (Stellenwert, Klammer vor Punkt) mit Begründung · Wechsel Frage–Lösung · Belohnung „Du bist bereit für die Plättchen“ · Mira und Ben holen die Plättchendose.
- `folgen`: Einstieg: drittes Plättchenbild der Wandreihe fortsetzen, Begründung zeigt „+3“ · schauen–zählen–vorhersagen–prüfen · Belohnung: Folge selbst fortsetzen · Wandbilder für die Spielecke.
- `regel`: Einstieg: wie viele Plättchen hat Bild 10, ohne alle zu legen? · Bild–Regel in Worten–Platzhalter–Aufgabe · Belohnung: Regel für Bild 100 anwenden · Ben will das Wandbild größer.
- `quadrat-kubik`: Einstieg: Quadrat mit Kante 4 legen, Plättchen zählen, Begründung 4·4 · Bild–Beispiel–Regel–Übung · Belohnung: 4³ als Würfel lesen und rechnen · Bauecke aus Quadraten und Würfeln.
- `zehnerpotenzen`: Einstieg: wie viele Plättchen in 10 Zehnerstangen à 10 Reihen? · Tafel–Beispiel–Übung · Belohnung: 1 000 000 als 10⁶ schreiben · Zählen der Plättchendose.
- `tabelle`: Einstieg: 3 Shirts × 2 Hosen als Plättchenfeld zählen · Feld–Tabelle–Rechnung · Belohnung: ohne Feld die Anzahl nennen · Outfits fürs Faschingsfest.
- `baum`: Einstieg: Baum mit zwei Stufen zu Ende zeichnen/zählen · Baum–Vergleich mit Tabelle–Übung · Belohnung: Kapitelrückblick „Was du jetzt kannst“ · Fest ist geplant, die Spielecke fertig.

**Ergänzen später:** Content-Guide `.agents/skills/app-content/SKILL.md`, Seiten in `src/muster/*.yaml`.

### Review

**Lernenden-Prüfer (Sub-Agent, alle 7 Seiten, 360/1280 px, Tastatur auf `baum`):** Befunde und was geändert wurde: Mira (11) und Ben (10), Spielecke und Fest erst im Recap eingeführt, „Bauecke“ zu „Spielecke“, Fest im Frühstück-Beispiel aufgegriffen; Merke „nicht mal 3“ ohne Vorwissen → umformuliert; Wahr-Falsch zu 2, 4, 8, 16 prüfte Ungelehrtes → neue Folge 3, 7, 11, 16 mit Grund; Platzhalter „Kästchen“ nie gezeigt → gestrichen; Regelseite erklärt jetzt, warum mit 3 malgenommen wird; „.:“ in Optionen entfernt; Tipps für Umkehraufgaben (`hosen-gesucht`, `welches-bild`, `mittlere-stufe`); Tabelle gab Antworten vor (Million) → Aufgabe auf 10¹² gestellt, Exponenten 2–9; „Stufe“ im Feedback der Kisten-Aufgabe ersetzt; Rückblick nennt Quadrat- und Kubikzahlen; größere Stellen (ZT, HT, M) im Text benannt. Nicht geändert (Runtime oder bewusst): leere Eingabe zeigt „Wähle, tippe oder ordne alles zu“ (Runtime); Wahr/Falsch und Ordnen melden bei Fehlern nur „Lies dazu noch einmal den Text“ (Runtime); „Aufgabe Nr.“ in der URL (Runtime); `{{answer}}` formatiert große Zahlen mit Punkt als Tausendertrenner in `steps` (verstößt gegen regeln.md §2, deshalb steht dort keine Zahl ≥ 1000 aus `{{answer}}`); Glossar nur drei Begriffe; „Abstand“ statt „Differenz“, „Rechteckmodell“ als Karten-Wort beibehalten; „Reihe/Zeile/Spalte“ in drei Bedeutungen bleibt (Reihe waagerecht im Plättchenbild, Zeile in der Tabelle, Spalte in der Stellenwerttafel; ein Hinweis steht auf der Seite `quadrat-kubik`).

**Fachlicher Prüfer (Sub-Agent):** 32 Aufgaben nachgerechnet, alle Musterlösungen richtig; alle `generated` über den ganzen Wertebereich geprüft (keine Division durch 0, keine unsinnigen Größen, `where` nötig und ausreichend). Befunde und was geändert wurde: `mistake 4*d` passte nicht zur Meldung → `3*d`; doppelte `mistake`-Werte bei einzelnen Zahlenpaaren → per `where` ausgeschlossen; vierstellige Zahlen mit Lücke (`2 407`, `1 000`) → ohne Lücke; Variablen a, b in der Tabellenseite → in Worten; Wort „Term“ fehlte → auf `regel` eingeführt mit Aufgabe `term-waehlen`; Kästchen als Unbekannte (`4 · □ = 12`, `2 · □ · 4 = 24`) → in Worten; `folge-sechs` mehrdeutig → „von klein nach groß“; Tabelle sprang von 10⁴ auf 10⁶ → HT, ZM, HM ergänzt; „Zehnerpotenzen zum Darstellen großer Zahlen“ nur halb → `5000 = 5 · 10³` und Aufgabe `zahl-aus-zehnerpotenz`; Zählprinzip „egal was du zuerst gewählt hast“ ergänzt; „Quadratzahl“ klarer gefasst. Als Hinweis bewusst nicht geändert: Wörter Reihe/Zeile/Spalte.

**Zweiter Lernenden-Durchgang (ganze App, nach den ersten Korrekturen), was ich geändert habe:** Antwort 13 stand im Text vor der Aufgabe (Folge nur bis 10, ohne Glied 13); Überschrift „Plus oder mal?“ → „Immer wieder dasselbe addieren“; Rückmeldungen mit „Faktor“ und „Dazukommende“ vor ihrer Einführung umformuliert; „Produkt“ erklärt, „lateinisch cubus“ gestrichen, Bildunterschrift der Lagen klarer; Schluss von `quadrat-kubik` verweist nicht mehr auf eine nie genannte Wand; Umkehraufgabe der Regelseite fragt nach Bild 40 statt 31 (Antwort stand schon im Text); Wahr-Falsch der Regelseite ist jetzt „stimmt“; richtige Option stand immer an erster Stelle → Reihenfolge in vier Fragen gemischt; Mira-Ben-Wechsel (Mira hat 3 Shirts, dann 4) → Ben; Zählprinzip-Hinweis in `baum` sprachlich korrigiert; Merke zu den Zehnerpotenzen ohne die irreführende Verallgemeinerung; Feedback „13 Ziffern“ lesbarer; Tabelle auf 360 px (Wert und Potenz in einer Spalte). Offen gelassen: Tabelle und Plättchenbild auf `tabelle`/`zehnerpotenzen` stehen nach der Einstiegsaufgabe und lassen sich beim Vorauslesen als Antwort nutzen (Erklärung braucht die Darstellung; Einstieg steht davor), Glossar mit drei Begriffen (Runtime erzeugt es aus `definition`), „Wiederholung“ im Titel der Recap-Seite fehlt (Runtime), Fehlermeldungen der Runtime ohne Grund bei Wahr/Falsch und Ordnen.

**Fachlicher Prüfer, zweiter Lauf (Stand b214c0f):** 22 feste und 7 generated Aufgaben nachgerechnet, alle richtig; keine Kollision zwischen `mistake` und Antwort im ganzen Wertebereich; Plättchenzahlen der SVGs stimmen mit alt-Texten; keine Tausenderpunkte, keine Brüche, kein Vorgriff auf #385/#389/#392/#393/#401; keine externen Links; Selbsteinschätzung ohne Seitenbezug lösbar. Stichprobe auf wörtliche Übernahmen: zwei Websuchen (Potenzdefinition, Outfit-Aufgabe), nichts Wörtliches gefunden; Zahlenfolge-Definition, Satz „egal was du zuerst gewählt hast“ und Aufgabentexte nicht per Suche geprüft. Umgesetzt (rein mechanisch, **nach der Prüfung geändert, nicht erneut geprüft**): `$n$` im Fragetext von `term-waehlen`; irreführende ids `verdoppeln` → `gleicher-abstand`, `million-potenz` → `billion-potenz` (auch in `selfAssessment`); „mit a · b“ → „mit der Rechnung Zahl mal Zahl“. Nicht umgesetzt, bewusst als offene Verbesserung: Term selbst eingeben statt wählen (Runtime hat dafür keinen Typ ohne Komponente), Beispiel für ein Muster ohne konstanten Abstand (1, 4, 9, 16), Aufgabe „Zahl → k · 10^e“ (`30 000 = 3 · 10^?`; neue Aufgaben wären ungeprüft), Variablen in Optionen kursiv (Runtime-Test ohne JavaScript bricht bei `$…$` in Optionen und `matching`: Fund).

**Recap nach regeln.md §7 (Auftrag des Menschen über den Orchestrator): Überarbeitung und Prüfung.** Vorher: Recap zitierte nur die „Ich kann …“-Sätze der Karte. Jetzt: ein Abschnitt je Baustein (`natuerliche-zahlen`, `grundrechenarten-rechengesetze`), Begriffe als `definition` (Ziffer, Stellenwert, Stellenwerttafel, Vorrangregel, Kommutativgesetz, Assoziativgesetz, Distributivgesetz; kommen ins Glossar), Summe/Summand und Produkt/Faktor im Text fett, Beispielkasten, „Kannst du das?“ mit zwei Aufgaben je Baustein, Lösung samt Fehlerhinweisen, Kartenlink, Checkliste. Anzahl überarbeiteter Recaps: 1 (das Kapitel hat nur einen; kein weiteres Kapitel braucht einen). Der Block `recap` erlaubt keine Aufgaben, daher Selbsttests als `note`-Boxen mit aufgedeckter Lösung (Fund fürs Werkzeug: keine Rückmeldung nach Antwort, nicht einklappbar). Lernenden-Prüfer (nur Recap): Kann ich beurteilen, ob ich die Voraussetzung erfülle? Stellenwert: ja, Begriffe klar; Vorrang und Gesetze: eher ja. Befunde und Umsetzung: Lösung sofort sichtbar (nicht lösbar ohne Einklappen, Hinweis „erst im Kopf rechnen“ im Kopf), Distributivgesetz und Klammern fehlten in den Aufgaben → Aufgabe 1 mit Klammer, Aufgabe 2 mit 6 · 102; „Faktor/Summand“ unerklärt → Summe/Produkt eingeführt; Checkliste zu abstrakt → mit Beispielen; Tabelle bei 360 px abgeschnitten → Kürzel im Kopf. Fachlicher Prüfer (nur neue Texte): Rechnungen richtig; Befunde: Kommutativgesetz ohne Subtraktion/Division, Assoziativgesetz unklar, Vorrangregel ohne „links nach rechts“ und Zeichen, Hinweistext „links nach rechts“ irreführend, „zehnmal so viel“ und ZT/HT/M fehlten, Trick im Aufgabentext → alle umgesetzt. Zweiter fachlicher Lauf über den überarbeiteten Recap: 19 Rechnungen und Hinweise richtig, keine Schreibweise-Abweichung; zwei optionale Wortvorschläge („Zehnerpotenzen“ im Kopf durch „Zehner, Hunderter, Tausender“, „malgenommen“ → „multipliziert“) bewusst nicht umgesetzt, damit der geprüfte Stand bleibt. Lernenden-Prüfer lief nur auf der Fassung davor, nicht erneut auf der überarbeiteten; offen. `lernapps check` grün (Hinweise zu Textmenge und Wiederholung bleiben: Recap-Seiten sind Text, die Wiederholung „Nicht sicher? Lies den Baustein“ verlangt §7).

**Recap, Selbsttest als Komponente `Kurztest` (Vorlage des Orchestrators):** Die Selbsttests sind jetzt `Kurztest`-Blöcke (vier im Stellenwert-Teil und im Vorrang-Teil: 2 + 2, je mit Rückmeldung samt Grund, Tastatur, `nojs`-Text mit Lösung), `src/components/Kurztest.{ts,vue,test.ts}` unverändert aus `/tmp/epic/docs/mathe-epic/components/`; `lernapps check` grün. Lernenden-Prüfer (nur diese Recap-Seite, 360/1280 px, Tastatur): Beide Voraussetzungen „ja“ (Vorrang „schwächer“: Kommutativ-/Assoziativgesetz und „links nach rechts“ erklärt, nicht getestet; keine Klammer-Testfrage); Rückmeldungen mit Grund, kein Vorabverrat, kein Querscrollen. Ein Wort im Kopf geändert (Zehnerpotenzen → Zehner, Hunderter, Tausender), **danach nicht erneut geprüft**. Offen: Klammer-Testfrage, Test zu Komm./Assoziativgesetz (je Baustein höchstens zwei Kurztests, regeln.md §7).

**Kurztest bei 360 px:** `Kurztest.vue` durch die korrigierte Vorlage ersetzt (`.kurztest` mit `min-width: 0; max-width: 100%; box-sizing: border-box; overflow-wrap: anywhere`, `.kurztest-option` mit `padding: 0.6rem 0; line-height: 1.4`); Script, `.ts` und Test unverändert. `lernapps check` grün (nur Hinweise), kein Überstand bei 360 px in Playwright.

**Durchgang zu regeln.md §9 (Rückmeldungen des Menschen):** (1) „Was du hier lernst“: keine Seite hat eine Einstiegsüberschrift „Was du hier kannst“ (Abschlussabschnitt „Das kannst du jetzt“ ist kein Einstieg), nichts geändert. (2) Nur auf Sichtbares verweisen: Verweise geprüft (Pfeil im Bündelbild vorhanden), nichts zu ändern. (3) Bündeln als Vorgang: Bild `buendeln.svg` um einen gestrichelten Rahmen um die zehn Plättchen ergänzt, Bildunterschrift und alt-Text benennen Rahmen, Vorgang und Ergebnis; nur der Schritt E → Z ist gezeichnet (Prüfer: schwach, mehrere Spalten fehlen; so gelassen). (4) Nicht zu leichte Selbsttests: Kurztests im Recap schwerer (Wert der 7 in 40 705, 5 Zehntausender mit Nullen, 20 − 3 · 4 + 2 statt 5 + 3 · 4). (5) Modell vor der ersten Aufgabe: `quadrat-kubik` und `tabelle` nennen „Anzahl der Reihen/Zeilen mal Anzahl der Plättchen je Reihe/Zeile“ im Einstieg. (6) Keine `links:` an Aufgaben: alle 27 entfernt, Build und `lernapps check` bestehen ohne. Geänderte Seiten: 7 (6 wegen der Links, davon `quadrat-kubik`, `tabelle`, `zehnerpotenzen` und `recap` auch inhaltlich). Lernenden-Prüfer über diese vier inhaltlich geänderten Seiten: keine Verweise auf Unsichtbares, Bündeln als Vorgang erkannt, Kurztests passend, Modell erklärt, keine Aufgabenlinks; Befund „tabelle: Rechenregel fehlte im Einstieg“ umgesetzt (Satz danach **nicht erneut geprüft**). Bekannt, Runtime: Falsch-Rückmeldung „Lies dazu noch einmal den Text“ bei Aufgaben ohne passenden `mistake`; Titel „Das brauchst du hier“ steht auf dem Recap doppelt.

**Rückmeldung des Menschen im Feedback-Modus der Vorschau (2 Notizen):** (1) Seite `folgen`, Ordnungsaufgabe `folge-sechs`: „Das übt nur, ob man Zahlen der Größe nach ordnen kann, keine Folgen“. Berechtigt; ersetzt durch die Zahlaufgabe `luecke-in-folge` (fehlendes Glied 7, 13, __, 25, 31: Abstand erkennen, Glied einsetzen, mit Rückmeldung zu 18 und 20). Der Baustein bleibt auf `folgen` mit vier Übungen geübt, ohne Ordnungsaufgabe; der Rechenweg 13 − 7 = 6 wurde von mir nachgerechnet (7, 13, 19, 25, 31), **von keinem Prüfer geprüft**. (2) Seite `regel`: Lob für die Einführung des Begriffs „Term“, keine Änderung.

**Offen (nicht geprüft):** Bildschirmleser; Hessischer Lehrplan; Prüfung der letzten Änderungen durch einen neuen Lernenden-Durchgang (nur `lernapps check` und Build liefen); das Plattformverhalten bei `{{answer}}` mit Tausenderpunkt ist ein Fund, kein behobener Fehler.

## Code

<!--
- Build the app, locally on `work`, on your own. After each task: `plan done`, then one commit with the work and this
  plan. The hooks check each commit; a failing check is fixed from its message, as skill `lernapps-cli` says.
- What you cannot decide: choose, write it under "Key decisions" with "(guess)", go on.
- The creator asks for a change: say your reading in one sentence first, then change every place it holds for
  (`feedback-applied-everywhere`).
-->

### Tasks

- [x] Load skill `lernapps-cli`. Create the app as its section "Create" says:
      `npx --no -- lernapps create --archetype explainer`.
- [x] Fill the content guide `.agents/skills/app-content/SKILL.md` from "Notes" and "Content method": every heading,
      no "FILL IN" left. Commit it before any content.
- [x] Load skill `lernapps-explainer`.
- [x] Load skill `lernapps-content-questions`. Read whole, with your file tool:
      `.agents/skills/lernapps-explainer/references/blocks.md` and
      `.agents/skills/lernapps-explainer/references/exercises.md`. A foreign language: also
      `references/language-tasks.md` in the same folder. A component in the plan: also `references/components.md`.
- [x] Decide whether the app needs `scope`, as "`scope`" in
      `.agents/skills/lernapps-explainer/references/structure.md` says. Write the choice under "Key decisions".
- [x] Musterseite muster/quadrat-kubik komplett: Einstieg, Plättchenbild-SVG mit alt, Beispiel, Aufgaben mit Rückmeldung und mistakes; Recap-Seite und Kapitel-Gerüst, app.yaml mit strand mathematik/arithmetik
<!-- tasks: pattern (1 added): the one page or screen that is the pattern for the others -->
- [x] **Checkpoint:** the pattern page. Load skill `lernapps-learner-check` and do its learner check on the page. Fix
      what it finds. Then show the creator the page and ask whether the others may follow it. Stop and wait. A
      change: change the pattern first.
      Creator: Orchestrator (in Vertretung): Musterseite angenommen, übrige Seiten nach diesem Muster; Stellenwerttafel als table mit E, Z, H, T
- [x] Seiten muster/folgen und muster/regel (muster-zahlenfolgen), Platzhalter nur in Worten, kein Termumformen
- [x] Seite muster/zehnerpotenzen (potenzen): Stellenwerttafel, Zehnerpotenzen bis 10⁹
- [x] Seiten muster/tabelle und muster/baum (zaehlprinzip): Plättchenfeld, Tabelle, Baumdiagramm, Kapitelrückblick
- [x] Zwei Prüfer starten (Lernenden-Prüfer, Fachlicher Prüfer), Befunde in den Plan unter Review, Befunde beheben
<!-- tasks: pages (4 added): the other pages or screens, after the pattern -->
- [x] Update the content guide so that it describes the app as built (`app-content-matches`).
- [x] Run `npx --no -- lernapps check` until it passes.
- [x] Look at every screen and state, at 360 px and on a desktop, as "Look at the app" of skill `lernapps-cli` says.
      Compare each with its sketch.
- [x] Do the whole-app check of skill `lernapps-learner-check`. Fix what it finds and write under "Notes" what you
      fixed.

## Commit

<!--
- Put the app on GitHub, publish it with the creator's yes, then list it. A push to `main` publishes.
- Open the pull requests (to `main`, to the catalog) without asking: they publish nothing.
- The creator asked to stop before publishing (a trial): stop here and say so.
-->

### Tasks

- [x] Load skill `lernapps-explainer-self-assessment`. Add the self-assessment as it says, or write under "Key
      decisions" why the app has none. Commit.
- [x] Load skill `lernapps-github`. Set up the repository and Pages as it says. Ask for the repository's name and
      every click only the creator can make, in one message.
- [x] Push `work`, open the preview pull request and see its checks to green, as skill `lernapps-github` says.
- [ ] **Checkpoint:** publish. Show what the app does and the preview link from the comment "Vorschau der App". Ask
      whether it may go online. Stop and wait for the yes.
- [ ] Load skill `lernapps-commit`. Publish as skill `lernapps-github` says: `work` into `main` as one squash commit,
      the run of `Pages` watched to its end.
- [ ] Open the address the job `deploy` printed and confirm that the app shows. Never use a derived address.
- [ ] Load skill `lernapps-listing`. Write the entry under "Entry draft" as it says, with the creator's answer to
      "Finding the app".
- [ ] Fill the retrospective.
- [ ] Commit this plan on `main` and push it: the listing check and the review read it there.
- [ ] **Checkpoint:** list. Open the listing pull request as skill `lernapps-listing` says, without asking first: the
      pull request is the review. See it to "bestanden", then show the creator the pull request and its result.
- [ ] If the plan changed since its last push, commit it on `main` and push again.

### Entry draft

<!-- YAML valid against the entry schema the listing skill names. Only known values, never invented. -->

```yaml
```

## Retrospective

<!-- At the end of Commit, before the listing pull request. Facts, short, no names. Read by review and evals. -->

### Phases reached

<!-- Last phase completed, checkpoints passed. E.g. "commit; confirmed, published". -->

Explore, Plan, Code erreicht; in Commit: Repository, Vorschau-PR #1 (alle Checks grün: app, preview; deploy übersprungen, wie bei PR). Checkpoints bestanden: Recherche, Plan, Musterseite (jeweils vom Orchestrator in Vertretung des Menschen beantwortet). Offen: Veröffentlichen, Liste (nach Freigabe).

### Creator turns after the plan

<!-- Number of creator messages after the confirmation, topic of each. Target: at most 3. -->

Mensch: 0 direkt; über den Orchestrator kam danach der Auftrag, die Recaps nach regeln.md §7 zu überarbeiten (Rückmeldung der Vorschau-Prüfung). Orchestrator in Vertretung nach der Planbestätigung: 4 Nachrichten (Konventionen der Stellenwerttafel; Antwort auf die Musterseite; Antwort zu Veröffentlichen mit erneutem fachlichem Prüflauf; Auftrag Recap). Zuvor: 2 Nachrichten (Konventionen der Stellenwerttafel aus #385 samt Regel „keine externen Links“, Antwort auf die Musterseite, …) und eine Regeländerung vor der Planbestätigung (Zahlenstrahl/Zahlengerade).

### Where I had to guess

<!-- Each gap in plan, skills, messages or answers, and your choice. "None" if none. -->

- Sprache nur Deutsch (Epic nennt nichts anderes).
- Keine Komponente (Stellenwerttafel als `table`): Plan sagte das, Orchestrator bestätigte nach Rückfrage.
- Kein `scope`; Selbsteinschätzung mit je zwei Aufgaben je Seite, drei Schritte.
- Interview durch den Issue-Text ersetzt (kein Gespräch möglich).
- Prozess: Ich habe fünf Plan-Aufgaben vor ihrer Erledigung abgehakt (Archetyp-Skills, Content-Research-Skill, Interview, Content-Methode, Zeigen); danach nachgeholt oder durch den Bericht erfüllt.
- Verwechslung bei Recap-ids: Plan nannte `mathematik/arithmetik/<id>`, richtig ist `mathematik/<id>`; vom Build gemeldet.
- Recap: `recap` erlaubt keine Aufgaben; Selbsttests als `note`-Boxen mit aufgedeckter Lösung statt Rückmeldung nach Antwort (guess, dem Orchestrator gemeldet).
- Beim Lernenden-Check habe ich Befunde zur Runtime nicht lokal umgangen (Symbol-Knopf, Standardmeldung bei Fehlern von Wahr/Falsch und Ordnen, Tausenderpunkt in `{{answer}}` der `steps`).
