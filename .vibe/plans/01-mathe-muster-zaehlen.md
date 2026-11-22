---
# Read by the hooks, the review, the evals. Schema: @lernapps/tooling/guidance/plan-front-matter.v1.schema.json
# Written by `lernapps plan` and the hooks. Never change a key or a value by hand.
# Archetype, null until chosen in Explore. Allowed values: explainer, interactive, quiz.
archetype: explainer
# Current phase. Allowed values: explore, plan, code, commit.
phase: code
# prePushFailures: failed pre-push runs, written by the hook.
prePushFailures: 0
# failedChecks: failed rules and runs, written by lernapps check and the hooks.
failedChecks: { checks-pass: 2 }
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
- [ ] **Checkpoint:** the pattern page. Load skill `lernapps-learner-check` and do its learner check on the page. Fix
      what it finds. Then show the creator the page and ask whether the others may follow it. Stop and wait. A
      change: change the pattern first.
- [ ] Seiten muster/folgen und muster/regel (muster-zahlenfolgen), Platzhalter nur in Worten, kein Termumformen
- [ ] Seite muster/zehnerpotenzen (potenzen): Stellenwerttafel, Zehnerpotenzen bis 10⁹
- [ ] Seiten muster/tabelle und muster/baum (zaehlprinzip): Plättchenfeld, Tabelle, Baumdiagramm, Kapitelrückblick
- [ ] Zwei Prüfer starten (Lernenden-Prüfer, Fachlicher Prüfer), Befunde in den Plan unter Review, Befunde beheben
<!-- tasks: pages (4 added): the other pages or screens, after the pattern -->
- [ ] Update the content guide so that it describes the app as built (`app-content-matches`).
- [ ] Run `npx --no -- lernapps check` until it passes.
- [ ] Look at every screen and state, at 360 px and on a desktop, as "Look at the app" of skill `lernapps-cli` says.
      Compare each with its sketch.
- [ ] Do the whole-app check of skill `lernapps-learner-check`. Fix what it finds and write under "Notes" what you
      fixed.

## Commit

<!--
- Put the app on GitHub, publish it with the creator's yes, then list it. A push to `main` publishes.
- Open the pull requests (to `main`, to the catalog) without asking: they publish nothing.
- The creator asked to stop before publishing (a trial): stop here and say so.
-->

### Tasks

- [ ] Load skill `lernapps-explainer-self-assessment`. Add the self-assessment as it says, or write under "Key
      decisions" why the app has none. Commit.
- [ ] Load skill `lernapps-github`. Set up the repository and Pages as it says. Ask for the repository's name and
      every click only the creator can make, in one message.
- [ ] Push `work`, open the preview pull request and see its checks to green, as skill `lernapps-github` says.
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

### Creator turns after the plan

<!-- Number of creator messages after the confirmation, topic of each. Target: at most 3. -->

### Where I had to guess

<!-- Each gap in plan, skills, messages or answers, and your choice. "None" if none. -->
