# EDC — Chapter 1: The Bipolar Junction Transistor (BJT)
**Course:** Electronic Devices and Circuit (ENEX 151 / EX 151) · Tribhuvan University, IOE · BE (BEI, BCT) I/II
**Sources synthesized:** Sedra–Smith (Microelectronic Circuits), Boylestad–Nashelsky (Electronic Devices and Circuit Theory), Floyd (Electronic Devices), Millman–Halkias (Integrated Electronics), Bell (Electronic Devices and Circuits) + your 4 PYQ papers (2081 Ashwin, 2082 Baishakh, 2082 Bhadra, 2083 Baishakh).

---

## Chapter Overview — Read This First

**What this chapter is about:** The BJT is a three-terminal semiconductor device in which a small base current (or base–emitter voltage) controls a much larger collector current. Everything in this chapter builds one story:

> **Physics of the device → its I–V characteristics → setting a DC operating point (biasing) → replacing the transistor with a small-signal model → analyzing the three amplifier configurations → using the BJT as a switch → the complete large-signal (Ebers–Moll) model.**

### 📊 PYQ Frequency Analysis (from your 4 papers)

BJT contributed **exactly 13 marks out of 60 in every one of the four papers** — it is the single most predictable chapter on this paper.

| Topic | 2081 Ashwin | 2082 Baishakh | 2082 Bhadra | 2083 Baishakh | Verdict |
|---|---|---|---|---|---|
| β-independent bias **design** (voltage divider) | ✔ [4] CE | ✔ [4] | ✔ [1+5] | ✔ [1+5] CC | 🔥 **4/4 years — GUARANTEED** |
| Small-signal analysis of one configuration (Zi, Zo, Av) | ✔ CC [1+4] | ✔ CE numerical [5] | ✔ CE [2+5] | ✔ CB [2+5] | 🔥 **4/4 years — GUARANTEED** |
| Role of coupling / bypass capacitors | – | – | ✔ coupling [2] | ✔ bypass [2] | 🔥 2/4 — attached to the amplifier question |
| BJT as a switch | – | ✔ [4] | – | – | 🟡 1/4 |
| Derive transconductance g_m | ✔ [4] | – | – | – | 🟡 1/4 |
| Why BJT is bipolar / FET unipolar | – | – | – | ✔ [1] | 🟡 1/4 |
| Load line, DC analysis, characteristics | (embedded inside design/numerical questions) | | | | 🟡 foundational |
| Ebers–Moll model | never asked | | | | 🟢 low, but on syllabus |

**Strategic conclusion:**
1. 🔥 You **must** be able to *design* a voltage-divider (β-independent) bias circuit for **any** configuration (CE, CC) with any given V_CC, I_C/I_E, β — this has appeared **every single year**.
2. 🔥 You **must** be able to draw the small-signal equivalent and *derive* Z_i, Z_o, A_v for **all three configurations** — the paper rotates the configuration each year (CE → CC → CE → CB). After CB in 2083, **CE and CC are both live candidates**.
3. 🟡 Prepare the 4-mark "side" theory: g_m derivation, BJT as switch, capacitor roles, bipolar-vs-unipolar.

---

## 1.1 Review of Operation of the npn Transistor in the Active Mode

### A. Intuition — what the device *is*

A BJT is two pn junctions built back-to-back sharing a **very thin, lightly doped base**:

```
        npn structure                        Circuit symbols

   E          B          C              npn:        C            pnp:        C
 ┌─────┬──────────┬─────┐                           │                        │
 │ n++ │    p     │  n  │                        B ─┤                     B ─┤
 │(emit│  (base,  │(coll│                           │↘ (arrow OUT)           │↙ (arrow IN)
 │ ter)│very thin,│ect- │                           E                        E
 │     │ lightly  │ or) │
 └─────┴──doped)──┴─────┘              Arrow is always on the EMITTER and
   EBJ ↑        ↑ CBJ                  points in the direction of conventional
 (emitter-base  (collector-base       emitter current (n→p direction).
   junction)      junction)
```

Three structural facts explain everything:

1. **Emitter is heavily doped (n⁺⁺)** → it can inject a huge number of electrons.
2. **Base is extremely thin and lightly doped** → electrons injected into it almost all survive the trip across; very few recombine.
3. **Collector is large and moderately doped** → it collects the electrons and handles power dissipation.

**The transistor is NOT two independent diodes.** Two discrete diodes wired back-to-back give no transistor action, because the thin shared base is what lets carriers injected by one junction be collected by the other.

### B. The four modes of operation

The mode is set by how the two junctions are biased:

| Mode | EBJ (B–E) | CBJ (B–C) | Use |
|---|---|---|---|
| **Active** | Forward | Reverse | **Amplifier** ← this section |
| **Saturation** | Forward | Forward | Switch ON |
| **Cutoff** | Reverse | Reverse | Switch OFF |
| Reverse-active | Reverse | Forward | Rarely used (poor β) |

**Active-mode bias conditions (npn):** V_BE ≈ 0.7 V (forward), V_CB ≥ 0 — equivalently **V_CE > V_CE(sat) ≈ 0.2–0.3 V**. Memory aid for npn active mode: **V_C > V_B > V_E**.

### C. Physical operation in the active mode (formal explanation)

With the EBJ forward-biased and CBJ reverse-biased:

1. **Injection:** The forward-biased EBJ lowers the junction barrier; the heavily doped emitter injects a large flood of **electrons into the base** (and the base injects a few holes into the emitter — this hole current is small because the base is lightly doped).
2. **Diffusion across the base:** Injected electrons become minority carriers in the p-type base and **diffuse** toward the collector. Because the base is thin, the diffusion transit is short.
3. **Little recombination:** Only a small fraction of electrons recombine with holes in the base. The holes lost to recombination (plus the holes injected into the emitter) must be resupplied by the base terminal → this constitutes the **small base current I_B**.
4. **Collection:** Electrons reaching the reverse-biased CBJ are swept into the collector by the junction field → **large collector current I_C**, almost equal to the injected electron current.

> **Key insight:** I_C is controlled by V_BE (which sets injection), and is nearly independent of V_CB/V_CE — the collector merely *collects*. This is why the active-mode BJT behaves as a **voltage-controlled current source**.

**Why is the BJT called "bipolar"?** 🔥 *PYQ 2083 Q1(a) [1 mark]*

> Current conduction in a BJT involves **both types of charge carriers — electrons AND holes** (e.g., in an npn device, electrons carry the main emitter→collector current while holes constitute the base current and recombination). Hence **bi-polar**. In an FET, the channel current is carried by **only one carrier type** (electrons in n-channel, holes in p-channel), so the FET is **uni-polar**. A complete 1-mark answer states both halves.

### D. Current relations and equations

**Terminal current balance (KCL on the device):**

- **I_E = I_C + I_B**  — always true, all modes, both npn and pnp.

**Common-base current gain α:**

- **I_C = α·I_E**, where α = fraction of emitter current collected. Typically α = 0.98 – 0.998 (α < 1, very close to 1).

**Common-emitter current gain β (also h_FE):**

- **I_C = β·I_B**, where β = 50 – 300 typically (take β ≈ 100 unless told otherwise).

**α ↔ β conversion (derive once, remember forever):**

Start from I_E = I_C + I_B and I_C = αI_E:
I_C = α(I_C + I_B) → I_C(1 − α) = αI_B → I_C = [α/(1−α)]·I_B

- **β = α/(1 − α)**  and inverting: **α = β/(β + 1)**
- Also: **I_E = (β + 1)·I_B**

**Exponential collector current law (Sedra–Smith — the foundation of g_m):**

- **I_C = I_S · e^(V_BE / V_T)**

| Symbol | Meaning | Typical value |
|---|---|---|
| I_S | Saturation (scale) current, ∝ junction area | 10⁻¹² – 10⁻¹⁵ A |
| V_T | Thermal voltage = kT/q | ≈ 25–26 mV at room temperature |
| V_BE | Base–emitter voltage | ≈ 0.7 V in conduction |

Conditions: active mode only; ignores Early effect (add factor (1 + V_CE/V_A) to include it).

### E. Exam interpretation

Examiners test: (i) the bipolar/unipolar distinction, (ii) junction bias conditions per mode, (iii) fluency with α, β, I_E = I_C + I_B in numericals, (iv) the physical story (injection → diffusion → collection) as a descriptive answer.

### F. Common mistakes

- Writing β = α/(1 + α). **Wrong** — denominator is (1 − α).
- Saying I_C flows "because CBJ is forward biased." No — CBJ is **reverse** biased in active mode; it *collects*.
- Treating the BJT as two diodes when explaining transistor action.
- Forgetting that for **pnp** everything reverses: V_EB ≈ 0.7 V, currents flow opposite, memory aid V_E > V_B > V_C for active mode.

