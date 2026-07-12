# Electronic Devices & Circuits — Subtopic-wise Reference Map
*(IOE / TU — BE Year I Part II syllabus)*

## The two books you need

| Code | Book | Why |
|---|---|---|
| **SS** | Sedra & Smith, *Microelectronic Circuits* (6th or 7th ed.) | Your syllabus headings are taken almost word-for-word from this book's table of contents (originally the 4th ed.). This is the primary text. |
| **B&N** | Boylestad & Nashelsky, *Electronic Devices and Circuit Theory* (11th ed.) | Easier, more numerical/practical. Best for load lines, biasing, JFET, power amps, and voltage regulators. |

Supporting books used for a few specific subtopics: **Floyd**, *Electronic Devices* (special diodes); **Gayakwad**, *Op-Amps and Linear Integrated Circuits* (555, IC regulators); **Gray–Hurst–Lewis–Meyer**, *Analysis and Design of Analog ICs* (bandgap reference only).

**Edition note (SS):** section numbers below are for the **7th edition**. For the 6th edition: Ch 7 → the amplifier sections inside Ch 5 (MOS) & Ch 6 (BJT); Ch 8 → Ch 7; Ch 9 → Ch 8; Ch 12 → Ch 11; Ch 17 → Ch 16; Ch 18 → Ch 17. In *any* edition, just match the **section title** — the syllabus uses the book's own headings.

## The three video anchors (verified links)

| Channel | Link | Best for |
|---|---|---|
| **Neso Academy — Analog Electronics** (chapter-wise course page) | https://www.nesoacademy.org/ee/04-analog-electronics · full lecture list: https://www.classcentral.com/course/youtube-analog-electronics-48206 · channel playlists: https://www.youtube.com/c/nesoacademy/playlists | Units 1, 2, 4 — follows Boylestad chapter-by-chapter (BJT → DC biasing → BJT AC analysis → FET → FET biasing → power amps) |
| **ALL ABOUT ELECTRONICS (AAE)** | Channel: https://www.youtube.com/channel/UCBkOVp1Cqz4MR0LYR8vKpZg · BJT playlist: https://www.youtube.com/playlist?list=PLwjK_iyK4LLDoFG8FeiKAr3IStRkPSxqq | Every unit — short topic videos (oscillators, 555, op-amp circuits, power amps, regulators). Browse the channel's **Playlists** tab for the MOSFET, Op-Amp, Oscillator, Power Amplifier and Voltage Regulator playlists. |
| **Razavi Electronics 1 & 2** (Prof. Behzad Razavi, UCLA) | Electronics 1 playlist: https://www.youtube.com/playlist?list=PLacwBqL-3HkwbaTZWbxgnb-ZKfaG16lXL · Electronics 2 starts here: https://www.youtube.com/watch?v=pK2elUcXWzs | Deep intuition — small-signal models, CE/CS amplifiers, current mirrors, differential pairs (Electronics 2) |

> Where a link isn't given below, the video title in quotes is the exact phrase to search on YouTube (mostly on the AAE or Neso channel) — titles I couldn't verify a URL for are given as search phrases rather than guessed links.

---

## Unit 1 — Bipolar Junction Transistor (9 hrs)

