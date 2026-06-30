---
tags: [learning-progress, curriculum, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
refined: [2026-06-30]
---

# Learning Path

A visual roadmap for [[Signals, Systems And Inference]], built for a learner starting from zero. This is the "map"; [[Curriculum]] is the detailed syllabus and [[Score Log]] holds the gate scores. **You are here → P0.**

Legend: ▶ active · 🔒 locked (unlocks when the prerequisite's quiz is passed at ≥ 80%) · ✅ passed.

---

## 1. The big picture — what the whole journey is about

Every topic serves one final goal: **pull a wanted signal out of noise.** The path climbs in four moves.

```mermaid
flowchart LR
    A["DESCRIBE<br/>a signal"] --> B["MODEL<br/>a system"]
    B --> C["ADD<br/>randomness"]
    C --> D["INFER<br/>estimate / detect<br/>under noise"]
    style A fill:#1565c0,color:#fff
    style B fill:#1565c0,color:#fff
    style C fill:#6a1b9a,color:#fff
    style D fill:#2e7d32,color:#fff
```

That last box — **inference** — is the math of a satellite receiver. Everything before it is the equipment you need to get there.

---

## 2. Dependency map — why the order is what it is

Arrows mean "must understand the source before the target." Foundations (P0–P4) are the prerequisites the book assumes; the 13 chapters build on them.

```mermaid
flowchart TD
    subgraph F["🧱 Phase 0 — Foundations (the prerequisites you build first)"]
        P0["P0 · Math Toolkit ▶<br/><small>complex numbers · Euler · phasors</small>"]
        P1["P1 · Linear Algebra 🔒<br/><small>vectors · matrices · eigenvalues</small>"]
        P2["P2 · Calculus &amp; Diff Eq 🔒<br/><small>rates · e^at · linear ODEs</small>"]
        P3["P3 · Signals &amp; Systems 🔒<br/><small>LTI · convolution · Fourier</small>"]
        P4["P4 · Probability 🔒<br/><small>random variables · Bayes · Gaussian</small>"]
    end

    P0 --> P1
    P0 --> P2
    P0 --> P3
    P1 --> P3
    P2 --> P3
    P0 --> P4

    subgraph DET["📐 Deterministic half — signals &amp; control"]
        C1["Ch1 · Signals &amp; Systems"]
        C2["Ch2 · Amplitude, Phase, Group Delay"]
        C3["Ch3 · Pulse-Amplitude Modulation ⭐"]
        C4["Ch4 · State-Space Models"]
        C5["Ch5 · LTI State-Space Models"]
        C6["Ch6 · Observers &amp; State Feedback"]
    end

    subgraph STO["🎲 Stochastic half — inference"]
        C7["Ch7 · Probabilistic Models"]
        C8["Ch8 · Estimation"]
        C9["Ch9 · Hypothesis Testing"]
        C10["Ch10 · Random Processes"]
        C11["Ch11 · Power Spectral Density"]
        C12["Ch12 · Signal Estimation — Wiener/Kalman ⭐"]
        C13["Ch13 · Signal Detection — matched filter ⭐"]
    end

    P3 --> C1 --> C2 --> C3
    P1 --> C4
    P2 --> C4 --> C5 --> C6
    P4 --> C7 --> C8 --> C9
    P3 --> C10
    C7 --> C10 --> C11
    C8 --> C12
    C11 --> C12
    C9 --> C13
    C3 --> C13

    classDef active fill:#2e7d32,color:#fff,stroke:#1b5e20,stroke-width:2px;
    classDef sat fill:#ef6c00,color:#fff,stroke:#e65100;
    class P0 active
    class C3,C12,C13 sat
```

⭐ = the chapters closest to **satellite comms** (modulation, optimal filtering, detection) — your motivation checkpoints.

**Read the map this way:** P0 is the root everything grows from. The book then splits into two trunks — a *deterministic* one (Ch 1–6, how signals and systems behave) and a *stochastic* one (Ch 7–13, how to make decisions under noise) — which finally rejoin at detection (Ch 13).

---

## 3. The recommended single track — just follow the numbers

Dependencies allow some branching, but you don't need to think about that. Follow this order top to bottom. Each ⟶ gate is a quiz in [[Score Log]] you must pass (≥ 80%) to continue.

```mermaid
flowchart TD
    S0["① P0 · Math Toolkit ▶"] --> G0{{"GATE: P0 quiz"}}
    G0 --> S1["② P1 · Linear Algebra"]
    S1 --> S2["③ P2 · Calculus &amp; Diff Eq"]
    S2 --> S3["④ P3 · Signals &amp; Systems"]
    S3 --> S4["⑤ P4 · Probability"]
    S4 --> GF{{"FOUNDATIONS COMPLETE"}}
    GF --> B1["⑥ Ch1 → ⑦ Ch2 → ⑧ Ch3 ⭐"]
    B1 --> B2["⑨ Ch4 → ⑩ Ch5 → ⑪ Ch6"]
    B2 --> B3["⑫ Ch7 → ⑬ Ch8 → ⑭ Ch9"]
    B3 --> B4["⑮ Ch10 → ⑯ Ch11"]
    B4 --> B5["⑰ Ch12 ⭐ → ⑱ Ch13 ⭐"]
    B5 --> DONE["🎓 Expert fluency"]
    style S0 fill:#2e7d32,color:#fff
    style DONE fill:#ef6c00,color:#fff
```

| # | Step | Module | Why it comes here |
|---|------|--------|-------------------|
| ① | **Foundations** | [[Complex Numbers]] · [[Euler's Formula]] · [[Sinusoids And Phasors]] (P0) | The language of every wave. **← current** |
| ② | | [[Linear Algebra Essentials]] (P1) | Vectors/eigenvalues — needed for state-space & estimation |
| ③ | | [[Calculus And Differential Equations]] (P2) | How systems evolve in time |
| ④ | | [[Signals And Systems Fundamentals]] (P3) | LTI, convolution, Fourier — the first named prerequisite |
| ⑤ | | [[Probability Fundamentals]] (P4) | Randomness — the second named prerequisite |
| ⑥–⑧ | **Book: deterministic** | Ch 1–3 | Describe signals → modulation (PAM ⭐) |
| ⑨–⑪ | | Ch 4–6 | State-space modeling & control |
| ⑫–⑭ | **Book: inference** | Ch 7–9 | Probability models → estimation → decisions |
| ⑮–⑯ | | Ch 10–11 | Random processes & their spectra |
| ⑰–⑱ | | Ch 12–13 | Optimal filtering ⭐ & detection ⭐ — the satellite-receiver payoff |

> **Pacing note.** Foundations (①–⑤) are ~60% of the total effort but unlock everything. P4 (probability) is an independent track — if you ever stall on the deterministic math, you can pull P4 forward without breaking dependencies.

---

## 4. How to use this page

- Keep this open while studying; glance at the **dependency map** whenever you wonder "why am I learning this?"
- After each module, take its quiz; I log the score in [[Score Log]] and flip the node ▶ → ✅ here and in [[Curriculum]].
- The ⭐ chapters are where this all becomes *satellite communications* — aim for them.

**Next action:** finish reading the three P0 pages, then say *"I'm ready for the P0 quiz."*