### 📌 Section Summary
- **Understand:** injection–diffusion–collection story; why thin base ⇒ β large; bipolar vs unipolar.
- **Memorize:** mode table; I_E = I_C + I_B; I_C = βI_B = αI_E; β = α/(1−α); I_C = I_S·e^(V_BE/V_T).
- **Draw:** npn structure with junctions; npn/pnp symbols with current directions.

### PYQ Check
- 2083 Baishakh Q1(a): *Why BJT is bipolar and FET is unipolar?* [1] — answered above.

> **Exam-ready when:** you can explain active-mode operation in 5–6 sentences with a structure sketch, and interconvert α, β, I_B, I_C, I_E instantly.

---

## 1.2 Review of Graphical Representation of Transistor Characteristics

### A. Input (base) characteristics — CE configuration

Plot of **I_B vs V_BE** (for fixed V_CE): looks exactly like a forward diode curve. Negligible I_B until V_BE ≈ 0.5 V, then rapid exponential rise; in analysis we idealize **V_BE ≈ 0.7 V whenever the transistor conducts**.

### B. Output (collector) characteristics — CE configuration 🔴

Family of **I_C vs V_CE** curves, one curve per value of I_B:

```
 I_C ↑      saturation │        ACTIVE REGION (curves ≈ flat, slight upward tilt)
     |      region     │
     |     (V_CE <     │________________________ I_B4
     |      ~0.3V,     │________________________ I_B3
     |     steep      /│________________________ I_B2      slopes extrapolate
     |     rise)     / │________________________ I_B1      back to −V_A (Early
     |              /  │                                    voltage) on V_CE axis
     |             /   │____________ I_B = 0  ← cutoff region (I_C ≈ 0)
     └────────────┴────┴─────────────────────────────→ V_CE
                0   ~0.3V
```
**Exam diagram — practice drawing this.** Label the three regions:

| Region | Condition | Behaviour |
|---|---|---|
| **Cutoff** | I_B = 0 (EBJ not forward) | I_C ≈ 0; transistor OFF |
| **Saturation** | V_CE < V_CE(sat) ≈ 0.2–0.3 V | Both junctions forward; I_C < βI_B; curves rise steeply |
| **Active** | V_CE > V_CE(sat), I_B > 0 | I_C ≈ βI_B, nearly independent of V_CE → amplifier region |

### C. Early effect (base-width modulation)

In the active region the curves are not perfectly flat: increasing V_CE widens the CBJ depletion region, **narrowing the effective base**, which slightly increases I_C. Extrapolated backwards, all active-region curves meet at **V_CE = −V_A**, the **Early voltage** (V_A ≈ 50–150 V).

Including it: **I_C = I_S·e^(V_BE/V_T)·(1 + V_CE/V_A)**

Consequence — the transistor has a finite **output resistance**:

- **r_o = V_A / I_C**  (typically tens of kΩ; appears later in the small-signal model, and as the given "r_o = 40 kΩ" in PYQ 2082 Baishakh Q2)

### D. Common mistakes
- Confusing BJT "saturation region" (V_CE small, switch ON) with MOSFET "saturation" (the *amplifying* region). Opposite meanings!
- Drawing active-region curves perfectly flat and then being unable to explain r_o.

### 📌 Section Summary
- **Draw:** output characteristic family with 3 labelled regions and Early-voltage extrapolation.
- **Memorize:** r_o = V_A/I_C; V_CE(sat) ≈ 0.2 V; region conditions.
- No standalone PYQ, but this diagram is **required inside** load-line, switch, and r_o-based answers.

---

## 1.3 Analysis of Transistor Circuits at DC

### A. The universal 5-step procedure 🔴

Given any DC BJT circuit (capacitors → open at DC):

1. **Assume active mode** → set **V_BE = 0.7 V** and use I_C = βI_B, I_E = (β+1)I_B.
2. Write **KVL around the base–emitter loop** → solve for I_B (or I_E).
3. Compute I_C, then **KVL around the collector loop** → V_CE.
4. **Verify the assumption:** active requires V_CE > 0.3 V (npn). If V_CE comes out < 0.3 V (or negative) → transistor is actually **saturated**: redo with V_CE = 0.2 V, I_C ≠ βI_B.
5. If EBJ not forward-biased at all → **cutoff**: all currents = 0.

### B. Worked example (fixed bias with emitter resistor — the exact DC front-end of PYQ 2082 Baishakh Q2)

**Given:** V_CC = 20 V, R_B = 470 kΩ (base to V_CC), R_C = 2.2 kΩ, R_E = 0.56 kΩ, β = 120.

**Base loop KVL:** V_CC = I_B·R_B + V_BE + I_E·R_E, with I_E = (β+1)I_B:

I_B = (V_CC − V_BE) / [R_B + (β+1)R_E] = (20 − 0.7)/(470k + 121×0.56k) = 19.3/537.76k = **35.9 μA**

I_C = βI_B = 120 × 35.9 μA = **4.31 mA**;  I_E = (β+1)I_B ≈ **4.34 mA**

**Collector loop:** V_CE = V_CC − I_C·R_C − I_E·R_E ≈ 20 − 4.31m×2.2k − 4.34m×0.56k = 20 − 9.48 − 2.43 = **8.09 V** → > 0.3 V ✓ active confirmed.

> This DC result (I_E ≈ 4.34 mA → r_e ≈ 6 Ω) is **step 1 of the 5-mark small-signal PYQ** solved fully in §1.9.

### C. Common mistakes
- Forgetting the **(β+1)R_E** reflection term in the base loop — the #1 DC error.
- Not verifying the active assumption.
- Using I_C where I_E belongs in the emitter-resistor drop (acceptable approximation only if stated: I_E ≈ I_C).

### 📌 Section Summary
- **Must be able to calculate:** I_B, I_C, I_E, V_CE for fixed-bias, emitter-bias, and voltage-divider circuits (divider case in §1.6).
- DC analysis is a **prerequisite embedded in every design and amplifier PYQ** — it silently carries 2–3 marks of every 5-mark question.

---

## 1.4 Graphical DC Load Line Analysis

### A. Concept

The transistor obeys its output characteristics; the external collector circuit obeys KVL. The operating point must satisfy **both simultaneously** → intersect them graphically.

**Collector-loop KVL (CE stage, total DC resistance R_DC = R_C + R_E):**

V_CE = V_CC − I_C·R_DC  → rearranged: **I_C = (V_CC − V_CE)/R_DC** — a straight line on the output characteristics.

**Endpoints:**
- V_CE-axis intercept (I_C = 0): **V_CE = V_CC** → cutoff end.
- I_C-axis intercept (V_CE = 0): **I_C(sat) = V_CC / R_DC** → saturation end.
- Slope = **−1/R_DC**.

```
 I_C ↑
 V_CC/R_DC ●  ← saturation end
     |      \.
     |        \.            ● Q-point (I_CQ, V_CEQ) — intersection of load
     |          \.____Q       line with the I_B = I_BQ characteristic curve
     |          /  \.
     |    I_BQ curve \.
     └────────────────●──→ V_CE
                    V_CC   ← cutoff end
```
**Exam diagram — practice drawing this** (load line drawn *on top of* the §1.2 family).

### B. Using the load line

- **Q-point (quiescent point):** the DC operating point (I_CQ, V_CEQ) with no signal applied. Set by the bias circuit (I_BQ) + load line.
- **Signal swing:** an AC input wiggles I_B → the operating point slides along the load line. Q centred near the middle (V_CEQ ≈ V_CC/2) gives **maximum symmetric swing** — this is exactly why bias-design rules in §1.6 choose V_CE = V_CC/2.
- Q too near saturation → negative peaks clip; too near cutoff → positive peaks clip.
- Changing R_C rotates the line (slope); changing V_CC shifts it; changing I_B moves Q along it.

### 📌 Section Summary
- **Memorize:** endpoints (V_CC and V_CC/R_DC); slope −1/R_DC; "mid-point bias ⇒ max swing".
- **Draw:** load line + Q + clipping argument.
- No standalone PYQ, but it is the **justification you quote inside every bias-design answer** ("V_CE = V_CC/2 for maximum symmetrical swing" earns method marks).

---

## 1.5 Transistor as an Amplifier (r_π, r_e, g_m)

### A. Intuition

Bias the BJT in active mode at Q, then superimpose a tiny wiggle v_be on top of V_BE. Because I_C depends **exponentially** on V_BE, a millivolt-scale wiggle produces a milliamp-scale wiggle in I_C. Push that current wiggle through a collector resistor and you get a **large voltage wiggle** → amplification. The three parameters g_m, r_π, r_e are just the linearized "exchange rates" between the small signals.

### B. 🔥 Derivation of transconductance g_m — *PYQ 2081 Ashwin Q3 [4 marks]*

**Objective:** find g_m ≡ i_c / v_be (collector-current response to base–emitter voltage), at bias point I_C.

**Step 1 — start from the fundamental law (active mode):**
i_C = I_S · e^(v_BE / V_T)