| # | Subtopic | Book (1:1) | Video (1:1) |
|---|---|---|---|
| 1.1 | npn transistor in active mode | **SS §6.1** (Device Structure and Physical Operation); B&N Ch 3 (§3.2–3.4) | AAE — "Introduction to Bipolar Junction Transistor (BJT)": https://www.youtube.com/watch?v=-VwPSDQmdjM · Razavi E1 (bipolar lectures in playlist) · Neso Ch 4 |
| 1.2 | Graphical representation of characteristics | **SS §6.2** (Current–Voltage Characteristics, incl. Early effect); B&N §3.5–3.6 (CB/CE characteristics) | AAE BJT playlist — "BJT Characteristics (input/output)" · Neso — "Transistor Configurations", "Output Characteristics" |
| 1.3 | Transistor circuits at DC | **SS §6.3** (BJT Circuits at DC — the 10+ worked examples here are exam gold); B&N Ch 4 | Neso Ch 5 (DC Biasing of Transistors, solved problems) · AAE — "BJT DC analysis solved examples" |
| 1.4 | Graphical DC load line analysis | **B&N §4.2–4.3** (Operating Point, Fixed-Bias with load line) — clearest treatment; SS §7.1 (load-line view of amplification) | AAE — "DC Load Line and Q Point" · Neso — "Load Line Analysis" (Ch 5) |
| 1.5 | Transistor as an amplifier (rπ, re, gm) | **SS §7.1–7.2** (Basic Principles; Small-Signal Operation — gm, rπ, re defined here); B&N §5.2–5.4 (re model) | Neso Ch 6 — "re Transistor Model (Part 1, 2)" · Razavi E1 — bipolar amplifier lectures |
| 1.6 | Biasing BJT for discrete-circuit design | **SS §7.4** (Biasing — voltage-divider, two-supply, collector-feedback); B&N Ch 4 (§4.3–4.7) | AAE — "Transistor Biasing" series (fixed bias / collector feedback / voltage divider) · Neso Ch 5 |
| 1.7 | Small-signal models (hybrid-π and T) | **SS §7.2** (subsections on the hybrid-π and T models); B&N §5.5 + hybrid-π section | Neso — "Hybrid-π Model" + "Hybrid-π Model (Solved Problem)" · Razavi E1 |
| 1.8 | Single-stage configs (C-B, C-E, C-C) | **SS §7.3** (The Basic Configurations — CE, CE with RE, CB, emitter follower); B&N Ch 5 (§5.6 onward) | AAE — "Common Emitter Amplifier", "Common Base Amplifier", "Emitter Follower" · Razavi E1 |
| 1.9 | Small-signal analysis of amplifier | **SS §7.3 + §7.5** (Discrete-Circuit Amplifiers — full worked analyses); B&N Ch 5 solved problems | Neso Ch 6 — "re Model (Voltage-Divider Bias)", "Two-Port Systems Approach" · AAE solved-example videos |
| 1.10 | Transistor as a switch — cutoff & saturation | **SS §6.2** (saturation-mode subsection) + worked switch examples in §6.3; B&N Ch 4 — "Transistor Switching Networks" section | AAE — "Transistor as a Switch" |
| 1.11 | Ebers-Moll model | **SS 4th/5th ed.**, BJT chapter, final section — "A General Large-Signal Model for the BJT: The Ebers-Moll Model" (this heading *is* your syllabus line; newer editions compress it into the saturation-mode discussion) | Search "Ebers Moll model of BJT" — good versions by GATE Academy and Engineering Funda |

## Unit 2 — Field-Effect Transistor (10 hrs)

| # | Subtopic | Book (1:1) | Video (1:1) |
|---|---|---|---|
| 2.1 | JFET structure & physical operation | **B&N Ch 6 (§6.2–6.5)** — best JFET coverage (SS 6th/7th moved JFETs to an appendix/online) | Neso Ch 7 — "Construction and Working of JFET", "Pinch-off Voltage" · AAE — "JFET Explained" |
| 2.2 | Enhancement MOSFET structure & operation | **SS §5.1** (Device Structure and Physical Operation); B&N Ch 6 — Enhancement-Type MOSFET section | Razavi E1 — "Lec 29, Intro. to MOSFETs": https://www.youtube.com/watch?v=dlOlxAcfBo4 · AAE — "MOSFET Explained" |
| 2.3 | I–V characteristics of E-MOSFET | **SS §5.2** (Current–Voltage Characteristics — triode/saturation, channel-length modulation); B&N Ch 6 | Razavi E1 — "Lec 30, MOS Characteristics": https://www.youtube.com/watch?v=0OH9d72ZX7s · AAE — "MOSFET characteristics" |
| 2.4 | Depletion-type MOSFET | **B&N Ch 6** — Depletion-Type MOSFET section (SS covers it briefly in Ch 5) | AAE — "Depletion type MOSFET" · Neso Ch 7 |
| 2.5 | Biasing in MOS amplifier circuits | **SS §7.4** (MOS biasing subsections); B&N Ch 7 (FET Biasing) | Neso Ch 8 (Biasing of FET) · AAE — "MOSFET biasing" |
| 2.6 | MOSFET circuits at DC | **SS §5.3** (MOSFET Circuits at DC — worked examples); B&N Ch 7 problems | AAE — "MOSFET DC analysis solved problems" · Razavi E1 MOS lectures |
| 2.7 | MOSFET as amplifier (Common Source) | **SS §7.2 (MOS small-signal) + §7.3** (CS configuration); B&N Ch 8 (FET Amplifiers) | Razavi E1 — CS amplifier lectures (in playlist above) · AAE — "Common Source Amplifier" |
| 2.8 | MOSFET & CMOS as logic circuits | **SS Ch 14** (CMOS Digital Logic Circuits — CMOS inverter, NAND/NOR gates) | AAE — "CMOS Inverter" · Neso — Digital Electronics playlist, CMOS lectures (channel playlists page above) |