**Step 2 — split total quantities into DC + signal:** v_BE = V_BE + v_be:
i_C = I_S · e^((V_BE + v_be)/V_T) = [I_S · e^(V_BE/V_T)] · e^(v_be/V_T) = I_C · e^(v_be/V_T)

**Step 3 — small-signal approximation.** For v_be ≪ V_T (in practice v_be < ~10 mV), expand e^x ≈ 1 + x:
i_C ≈ I_C (1 + v_be/V_T) = I_C + (I_C/V_T)·v_be

**Step 4 — identify the signal component:** i_c = i_C − I_C = (I_C / V_T) · v_be. Therefore:

> **g_m = i_c / v_be = I_C / V_T**  ✅ final result — box this in the exam.

Equivalently g_m = dI_C/dV_BE evaluated at the Q-point — the **slope of the exponential i_C–v_BE curve at Q**.

**Numbers:** V_T ≈ 25 mV ⇒ **g_m ≈ 40·I_C** (in mA/V if I_C in mA). E.g., I_C = 1 mA → g_m = 40 mA/V.

**Exam interpretation:** the 4 marks are for (i) the exponential law, (ii) the DC+AC split, (iii) the linearization with its validity condition v_be ≪ V_T, (iv) the boxed result with slope interpretation. Skipping step 3's condition loses a mark.

### C. Input resistances r_π and r_e

**r_π — resistance seen looking into the base** (signal v_be, signal current i_b):
i_b = i_c/β = (g_m/β)·v_be ⇒

> **r_π = v_be / i_b = β / g_m = β·V_T / I_C = V_T / I_B**

**r_e — resistance seen looking into the emitter** (signal v_be across it, but current i_e):
i_e = i_c/α = (g_m/α)·v_be ⇒

> **r_e = v_be / i_e = α / g_m ≈ 1/g_m = V_T / I_E ≈ 25 mV / I_E**

**Relations to memorize (used constantly in §1.9):**

- r_π = (β + 1)·r_e ≈ β·r_e
- g_m·r_π = β;  g_m·r_e = α ≈ 1
- r_e ≈ 26 mV / I_E(mA) Ω  ← Boylestad's working formula (26 mV variant; 25 mV also accepted — state which you use)

### D. Amplification in one line

With collector resistor R_C: v_o = −i_c·R_C = −g_m·R_C·v_be ⇒ **A_v = −g_m·R_C**. Voltage gain is transconductance × load — the seed of all of §1.9.

### 📦 Formula Box — §1.5

| Formula | What it is | Use / condition |
|---|---|---|
| g_m = I_C/V_T ≈ 40·I_C | Transconductance | Active mode, Q known; the "gain engine" |
| r_π = β/g_m = βV_T/I_C | Base input resistance (π-model) | CE input-impedance calcs |
| r_e = α/g_m ≈ V_T/I_E ≈ 26mV/I_E | Emitter resistance (T-model) | CB/CC and quick CE calcs |
| r_π = (β+1)r_e ≈ βr_e | Model bridge | Converting between π and T results |
| r_o = V_A/I_C | Output resistance | Only when V_A or r_o given |

### Common mistakes
- Using **total** V_BE (0.7 V) instead of I_C/V_T when computing g_m.
- Mixing r_π and r_e (r_π is ~β times larger!).
- Forgetting that all three parameters **depend on the Q-point** — you must do DC analysis first.

### PYQ Check
- 2081 Ashwin Q3: *Derive trans-conductance of BJT.* [4] — full derivation in B above. 

> **Exam-ready when:** you can reproduce the g_m derivation from a blank page in ~6 lines and compute g_m, r_π, r_e in seconds from any Q-point.

---

## 1.6 Biasing BJT for Discrete-Circuit Design 🔥🔥 (GUARANTEED QUESTION — 4/4 YEARS)

### A. Why bias, and what "good bias" means

Biasing establishes a stable Q-point (I_CQ, V_CEQ) so the transistor amplifies linearly. The enemy: **β is unreliable** — it varies unit-to-unit (e.g., 50–150 for the "same" transistor) and with temperature. A good bias circuit makes **I_CQ insensitive to β** (and to V_BE drift and I_CBO).

### B. Fixed bias (base bias) — the bad example you compare against

Single R_B from V_CC to base, R_C to collector. I_B = (V_CC − 0.7)/R_B ⇒ **I_C = β·(V_CC − 0.7)/R_B — directly proportional to β.** If β doubles, I_C doubles and the stage may saturate. Mention this circuit in design answers as the motivation for the voltage divider.

Adding R_E (emitter bias / fixed bias with R_E, §1.3 example) helps via negative feedback: I_C = β(V_CC−0.7)/[R_B+(β+1)R_E] — better, still β-dependent unless (β+1)R_E ≫ R_B.

### C. Voltage-divider bias — THE β-independent circuit 🔴

```
            V_CC
         ┌───┬────┐
         │   │    │
        R_1  R_C ─┴─→ (in a CC design: no R_C, collector ties to V_CC)
         │   │
         ├───┤C          Thévenin view of the base network:
    B ●──┤   ▷ (npn)       V_BB = V_CC·R_2/(R_1+R_2)
         │   │E            R_Th = R_1 ∥ R_2
        R_2  R_E
         │   │
         └───┴──── GND
```
**Exam diagram — practice drawing this** (with coupling/bypass capacitors added when the question says "amplifier": C_in at base, C_out at collector, C_E across R_E).

**Exact analysis (Thévenin):** base loop KVL: V_BB = I_B·R_Th + V_BE + I_E·R_E, with I_B = I_E/(β+1):

> **I_E = (V_BB − V_BE) / [R_E + R_Th/(β+1)]**

**β-independence condition:** if **R_Th/(β+1) ≪ R_E**, i.e. **R_Th ≪ (β+1)R_E**, then

> **I_E ≈ (V_BB − V_BE)/R_E — no β anywhere.** ✅

**Significance of β-independency** 🔥 *PYQ 2082 Bhadra Q1(a) [1 mark]:*
> β varies widely between devices and with temperature. If the divider is designed so that R_Th ≪ (β+1)R_E (divider current ≫ base current), then V_B is fixed by R_1–R_2 alone and I_E ≈ (V_B − V_BE)/R_E is set by resistors only. The Q-point then stays put when the transistor is replaced or heats up → stable, reproducible, mass-producible amplifier.

**Physical stabilizing mechanism (worth 1–2 marks of explanation):** V_B is held stiff by the divider. If I_C tries to rise (β↑ or T↑), V_E = I_E·R_E rises, so V_BE = V_B − V_E **falls**, throttling injection and pulling I_C back down — **negative feedback via R_E**.

**Stiff / firm biasing rules (the design criterion the PYQs name):**

| Term (as used in your PYQs / Floyd–Boylestad) | Criterion | Meaning |
|---|---|---|
| **Stiff** voltage divider | **R_2 ≤ β·R_E / 10**  (equivalently β·R_E ≥ 10·R_2, i.e. base loading ≤ ~10%) | divider current ≈ 10× I_B; V_B essentially independent of β |
| **Firm** biasing | same practical rule, R_2 ≈ β·R_E/10 (some texts allow up to β·R_E/5) | "firmly held" base voltage; treat as the same design step in exams |

If the examiner writes "use firm/stiff biasing method," they want you to **choose R_2 = β·R_E/10** and then compute R_1 — say so explicitly for the method mark.

### D. 🔴 Standard design recipe (memorize this — it answers a guaranteed question)

**Given:** V_CC, desired I_C (or I_E), β. **Find:** R_E, R_C (if CE), R_1, R_2.

1. **Emitter voltage:** choose **V_E = V_CC/10** (rule of thumb: ~1–2 V; large enough to swamp V_BE drift, small enough not to eat swing). → **R_E = V_E / I_E** (I_E ≈ I_C·(β+1)/β ≈ I_C).
2. **Q at mid-line for max swing:** choose **V_CE = V_CC/2** → V_C = V_CE + V_E → **R_C = (V_CC − V_C)/I_C**. *(CC amplifier: no R_C — instead put V_E = V_CC/2, see Design 3.)*
3. **Base voltage:** **V_B = V_E + 0.7 V.**
4. **Stiff/firm divider:** **R_2 = β·R_E / 10.**
5. **R_1 from the divider ratio:** V_B = V_CC·R_2/(R_1+R_2) ⇒ **R_1 = R_2·(V_CC − V_B)/V_B.**
6. (State the check: R_Th = R_1∥R_2 ≪ (β+1)R_E ✓.)

*(Alternative guideline — Sedra–Smith "one-third rule": drop V_CC/3 across R_C, V_CC/3 across V_CE, V_CC/3 across R_E. Acceptable if you state it; the V_CC/10 + V_CC/2 recipe above matches IOE marking schemes.)*

### E. 🔥 Worked PYQ Designs — all four years

---
**Design 1 — PYQ 2082 Bhadra Q1(b) [5]:** *β-independent voltage-divider bias; V_CC = 15 V, I_E = 1 mA, β = 100.*

1. V_E = 15/10 = 1.5 V → **R_E = 1.5 V / 1 mA = 1.5 kΩ**
2. I_C = αI_E = (100/101)(1 mA) ≈ 0.99 mA ≈ 1 mA. V_CE = 7.5 V → V_C = 7.5 + 1.5 = 9 V → **R_C = (15 − 9)/1 mA = 6 kΩ**
3. V_B = 1.5 + 0.7 = 2.2 V
4. **R_2 = βR_E/10 = 100 × 1.5k/10 = 15 kΩ**
5. **R_1 = 15k × (15 − 2.2)/2.2 = 15k × 12.8/2.2 ≈ 87.3 kΩ** (≈ 82–91 kΩ standard value; state nearest standard)
6. Check: R_Th = 87.3k∥15k ≈ 12.8 kΩ ≪ (β+1)R_E = 151.5 kΩ ✓ β-independent.

---
**Design 2 — PYQ 2081 Ashwin Q1 [4]:** *β-independent CE amplifier, stiff biasing; V_CC = 20 V, I_C = 1.5 mA, β = 110.*

1. I_E = I_C(β+1)/β = 1.5×111/110 ≈ 1.51 mA. V_E = 2 V → **R_E = 2/1.51m ≈ 1.32 kΩ** (≈1.3 kΩ)
2. V_CE = 10 V → V_C = 12 V → **R_C = (20 − 12)/1.5m = 5.33 kΩ** (≈5.6 kΩ std)
3. V_B = 2.7 V
4. Stiff: **R_2 = βR_E/10 = 110 × 1.32k/10 ≈ 14.6 kΩ** (≈15 kΩ)
5. **R_1 = 14.6k × (20 − 2.7)/2.7 ≈ 93.5 kΩ** (≈91 kΩ std)

---
**Design 3 — PYQ 2083 Baishakh Q1(b) [5]:** *β-independent DC-biased **common-collector** amplifier, firm biasing; V_CC = 20 V, I_C = 2 mA, β = 100.*

**Key difference:** CC (emitter follower) → **collector tied directly to V_CC (no R_C)**; output taken at emitter; V_CE = V_CC − V_E.

1. For maximum symmetric emitter swing choose **V_E = V_CC/2 = 10 V** (so V_CE = 10 V, Q mid-line).
2. I_E = I_C(β+1)/β = 2×101/100 = 2.02 mA ≈ 2 mA → **R_E = 10 V/2.02 mA ≈ 4.95 kΩ ≈ 5 kΩ** (4.7 kΩ std)
3. V_B = V_E + 0.7 = 10.7 V
4. Firm: **R_2 = βR_E/10 = 100 × 5k/10 = 50 kΩ**
5. **R_1 = 50k × (20 − 10.7)/10.7 = 50k × 9.3/10.7 ≈ 43.5 kΩ** (43 kΩ / 47 kΩ std)
6. Check: R_Th ≈ 23.3 kΩ ≪ (β+1)R_E ≈ 505 kΩ ✓. Draw the circuit: divider R_1/R_2 at base, collector→V_CC, R_E to ground, output via capacitor from emitter.

---
**Design 4 — PYQ 2082 Baishakh Q1 [4]:** *β-independent voltage-divider bias; V_CC = 12 V, I_E = 1 mA, β = 100.*

1. V_E = 1.2 V → **R_E = 1.2 kΩ**
2. V_CE = 6 V → V_C = 7.2 V → **R_C = (12 − 7.2)/1 mA = 4.8 kΩ** (4.7 kΩ std)
3. V_B = 1.9 V
4. **R_2 = 100 × 1.2k/10 = 12 kΩ**
5. **R_1 = 12k × (12 − 1.9)/1.9 ≈ 63.8 kΩ** (62 kΩ / 68 kΩ std)

---

**Marking-scheme observation:** every design carries the same 5 mark-points — (i) circuit diagram, (ii) V_E & R_E choice with justification, (iii) V_CE = V_CC/2 & R_C (or V_E = V_CC/2 for CC), (iv) stiff/firm R_2 rule stated and used, (v) R_1 from divider equation. Write the rules *as sentences* before substituting numbers.

### F. Common mistakes 🔴
- Putting R_C in a **common-collector** design (Design 3) — instant concept error.
- Using I_C and I_E interchangeably without stating I_E ≈ I_C.
- Computing R_1 first: you can't — **R_2 comes from the stiffness rule first**, then R_1 from the ratio.
- Forgetting V_B = V_E **+ 0.7** (not V_E).
- Not stating the stiff/firm criterion when the question explicitly names it — that phrase is worth a mark.

### 📦 Formula Box — §1.6

| Formula | Role |
|---|---|
| V_BB = V_CC·R_2/(R_1+R_2), R_Th = R_1∥R_2 | Thévenin base network |
| I_E = (V_BB − V_BE)/[R_E + R_Th/(β+1)] | Exact bias current |
| Condition R_Th ≪ (β+1)R_E ⇒ I_E ≈ (V_BB − 0.7)/R_E | β-independence |
| Design set: V_E = V_CC/10; V_CE = V_CC/2; V_B = V_E+0.7; R_2 = βR_E/10; R_1 = R_2(V_CC−V_B)/V_B | The recipe |

### PYQ Check (🔥 REPEATED PYQ TOPIC — every year)
- 2083 Baishakh Q1 [1+5] — CC design, firm bias (Design 3)
- 2082 Bhadra Q1 [1+5] — significance of β-independency + design (Design 1)
- 2082 Baishakh Q1 [4] — design (Design 4)
- 2081 Ashwin Q1 [4] — CE design, stiff bias (Design 2)

> **Exam-ready when:** given any (V_CC, I_C or I_E, β, configuration), you produce circuit + all four resistors + stated rules in under 8 minutes.

---

## 1.7 Small-Signal Equivalent Circuit Models (π and T)

### A. What a small-signal model is

For AC analysis we (i) kill DC sources (V_CC → AC ground), (ii) short coupling/bypass capacitors, (iii) **replace the transistor by a linear circuit** valid for small wiggles about Q. Two equivalent linear circuits exist — π and T. Same device, same equations, different convenience.

### B. The hybrid-π model 🔴 (best for CE)

```
      B o───────┬────────────┐                 Two interchangeable forms:
                │            │
               r_π       (↓) g_m·v_π   ┐       • current source = g_m·v_π
        (+ v_π −)            │         ├──o C  • OR equivalently = β·i_b
                │            ├── r_o ──┘         (since g_m·v_π = g_m·r_π·i_b = β·i_b)
      E o───────┴────────────┴────────────o E
```
- Input: r_π between B–E carrying i_b, with v_π = v_be across it.
- Output: dependent current source g_m·v_π (or β·i_b) from C to E, in parallel with **r_o = V_A/I_C** (include r_o only when given/needed).

### C. The T model (best for CB and CC)

```
              C o
                │
            (↓) α·i_e   (or g_m·v_π; collector source same as before)
                │
      B o───────┤
                │
               r_e        ← resistance r_e sits in the EMITTER leg,
                │            carrying the full i_e
              E o
```
- r_e = V_T/I_E in series with the emitter; collector source α·i_e ≈ i_e.
- Looking into the **base** of the T model you see (β+1)·(r_e + anything in the emitter path) — the **resistance-reflection rule**, the workhorse of CC/CE-with-R_E analysis.

### D. Model selection & equivalence

| | Hybrid-π | T model |
|---|---|---|
| Parameters | r_π, g_m (or β·i_b), r_o | r_e, α (≈1) |
| Natural for | **CE** | **CB, CC (emitter follower)** |
| Input resistance element | r_π at base | r_e at emitter |
| Bridge | r_π = (β+1)r_e ≈ βr_e; g_m r_e = α; g_m r_π = β | |

Both give identical answers — choose whichever makes the algebra shortest, and **say which model you are using** in the exam.

### 📌 Section Summary
- **Draw:** both models from memory. **Exam diagram — practice drawing these.** Every §1.9 derivation begins with one of them; the model diagram itself carries ~1 mark of each 5-mark question.
- **Memorize:** the reflection rule R_in(base) = (β+1)(r_e + R_emitter-path).

---

## 1.8 Basic Single-Stage BJT Amplifier Configurations (C-B, C-E, C-C)

### A. Naming rule

The configuration is named after the terminal that is **common to input and output (AC ground)**: input–output pairs are E→C (Common-**Base**), B→C (Common-**Emitter**), B→E (Common-**Collector** / emitter follower).

### B. 🔥 Role of coupling capacitors — *PYQ 2082 Bhadra Q2(a) [2 marks]*