## Unit 3 — Op-Amp Circuits and Oscillators (10 hrs)

| # | Subtopic | Book (1:1) | Video (1:1) |
|---|---|---|---|
| 3.1 | Principles of sinusoidal oscillators | **SS §18.1** (Basic Principles — loop gain, Barkhausen criterion, amplitude control); B&N Ch 14 | AAE — "Oscillators: introduction / Barkhausen criterion" · reading: https://www.electronics-tutorials.ws/category/oscillator |
| 3.2 | Op-amp square/triangular & RC oscillators | **SS §18.2** (Op-Amp RC Oscillators — Wien bridge, phase shift) + §18.5-area sections on square/triangular generation (astable, bistable + integrator); B&N Ch 14 (phase-shift, Wien bridge) | AAE — "Wien Bridge Oscillator": https://www.youtube.com/watch?v=gbUXbaxvX94 · AAE — "RC Phase Shift Oscillator", "Triangular Wave Generator using Op-Amp" |
| 3.3 | LC and crystal oscillators | **SS §18.3** (LC and Crystal Oscillators — Colpitts, Hartley, crystal); B&N Ch 14 (tuned oscillators, crystal) | AAE — "Colpitts Oscillator", "Hartley Oscillator", "Crystal Oscillator" · reading: https://www.electronics-tutorials.ws/oscillator/colpitts.html |
| 3.4 | Integrated-circuit timers | **SS Ch 18** — "Integrated-Circuit Timers" section (555 monostable & astable); B&N Ch 13 (Linear-Digital ICs — 555); Gayakwad | AAE — "555 Timer" videos (astable / monostable) · reading: https://www.electronics-tutorials.ws/waveforms/555_timer.html and https://www.electronics-tutorials.ws/waveforms/555_oscillator.html |
| 3.5 | Precision rectifier circuits | **SS Ch 18** — "Precision Rectifier Circuits" section (superdiode, precision half/full-wave); Gayakwad | AAE — "Precision Rectifier using Op-Amp (Super diode)" |
| 3.6 | Bias circuits for IC design | **SS Ch 8** — "IC Biasing — Current Sources, Current Mirrors, and Current-Steering Circuits" section | AAE — "Current Mirror Circuit Explained" · Razavi Electronics 2, Lec 1 (current sources): https://www.youtube.com/watch?v=pK2elUcXWzs |
| 3.7 | Widlar current source | **SS Ch 8** — "Current-Mirror Circuits with Improved Performance" section (Widlar, Wilson, cascode) | Search "Widlar current source" — solid derivations by GATE Academy / Engineering Funda |
| 3.8 | The differential amplifier | **SS §9.1–9.2** (MOS and BJT differential pairs); B&N Ch 12-area intro in op-amp chapter | AAE — "Differential Amplifier" series (BJT diff amp, half-circuit analysis) · Razavi Electronics 2 — differential pair lectures |
| 3.9 | Active loads | **SS Ch 9** — "The Differential Amplifier with a Current-Mirror (Active) Load" section | Razavi Electronics 2 — "differential pair with active load" lectures · AAE current-mirror-load video |
| 3.10 | Output stages | **SS Ch 12 intro** (overview — full treatment is Unit 4) | AAE — Power Amplifier playlist intro video (channel Playlists tab) |

## Unit 4 — Output Stages and Power Amplifiers (10 hrs)

| # | Subtopic | Book (1:1) | Video (1:1) |
|---|---|---|---|
| 4.1 | Classification of output stages | **SS §12.1** (Classification — A/B/AB/C by conduction angle); B&N §12.1 | AAE — "Power Amplifier introduction & classes" · Neso Ch 12 |
| 4.2 | Class A output stage | **SS §12.2** (emitter-follower class A; power & efficiency derivation); B&N §12.2–12.3 (series-fed & transformer-coupled class A) | AAE — "Class A Power Amplifier" · Neso Ch 12 |
| 4.3 | Class B output stage | **SS §12.3** (push-pull, crossover distortion, η = 78.5% derivation); B&N — Class-B sections of Ch 12 | AAE — "Class B Power Amplifier / Push-Pull" · Neso Ch 12 |
| 4.4 | Class AB output stage | **SS §12.4** (Class AB Output Stage); B&N Ch 12 (class AB discussion) | AAE — "Class AB Power Amplifier" |
| 4.5 | Biasing of class AB | **SS §12.5** (Biasing the Class AB Circuit — diode biasing, VBE multiplier) | AAE — "VBE multiplier / Class AB biasing" (in power-amp playlist) |
| 4.6 | Power BJTs | **SS Ch 12** — "Power BJTs" section (junction temperature, thermal resistance, heat sinks, SOA); B&N — "Power Transistor Heat Sinking" section | Search "power transistor thermal resistance heat sink" (Engineering Funda has a clear one) |
| 4.7 | Transformer-coupled push-pull stage | **B&N Ch 12** — transformer-coupled push-pull circuit section (better than SS here) | AAE — "Push Pull Amplifier" · Neso Ch 12 |
| 4.8 | Tuned amplifiers | **SS Ch 17** (Filters and Tuned Amplifiers) — final "Tuned Amplifiers" section (single/synchronous/stagger tuning) | Search "tuned amplifier single tuned double tuned" — Engineering Funda playlist covers all three types |

## Unit 5 — Power Supplies, Breakdown Diodes, Voltage Reference (6 hrs)

| # | Subtopic | Book (1:1) | Video (1:1) |
|---|---|---|---|
| 5.1 | Unregulated power supply | **SS §4.5** (Rectifier Circuits — half/full-wave, bridge, capacitor filter, ripple); B&N Ch 15 (§15.2–15.3, filters) | AAE — "Half Wave / Full Wave Bridge Rectifier (with capacitor filter)" |
| 5.2 | Zener regulated power supply | **SS §4.4** (Operation in the Reverse Breakdown Region — Zener Diodes, shunt regulator design example); B&N Ch 2 Zener sections | AAE — "Zener Diode as Voltage Regulator" |
| 5.3 | Zener diodes, bandgap reference, constant-current diodes | Zener: **SS §4.4**. Bandgap: **Gray–Hurst–Lewis–Meyer Ch 4** (voltage references) or Razavi *Design of Analog CMOS ICs*, "Bandgap References" chapter. Constant-current diodes: **Floyd, Electronic Devices** — "Special-Purpose Diodes" chapter | AAE — "Zener Diode Explained" · search "bandgap voltage reference explained" · search "current regulator diode" |
| 5.4 | Transistor shunt/series voltage regulator | **B&N Ch 15** — "Discrete Transistor Voltage Regulation" section (series & shunt circuits, worked examples) | Search "transistor series voltage regulator" / "shunt voltage regulator" (Engineering Funda covers both) |
| 5.5 | Improving regulation with feedback | **B&N Ch 15** — series regulator with error amplifier / op-amp feedback (same section as 5.4) | Search "series voltage regulator with feedback op-amp error amplifier" |
| 5.6 | IC voltage regulator | **B&N Ch 15** — "IC Voltage Regulators" section (78xx/79xx, LM317); Gayakwad (723, three-terminal regulators) | AAE — "7805 Voltage Regulator" / "LM317" videos |

---

## How to actually use this

1. **Read SS by section title, not number.** Your syllabus lines are SS headings — open the table of contents of whatever edition/PDF you have and match the words.
2. **Watch before reading** for Units 1–2 (Neso/AAE first, then SS examples), and **read before watching** for Unit 3.6–3.10 (current mirrors and diff amps are hard to follow on video cold).
3. **SS worked examples §6.3 and §5.3** (BJT and MOSFET circuits at DC) are the most exam-relevant pages in the whole book for this course.
4. For IOE-specific notes, insight into past questions, and old exam solutions, students commonly use **ioenotes.edu.np** (search "electronic devices and circuits IOE notes").