> Coupling capacitors (C_1 at input, C_2 at output) **pass the AC signal while blocking DC**. They connect source→amplifier→load without letting the source or load resistance disturb the DC Q-point (which would shift bias), and without letting the amplifier's DC voltages appear across the load. At signal (mid-band) frequencies X_C = 1/(2πfC) is negligible → the capacitor is an effective **short for AC, open for DC**. Side-effect: they set the amplifier's **lower cutoff frequency** (blocking very low frequencies/DC).

### C. 🔥 Role of the bypass capacitor — *PYQ 2083 Baishakh Q2(a) [2 marks]*

> The bypass capacitor C_E is placed **in parallel with R_E**. At DC it is open, so R_E still provides the negative feedback that stabilizes the Q-point (§1.6). At signal frequencies it is a short, **bypassing R_E to ground** so the emitter is AC-grounded. Without it the gain collapses from |A_v| = R_C/r_e to R_C/(r_e + R_E) (§1.9-C). So C_E lets you keep **DC bias stability AND high AC gain simultaneously**. It also raises input-side gain by removing R_E from the reflected base impedance.

### D. The three circuits (AC signal paths)

```
  CE (input base, output collector):     CB (input emitter, output collector):   CC (input base, output emitter):
        V_CC                                  V_CC                                   V_CC
      R_1│ │R_C ──C_2──> v_o                R_1│ │R_C ──C_2──> v_o                 R_1│ │ (collector straight to V_CC)
  v_in>──C_1──B                          B──┬  C                                v_in>──C_1──B
         R_2│  E                        C_B═╪ (base AC-grounded)                    R_2│  E──C_2──> v_o
            R_E ║ C_E (bypassed)            E──C_1──< v_in                             R_E   (no bypass — R_E IS the load path)
            GND                            R_E to GND                                  GND
```
**Exam diagrams — practice drawing all three** with the divider bias from §1.6 attached.

### E. 🔴 Master comparison table (memorize — a compare question is always possible)

| Property | Common-Emitter | Common-Base | Common-Collector (Emitter Follower) |
|---|---|---|---|
| Input / output terminals | B / C | E / C | B / E |
| Input impedance | Medium (≈ R_1∥R_2∥βr_e, ~kΩ) | **Low** (≈ r_e, ~tens of Ω) | **High** ((β+1)(r_e+R_E∥R_L), ~100 kΩ) |
| Output impedance | Medium–high (≈ R_C) | High (≈ R_C) | **Low** (≈ r_e + R_s′/(β+1)) |
| Voltage gain A_v | **High**, inverting (−g_m R_C) | High, **non-inverting** (+g_m R_C) | ≈ **1** (slightly less), non-inverting |
| Current gain A_i | High (≈ β) | ≈ α ≈ **1** | High (≈ β+1) |
| Phase shift | 180° | 0° | 0° |
| Typical use | General voltage amplifier | High-frequency stages, current buffer | **Buffer / impedance matcher**, output stage |

---

## 1.9 Small-Signal Analysis of Amplifiers 🔥🔥 (GUARANTEED QUESTION — 4/4 YEARS)

### A. Universal 4-step method (state it, then execute it)

1. **DC analysis** → I_E (Q-point) → compute r_e (= 26 mV/I_E), r_π (= βr_e), g_m (= I_C/V_T).
2. **Draw the AC equivalent:** V_CC → ground; capacitors → shorts; then substitute the π or T model. *(This drawing is explicitly demanded by every PYQ — never skip it.)*
3. Write KVL/KCL for **Z_i = v_i/i_i**, **Z_o = v_o/i_o (with v_in = 0)**, **A_v = v_o/v_i** (and A_i when asked).
4. Sanity-check signs and magnitudes against the §1.8 table.

Below, R_B ≡ R_1∥R_2 (the bias divider as seen by AC).

---
### B. 🔥 Common-Emitter amplifier (bypassed R_E) — *PYQ 2082 Bhadra Q2(b) [5]*

**AC equivalent (hybrid-π):** source v_i → base node; r_π from B to ground (E is AC ground via C_E); R_B from B to ground; at the collector, current source g_m·v_π (downward C→E) in parallel with r_o and R_C to ground.

```
  v_i o──┬────┬──● B        C ●───┬──────┬──────┬──o v_o
         │    │  │(+           (↓)│      │      │
        R_B  r_π │ v_π)    g_m·v_π│     r_o    R_C
         │    │  │(−              │      │      │
        ─┴────┴──┴─── E = AC ground ─────┴──────┴──
```

**Input impedance.** Looking into the base: only r_π to ground (emitter grounded). With the divider:
> **Z_i = R_B ∥ r_π = R_1 ∥ R_2 ∥ βr_e**

**Output impedance.** Set v_i = 0 ⇒ v_π = 0 ⇒ dependent source = 0 (open). Looking back from the output:
> **Z_o = R_C ∥ r_o ≈ R_C** (when r_o ≥ 10R_C)

**Voltage gain.** v_π = v_i (base to grounded emitter). Output node: v_o = −(g_m v_π)(R_C ∥ r_o):
> **A_v = −g_m(R_C ∥ r_o) = −(R_C ∥ r_o)/r_e ≈ −R_C/r_e**  (negative ⇒ 180° inversion)

With an external load R_L (coupled by C_2): replace R_C by R_C∥R_L.

*(Current gain if asked: A_i = −A_v·Z_i/R_C ≈ β·R_B/(R_B + r_π) ≈ β for stiff R_B.)*

---
### C. 🔥 CE with UNBYPASSED R_E + Worked numerical — *PYQ 2082 Baishakh Q2 [5]*

**Given circuit:** V_CC = 20 V; R_B = 470 kΩ (single base resistor); R_C = 2.2 kΩ; R_E = 0.56 kΩ (no bypass capacitor shown); C_1, C_2 coupling; **β = 120, r_o = 40 kΩ**. Find Z_i, A_v, Z_o.

**Step 1 — DC (done in §1.3-B):** I_B = 35.9 μA, I_E = 4.34 mA ⇒ **r_e = 26 mV/4.34 mA ≈ 5.99 Ω**.

**Step 2 — AC equivalent:** base sees R_B to ground and, into the base, r_π (=βr_e) in series with the **unbypassed R_E** (T-model thinking). Collector: β·i_b source with R_C; r_o sits from C to E.

**Step 3 — key derivation (reflection rule).** Base current i_b flows in r_π; emitter carries (β+1)i_b through R_E:
v_i = i_b·βr_e + (β+1)i_b·R_E ⇒
> **Z_b = v_i/i_b = βr_e + (β+1)R_E ≈ β(r_e + R_E)**
> **Z_i = R_B ∥ Z_b**;  **Z_o ≈ R_C**;  **A_v = −βR_C/Z_b ≈ −R_C/(r_e + R_E)**

*(These approximations require r_o ≥ 10(R_C + R_E) — that is exactly why the question gives you r_o: to check it.)*

**Step 4 — numbers.**
- Z_b = 120×5.99 + 121×560 ≈ 719 + 67,760 ⇒ ≈ **67.9 kΩ** (dominated by the reflected R_E)
- **Z_i = 470 kΩ ∥ 67.9 kΩ ≈ 59.3 kΩ**
- Check r_o: 10(R_C + R_E) = 10(2.2k + 0.56k) = 27.6 kΩ ≤ r_o = 40 kΩ ✓ ⇒ r_o negligible.
- **Z_o ≈ R_C = 2.2 kΩ**
- **A_v = −βR_C/Z_b = −(120×2.2k)/67.9k ≈ −3.89** ⇒ small gain, inverted — the price of an unbypassed R_E (this is the numerical proof of the bypass-capacitor story in §1.8-C).

**Exam shortcut / observation:** when (β+1)R_E ≫ βr_e, A_v ≈ −R_C/R_E = −2.2k/0.56k ≈ −3.93 — a 5-second sanity check of your long answer.

---
### D. 🔥 Common-Base amplifier — *PYQ 2083 Baishakh Q2(b) [5]*

**Circuit:** input at emitter through C_1; base AC-grounded via base bypass capacitor C_B (divider R_1–R_2 still sets DC); output at collector; R_E from emitter to ground, R_C at collector.

**AC equivalent (T model is natural):**
```
  v_i o──C_1──┬──● E ──[r_e]──● B(gnd)      C ●───┬─────┬──o v_o
              │        i_e →              (↓) α·i_e    R_C
             R_E                              │        │
              ⏚                               ⏚        ⏚
```

**Input impedance.** Looking into the emitter (base grounded): v_i = i_e·r_e ⇒ R_in(emitter) = r_e. With R_E in parallel:
> **Z_i = R_E ∥ r_e ≈ r_e** (very low, tens of Ω — the defining CB feature)

**Output impedance.** v_i = 0 ⇒ i_e = 0 ⇒ source α·i_e = 0 (open):
> **Z_o = R_C** (in parallel with the very large CB output resistance of the transistor ≈ r_o(1+g_mR_E′) — state Z_o ≈ R_C)

**Voltage gain.** i_e = v_i/r_e; v_o = +(α·i_e)(R_C∥R_L):
> **A_v = +α·R_C/r_e ≈ +g_m·R_C = +R_C/r_e** — same magnitude as CE but **non-inverting (0°)**

**Current gain:** A_i = i_c/i_e = **α ≈ 1** (slightly less than unity — CB is not a current amplifier).

---
### E. 🔥 Common-Collector (Emitter Follower) — *PYQ 2081 Ashwin Q2 [1+4]*

**Part (a) — Why "emitter follower"? [1]:**
> The output is taken at the emitter, and v_E = v_B − v_BE with v_BE nearly constant (~0.7 V DC, tiny signal variation). Hence the emitter voltage **follows the base voltage** almost exactly: A_v = v_o/v_i ≈ 1, in phase. The stage gives no voltage gain but large current gain and an impedance step-down — the transistor equivalent of a buffer.

**Part (b) — model + derivations [4].** Circuit: divider bias at base, collector directly to V_CC (AC ground!), R_E emitter→ground, output across R_E (∥ R_L via C_2).

**AC equivalent (T model):**
```
  v_i o──┬──● B ──[ i_b → into base ]                 collector = AC ground
         │        base sees (β+1)(r_e + R_E∥R_L)
        R_B                │
         ⏚          E ●────┴──[r_e above it]── v_o node ──R_E∥R_L──⏚
```

**(i) Input resistance.** v_i = i_b·(β+1)(r_e + R_E′) where R_E′ = R_E∥R_L (reflection rule):
> **R_in(base) = (β+1)(r_e + R_E′)**;  **Z_i = R_B ∥ (β+1)(r_e + R_E′)** — **high** (often ≫100 kΩ)

**(ii) Voltage gain.** The emitter current i_e flows through r_e then R_E′; output is across R_E′ — a voltage divider:
v_i = i_e(r_e + R_E′), v_o = i_e·R_E′ ⇒
> **A_v = R_E′/(r_e + R_E′) ≈ 1 (but < 1), non-inverting** — because r_e (a few Ω) ≪ R_E′ (kΩ)

**(iii) Current gain.** i_e = (β+1)i_b ⇒ device current gain = **β+1**. Overall (including the R_B divider): A_i = (β+1)·R_B/(R_B + Z_b) ≈ β+1 for large R_B. State both.

**(iv) Output impedance (know it — often the follow-up):** kill v_i, look into the emitter; the source resistance R_s′ = R_s∥R_B seen at the base gets **divided** by (β+1):
> **Z_o = R_E ∥ [r_e + R_s′/(β+1)] ≈ r_e + R_s′/(β+1)** — **very low** (Ω-range) ⇒ ideal buffer/output stage.

---
### F. 🔴 Results comparison table (the one-look revision grid)

| Quantity | CE (bypassed) | CE (unbypassed R_E) | CB | CC |
|---|---|---|---|---|
| Z_i | R_B∥βr_e | R_B∥β(r_e+R_E) | R_E∥r_e ≈ r_e | R_B∥(β+1)(r_e+R_E′) |
| Z_o | R_C∥r_o ≈ R_C | ≈ R_C | ≈ R_C | r_e + R_s′/(β+1) |
| A_v | −R_C′/r_e (high, inv.) | −R_C/(r_e+R_E) (low, inv.) | +R_C′/r_e (high, non-inv.) | R_E′/(r_e+R_E′) ≈ 1 |
| A_i | ≈ β | ≈ β | ≈ α ≈ 1 | ≈ β+1 |

(Primes denote ∥ with load: R_C′ = R_C∥R_L, R_E′ = R_E∥R_L.)

### G. Common mistakes 🔴
- Skipping the DC step — r_e is unknown without I_E, and the whole answer collapses.
- **Not drawing the AC equivalent** when the question says "draw the small-signal equivalent circuit" — that's ~2 of the 5 marks.
- Dropping the (β+1) factor in the reflection rule, or reflecting the wrong way for Z_o of the follower (divide by (β+1), don't multiply).
- Sign of A_v: CE negative; CB and CC positive.
- Forgetting to check/mention r_o ≥ 10(R_C+R_E) when r_o is given (2082 Baishakh Q2 gives r_o precisely to test this).

### PYQ Check (🔥 REPEATED PYQ TOPIC — every year, configuration rotates)
- 2082 Bhadra Q2 [2+5] — coupling caps + CE derivation (B above)
- 2082 Baishakh Q2 [5] — CE-with-R_E numerical (C above, full solution)
- 2083 Baishakh Q2 [2+5] — bypass cap + CB derivation (D above)
- 2081 Ashwin Q2 [1+4] — emitter follower + CC derivations (E above)

> **Exam-ready when:** for each configuration you can, from a blank page: draw circuit → draw AC model → derive Z_i, Z_o, A_v (A_i) → quote typical magnitudes — in ≤10 minutes.

---

## 1.10 Transistor as a Switch — Cutoff and Saturation 🟡 *PYQ 2082 Baishakh Q3 [4]*

### A. Concept

Restrict operation to the two **ends of the load line** — cutoff (open switch) and saturation (closed switch) — skipping the active region entirely. This is the basis of BJT logic/driver circuits (the circuit is a logic **inverter**).

### B. Circuit and the two states

```
            V_CC                       Load line view:
             │                          I_C ↑ SAT ● v_in high (Q at top: switch ON)
            R_C                             |   \.
             ├────o v_o = V_CE              |     \.
   v_in o──R_B──B                           |       \.
             ▷ (npn)                        |         \. ● CUTOFF, v_in ≈ 0
             │E                             └───────────●──→ V_CE = V_CC (switch OFF)
             ⏚
```
**Exam diagram — practice drawing both** (circuit + load line with the two operating points marked).

**State 1 — Cutoff (switch OPEN):** v_in ≈ 0 (< 0.5 V) → EBJ not forward → I_B = 0 → **I_C ≈ 0**, **v_o = V_CE ≈ V_CC**. The C–E path behaves as an open switch (only leakage I_CEO flows).

**State 2 — Saturation (switch CLOSED):** v_in high → I_B large. Maximum possible collector current is fixed by the external circuit:
> **I_C(sat) = (V_CC − V_CE(sat))/R_C ≈ V_CC/R_C**, with **V_CE(sat) ≈ 0.2 V**

**Condition to guarantee saturation:**
> **I_B > I_C(sat)/β**  (design with overdrive: I_B ≈ 2–10× this minimum; equivalently the circuit forces βI_B > I_C(sat), so the transistor cannot deliver βI_B and both junctions become forward-biased)

The C–E path then behaves as a closed switch with only ~0.2 V across it.

### C. 4-mark answer skeleton
(i) circuit diagram; (ii) cutoff explanation with v_o ≈ V_CC; (iii) saturation explanation with I_C(sat), V_CE(sat), and the I_B > I_C(sat)/β condition; (iv) load-line/inverter remark. Add one number example if time permits (e.g., V_CC = 10 V, R_C = 1 kΩ ⇒ I_C(sat) ≈ 9.8 mA; β = 100 ⇒ need I_B > 98 μA).

### Common mistakes
- Writing I_C = βI_B **in saturation** — false; in saturation I_C < βI_B and I_C is set by R_C.
- Using V_CE = 0 exactly instead of V_CE(sat) ≈ 0.2 V.

---

## 1.11 A General Large-Signal Model of the BJT: The Ebers–Moll Model 🟢 (syllabus-complete; no PYQ in your 4 papers)

### A. Idea

One model valid in **all four modes**: represent the BJT as its two physical diodes **plus** two dependent sources expressing the coupling (transistor action) between them.

```
            C o──────┬──────────┐
                     │          │
                 (▲ diode    (↓) α_F·I_DE      I_DE = current of the B–E diode
                  D_C:          │              I_DC = current of the B–C diode
                  I_DC)         │
      B o────────────┤          │              Each junction = a diode, and each
                     │          │              injects a fraction (α_F forward,
                 (▲ diode    (↑) α_R·I_DC      α_R reverse) of the OTHER
                  D_E:          │              junction's diode current.
                  I_DE)         │
            E o──────┴──────────┘
```

### B. Equations (npn)

Diode currents: I_DE = I_ES(e^(V_BE/V_T) − 1), I_DC = I_CS(e^(V_BC/V_T) − 1). Terminal currents:

> **I_E = I_ES(e^(V_BE/V_T) − 1) − α_R·I_CS(e^(V_BC/V_T) − 1)**
> **I_C = α_F·I_ES(e^(V_BE/V_T) − 1) − I_CS(e^(V_BC/V_T) − 1)**
> Reciprocity: **α_F·I_ES = α_R·I_CS = I_S**

| Symbol | Meaning | Typical |
|---|---|---|
| α_F | Forward CB gain (normal α) | 0.98–0.998 |
| α_R | Reverse CB gain (poor — asymmetric doping) | 0.02–0.5 |
| I_ES, I_CS | EBJ / CBJ diode scale currents | fA–pA |

### C. Modes recovered as special cases
- **Active:** V_BE > 0, V_BC < 0 ⇒ second exponentials ≈ 0 ⇒ I_C ≈ α_F I_ES e^(V_BE/V_T) = I_S e^(V_BE/V_T) — recovers §1.1.
- **Saturation:** both exponentials active ⇒ V_CE(sat) = V_BE − V_BC ≈ 0.2 V emerges naturally.
- **Cutoff:** both ≈ −(leakage) ⇒ currents ≈ 0.

> **Exam-ready when:** you can draw the two-diode/two-source model, write the two equations + reciprocity, and show how active mode falls out. Prepare at 4-mark depth; probability low but it is *the only Chapter-1 topic never yet asked* — a fresh-question candidate.


---
---

# BJT Final Revision

## 1. One-Shot Conceptual Summary

A BJT is two junctions sharing a thin, lightly doped base. Forward-bias the EBJ and reverse-bias the CBJ (**active mode**) and the heavily doped emitter injects carriers that diffuse across the thin base and are collected: I_C = I_S·e^(V_BE/V_T) ≈ βI_B ≈ αI_E — a voltage-controlled current source using **both carrier types (bipolar)**. Its behaviour is drawn as **output characteristics** (cutoff / active / saturation; slight tilt = Early effect ⇒ r_o = V_A/I_C). The external collector circuit adds a **load line**; their intersection is the **Q-point**, which we place mid-line (V_CE ≈ V_CC/2) for maximum swing using a **voltage-divider bias** designed so R_Th ≪ (β+1)R_E — making I_E ≈ (V_B − 0.7)/R_E, **independent of β** (stiff/firm rule R_2 = βR_E/10). Around Q, linearize: **g_m = I_C/V_T**, r_π = β/g_m, r_e ≈ 26 mV/I_E, giving the **hybrid-π** and **T** models. Insert these into the three configurations: **CE** = high inverting voltage gain (−R_C/r_e; falls to −R_C/(r_e+R_E) if R_E unbypassed — hence the **bypass capacitor**; **coupling capacitors** isolate DC while passing signal); **CB** = low Z_in, non-inverting gain, A_i ≈ 1; **CC (emitter follower)** = A_v ≈ 1, huge Z_in, tiny Z_out — a buffer. Drive the base hard or not at all and the BJT is a **switch**: cutoff (open, v_o ≈ V_CC) ↔ saturation (closed, V_CE(sat) ≈ 0.2 V, need I_B > I_C(sat)/β). The **Ebers–Moll model** (two diodes + two α-coupled sources) unifies all modes in one large-signal description.

## 2. Important Diagrams (practice each until automatic)

| # | Diagram | Where | Priority |
|---|---|---|---|
| D1 | npn structure + npn/pnp symbols with current directions | §1.1 | 🟡 |
| D2 | CE output characteristics, 3 regions, Early extrapolation | §1.2 | 🔴 (embedded everywhere) |
| D3 | DC load line with Q-point and clipping | §1.4 | 🔴 |
| D4 | Voltage-divider bias circuit (+ CC variant, + capacitors) | §1.6 | 🔴 GUARANTEED |
| D5 | Hybrid-π model; T model | §1.7 | 🔴 GUARANTEED |
| D6 | CE, CB, CC full amplifier circuits | §1.8 | 🔴 |
| D7 | AC equivalent of CE / CB / CC | §1.9 | 🔴 GUARANTEED |
| D8 | BJT switch circuit + two-point load line | §1.10 | 🟡 |
| D9 | Ebers–Moll two-diode model | §1.11 | 🟢 |

## 3. Important Derivations

| # | Derivation | Section | Status |
|---|---|---|---|
| Dv1 | β = α/(1−α) and α = β/(β+1) | §1.1-D | Result to remember (1-line derivation) |
| Dv2 | **g_m = I_C/V_T** from the exponential law | §1.5-B | 🔴 **Important derivation** (asked 2081) |
| Dv3 | r_π = β/g_m, r_e = α/g_m | §1.5-C | Short derivation |
| Dv4 | I_E = (V_BB−V_BE)/[R_E + R_Th/(β+1)] → β-independence condition | §1.6-C | 🔴 Important (justifies every design) |
| Dv5 | CE: Z_i = R_B∥βr_e, Z_o ≈ R_C, A_v = −g_m(R_C∥r_o) | §1.9-B | 🔴 Important (asked 2082 Bhadra) |
| Dv6 | Reflection rule Z_b = βr_e + (β+1)R_E | §1.9-C | 🔴 Important (asked 2082 Baishakh) |
| Dv7 | CB: Z_i ≈ r_e, A_v = +R_C/r_e | §1.9-D | 🔴 Important (asked 2083) |
| Dv8 | CC: R_in = (β+1)(r_e+R_E′), A_v = R_E′/(r_e+R_E′), A_i ≈ β+1, Z_o ≈ r_e + R_s′/(β+1) | §1.9-E | 🔴 Important (asked 2081) |
| Dv9 | Ebers–Moll equations → active-mode limit | §1.11 | 🟢 Result to remember |

## 4. Formula Sheet (clean)

**Device:** I_E = I_C + I_B · I_C = βI_B = αI_E · β = α/(1−α) · α = β/(β+1) · I_C = I_S e^(V_BE/V_T) · r_o = V_A/I_C · V_BE ≈ 0.7 V · V_CE(sat) ≈ 0.2 V

**Small-signal parameters:** g_m = I_C/V_T ≈ 40 I_C · r_π = β/g_m = βV_T/I_C · r_e = α/g_m ≈ 26 mV/I_E · r_π = (β+1)r_e

**Load line:** I_C = (V_CC − V_CE)/(R_C+R_E); ends V_CC and V_CC/(R_C+R_E)

**Voltage-divider bias:** V_BB = V_CC R_2/(R_1+R_2) · R_Th = R_1∥R_2 · I_E = (V_BB−V_BE)/[R_E + R_Th/(β+1)] · β-independent when R_Th ≪ (β+1)R_E

**Design recipe:** V_E = V_CC/10 → R_E = V_E/I_E · V_CE = V_CC/2 → R_C = (V_CC−V_CE−V_E)/I_C · V_B = V_E+0.7 · **R_2 = βR_E/10** · R_1 = R_2(V_CC−V_B)/V_B · (CC: no R_C, V_E = V_CC/2)

**Amplifiers:** CE: Z_i = R_B∥βr_e, Z_o ≈ R_C∥r_o, A_v = −(R_C∥r_o∥R_L)/r_e · CE+R_E: Z_b = β(r_e+R_E), A_v ≈ −R_C/(r_e+R_E) · CB: Z_i ≈ r_e, Z_o ≈ R_C, A_v = +R_C′/r_e, A_i = α · CC: Z_i = R_B∥(β+1)(r_e+R_E′), A_v = R_E′/(r_e+R_E′) ≈ 1, A_i ≈ β+1, Z_o ≈ r_e + (R_s∥R_B)/(β+1)

**Switch:** I_C(sat) = (V_CC−V_CE(sat))/R_C · guarantee: I_B > I_C(sat)/β

**Ebers–Moll:** I_E = I_ES(e^(V_BE/V_T)−1) − α_R I_CS(e^(V_BC/V_T)−1) · I_C = α_F I_ES(e^(V_BE/V_T)−1) − I_CS(e^(V_BC/V_T)−1) · α_F I_ES = α_R I_CS = I_S

## 5. High-Priority Concepts (evidence-based)

1. 🔥 **Voltage-divider bias design** (stiff/firm) for CE **and** CC — appeared in **all 4 papers**.
2. 🔥 **Small-signal Z_i, Z_o, A_v of CE, CB, CC** — appeared in **all 4 papers**, configuration rotating; be equally fluent in all three.
3. 🔥 **Coupling & bypass capacitor roles** — 2 of 4 papers, always as the 2-mark lead-in.
4. 🟡 g_m derivation · BJT as switch · bipolar-vs-unipolar — each asked once; cheap 4-mark preparation.
5. 🟡 DC analysis + load line — never standalone, always embedded (they are the marks *inside* the design/numerical questions).
6. 🟢 Ebers–Moll — never asked yet; prepare a 4-mark version precisely because it's the untouched syllabus item.

## 6. Common Mistakes (master list)

1. β = α/(1+α) instead of α/(1−α).
2. Forgetting (β+1)R_E in base-loop KVL (DC) and (β+1) reflection (AC).
3. Confusing BJT saturation with MOSFET saturation.
4. Designing a CC stage with a collector resistor.
5. Computing R_1 before R_2 (R_2 comes from the stiffness rule).
6. V_B = V_E (forgetting +0.7).
7. Skipping DC analysis before small-signal work (no I_E ⇒ no r_e).
8. Not drawing the demanded AC equivalent circuit.
9. Wrong A_v signs (CE −, CB +, CC + and <1).
10. Using I_C = βI_B inside saturation.
11. Ignoring the given r_o (fail to check r_o ≥ 10(R_C+R_E)).
12. Using v_be-scale ≫ V_T while still applying small-signal formulas (state the validity condition).

## 7. Numerical Problem Types You Must Be Able to Solve

| Type | Given → Find | Template |
|---|---|---|
| N1 Bias design | V_CC, I_C/I_E, β → all resistors | §1.6-D recipe + Designs 1–4 |
| N2 Bias analysis | Circuit resistors → I_CQ, V_CEQ | §1.6-C exact formula / §1.3 procedure |
| N3 Amplifier numerical | Circuit + β (+r_o) → Z_i, Z_o, A_v | §1.9-C worked PYQ |
| N4 Parameter calc | Q-point → g_m, r_π, r_e | §1.5 |
| N5 Switch design | V_CC, R_C, β → required I_B / R_B | §1.10 |
| N6 α↔β / current juggling | any two of I_B, I_C, I_E, α, β → rest | §1.1-D |

---
---

# Complete BJT PYQ Bank

*(Every Chapter-1 question from the four provided papers; wording preserved; organized by year. Questions 3–10+ of each paper belong to Chapters 2–5 and are excluded.)*

## 2083 Baishakh — Back (New Course), ENEX 151
| Q | Question (verbatim) | Marks | Topic | Type |
|---|---|---|---|---|
| 1 | Why BJT is bipolar and FET is unipolar? Design β-independent type DC biased common collector amplifier. Given parameters are: V_CC = 20 V, I_C = 2 mA, and β = 100. Use firm biasing method. | [1+5] | Device physics + CC bias design | Theory + Design |
| 2 | Explain the role of bypass capacitor in amplifier circuits. Draw the small signal equivalent circuit of a common base amplifier circuit and find its input impedance, output impedance and voltage gain. | [2+5] | Bypass capacitor + CB small-signal | Theory + Derivation |

## 2082 Bhadra — Regular (New Course), ENEX 151
| Q | Question (verbatim) | Marks | Topic | Type |
|---|---|---|---|---|
| 1 | What is the significance of β-independency in a voltage divider biasing circuit? Design a β-independent voltage divider bias circuit for the given parameters: V_CC = 15 V, I_E = 1 mA and β = 100. | [1+5] | β-independence + bias design | Theory + Design |
| 2 | Explain the role of coupling capacitors in amplifier circuits. Draw the small signal equivalent circuit of a common emitter amplifier circuit and find its input impedance, output impedance and voltage gain. | [2+5] | Coupling capacitors + CE small-signal | Theory + Derivation |

## 2082 Baishakh — Back (New Course), EX 151
| Q | Question (verbatim) | Marks | Topic | Type |
|---|---|---|---|---|
| 1 | Design a β-independent voltage divider bias circuit using the appropriate guidelines for the given parameters: V_CC = 12 V, I_E = 1 mA, and β = 100. | [4] | Bias design | Design |
| 2 | Determine input resistance, voltage gain and output resistance of given common emitter BJT Amplifier. β = 120 and r_o = 40 kΩ. *(Circuit: V_CC = +20 V, R_B = 470 kΩ, R_C = 2.2 kΩ, R_E = 0.56 kΩ, coupling C_1, C_2.)* | [5] | CE-with-R_E small-signal | Numerical |
| 3 | Explain the operation principle of a BJT as a switch with the necessary diagrams. | [4] | Switch (cutoff/saturation) | Theory |

## 2081 Ashwin — Regular (New Course – 2080 Batch), EX 151
| Q | Question (verbatim) | Marks | Topic | Type |
|---|---|---|---|---|
| 1 | Design β independent type dc biased common emitter amplifier. Given parameters V_CC = 20 V, I_C = 1.5 mA and β = 110. Use stiff biasing method. | [4] | CE bias design | Design |
| 2 | Why is a common collector BJT amplifier also known as an emitter follower? Draw the small signal model of common collector amplifier circuit and derive expressions for input resistance, voltage gain, and current gain. | [1+4] | Emitter follower + CC small-signal | Theory + Derivation |
| 3 | Derive trans-conductance of BJT. | [4] | g_m derivation | Derivation |

---

# PYQ → What to Study

| PYQ | Topic Tested | Notes Section(s) to Study | Required Skill |
|---|---|---|---|
| 2083 Q1(a) [1] | Bipolar vs unipolar conduction | §1.1-C (boxed answer) | State both carrier arguments |
| 2083 Q1(b) [5] | CC bias design, firm rule | §1.6-C, §1.6-D, **Design 3**; swing logic §1.4 | Design R_E, R_1, R_2 with V_E = V_CC/2; no R_C |
| 2083 Q2(a) [2] | Bypass capacitor | §1.8-C (+ numerical proof §1.9-C) | Explain DC-open/AC-short & gain restoration |
| 2083 Q2(b) [5] | CB small-signal | §1.7-C (T model), **§1.9-D**; table §1.9-F | Draw AC model; derive Z_i ≈ r_e, Z_o ≈ R_C, A_v = +R_C/r_e |
| 2082 Bhadra Q1(a) [1] | Significance of β-independence | §1.6-C (boxed answer) | State variability of β + resistor-set I_E |
| 2082 Bhadra Q1(b) [5] | Voltage-divider design | §1.6-D, **Design 1**; prerequisite §1.3 | Full recipe with stated rules |
| 2082 Bhadra Q2(a) [2] | Coupling capacitors | §1.8-B | DC-block/AC-couple + Q-point protection |
| 2082 Bhadra Q2(b) [5] | CE small-signal | §1.7-B (π model), **§1.9-B**; parameters §1.5 | Draw model; derive Z_i, Z_o, A_v with signs |
| 2082 Baishakh Q1 [4] | Voltage-divider design | §1.6-D, **Design 4** | Full recipe |
| 2082 Baishakh Q2 [5] | CE-with-R_E numerical | §1.3-B (DC) → **§1.9-C** (full solution); r_o check §1.2-C | DC → r_e → reflection rule → numbers; r_o ≥ 10(R_C+R_E) check |
| 2082 Baishakh Q3 [4] | BJT as switch | **§1.10**; regions §1.2-B; load line §1.4 | Circuit + both states + I_B > I_C(sat)/β + diagram |
| 2081 Q1 [4] | CE bias design, stiff rule | §1.6-D, **Design 2** | Full recipe, quote stiff rule |
| 2081 Q2(a) [1] | Why "emitter follower" | §1.9-E boxed answer | v_E follows v_B, A_v ≈ 1 |
| 2081 Q2(b) [4] | CC derivations | §1.7-C, **§1.9-E**; reflection rule §1.9-C | Derive R_in, A_v, A_i (and Z_o) |
| 2081 Q3 [4] | Transconductance derivation | **§1.5-B**; law from §1.1-D | 4-step derivation with validity condition |

---

# Final Coverage Audit

**Syllabus coverage** — ✅ all eleven headings 1.1–1.11 present as the document's backbone, in syllabus order; nothing skipped (1.2 load-line and 1.11 Ebers–Moll included despite zero PYQs, per Rule 4).

**Reference coverage** — ✅ Sedra–Smith supplied the exponential-law/g_m framework, π–T models, Early effect, Ebers–Moll, and the one-third design alternative; Boylestad–Nashelsky supplied r_e ≈ 26 mV/I_E, the exact 470k/2.2k/0.56k unbypassed-R_E analysis method and the r_o ≥ 10(R_C+R_E) check; Floyd supplied the stiff-divider rule (R_2 ≤ βR_E/10) and switch treatment; Millman–Halkias/Bell corroborate bias-stability and configuration comparisons. ✅ Notation unified to I_B, I_C, I_E, V_BE, V_CE, α, β, g_m, r_π, r_e, r_o; the 25 mV vs 26 mV V_T convention and h_FE ≡ β equivalences flagged.

**PYQ coverage** — ✅ 10 BJT questions (15 sub-parts) identified across 4 papers; ✅ each appears inside its syllabus section; ✅ all appear in the Complete PYQ Bank; ✅ all mapped in PYQ → What to Study. Cross-topic questions handled: 2082 Baishakh Q2 spans DC analysis + small-signal (placed in §1.9, DC prerequisite cross-referenced to §1.3); 2083 Q1 spans device physics + biasing (split across §1.1/§1.6).

**Exam preparation** — ✅ derivations table (Dv1–Dv9) distinguishes *important derivations* from *results to remember*; ✅ formula boxes per section + consolidated sheet; ✅ 9 exam diagrams flagged; ✅ 6 numerical templates; ✅ 🔥 repeated topics identified (bias design 4/4, small-signal 4/4); ✅ priority labels 🔴🟡🟢 assigned from PYQ evidence.

*End of Chapter 1 notes.*
