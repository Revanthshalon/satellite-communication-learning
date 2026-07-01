---
tags: [learning-progress, curriculum, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
refined: [2026-06-30]
---

# Curriculum

The master learning roadmap for [[Signals, Systems And Inference]], built for a learner starting from zero and aiming for expert fluency. Teaching style: **intuition first, then full rigor** (nothing hand-waved). For the visual version (dependency map + recommended track), see [[Learning Path]].

**How progression works:** each module is `🔒 locked`, `▶ active`, or `✅ passed`. You unlock the next module by passing its checkpoint quiz at **≥ 80%** under the strict rubric in [[Score Log]]. Modules build on each other — the dependency arrows are real, not decorative.

```
P0 Math Toolkit ─► P1 Linear Algebra ─┐
       │                              ├─► P3 Signals & Systems ─► Ch 1–3, 10–13
       └──────────► P2 Calc & Diff Eq ┘            │
                          │                        ▼
                          └──► P4 Probability ─► Ch 7–13
                                   (also feeds Ch 4–6 via P1)
```

## Phase 0 — Prerequisites (the "strict prep")

| # | Module | Status | Contents | Checkpoint |
|---|--------|--------|----------|-----------|
| P0 | [[Complex Numbers]], [[Euler's Formula]], [[Sinusoids And Phasors]] | ▶ active | Imaginary unit `j`, complex plane, polar form, magnitude/phase, Euler's identity, sinusoids as rotating phasors | Drills: [[Problems P0 Math Toolkit]] → Gate: [[Quiz P0 Math Toolkit]] |
| P1 | [[Linear Algebra Essentials]] → [[Vectors And Dot Products]], [[Matrices And Linear Transformations]], [[Eigenvalues And Eigenvectors]] | 📘 built · locked until P0 passed | Vectors, dot product, orthogonality, projection; matrices as transformations, determinant, independence/span/basis/rank; eigenvalues/eigenvectors, characteristic equation, diagonalization & modes | Drills: [[Problems P1 Linear Algebra]] → Gate: [[Quiz P1 Linear Algebra]] |
| P2 | [[Calculus And Differential Equations]] → [[Derivatives And Integrals]], [[Differential Equations]] | 📘 built · locked until P1 passed | Derivatives, integrals, FTC, the exponential `e^{at}`; 1st/2nd-order linear ODEs, characteristic equation, damping, complex roots ⇒ oscillation, left-half-plane stability, why `e^{st}` solves them | Drills: [[Problems P2 Calculus And Differential Equations]] → Gate: [[Quiz P2 Calculus And Differential Equations]] |
| P3 | [[Signals And Systems Fundamentals]] | 🔒 locked | Signals, LTI systems, impulse response, convolution, frequency response, the Fourier transform, sampling | _to build_ |
| P4 | [[Probability Fundamentals]] | 🔒 locked | Sample spaces, conditional probability, Bayes' rule, random variables, pdf/pmf, expectation, variance, Gaussian | _to build_ |

## Phase 1 — The Book (Chapters 1–13)

Built after the prerequisites that each chapter needs are passed. Each becomes its own concept/synthesis page with the same teaching format + checkpoint.

| Ch | Topic | Needs | Status |
|----|-------|-------|--------|
| 1 | Signals and Systems | P0, P3 | 🔒 |
| 2 | Amplitude, Phase, and Group Delay | P0, P3 | 🔒 |
| 3 | Pulse-Amplitude Modulation (PAM) | Ch 1–2 | 🔒 |
| 4 | State-Space Models | P1, P2 | 🔒 |
| 5 | LTI State-Space Models | Ch 4, P1 | 🔒 |
| 6 | State Observers and State Feedback | Ch 5 | 🔒 |
| 7 | Probabilistic Models | P4 | 🔒 |
| 8 | Estimation | Ch 7 | 🔒 |
| 9 | Hypothesis Testing | Ch 7–8 | 🔒 |
| 10 | Random Processes | Ch 7, P3 | 🔒 |
| 11 | Power Spectral Density | Ch 10 | 🔒 |
| 12 | Signal Estimation (Wiener / Kalman) | Ch 8, 10–11 | 🔒 |
| 13 | Signal Detection (matched filtering) | Ch 9, 13 prereqs | 🔒 |

## Teaching format for every concept page

1. **Intuition** — plain language + analogy, no symbols yet
2. **Math** — built from scratch, every symbol defined, units stated
3. **Terms experts use** — the vocabulary, defined the way a pro uses it
4. **Worked example** — numbers all the way through
5. **Problem set (progressive drills)** — a module-level `Problems …` page with a rising-complexity ladder (**L1** mechanics → **L2** operations → **L3** structure → **L4** applied/satcom) for every topic. Open-book, formative; worked before the gate quiz.
6. **Checkpoint** — strict closed-book quiz; score logged in [[Score Log]]
7. **My Understanding** / **Open Questions** — your space; landing spots for [[Learning Log]] updates

**Reinforcement loop.** Every shared solution (drill, quiz, or discussion) runs through the [[Remediation Loop]]: I classify the error (conceptual / procedural / definitional / transfer), name the misconception, re-explain from a deeper angle, and hand you a twin problem. Named weaknesses are tracked in [[Learning Log]] and hold back mastery until their twin is passed. **Study order per module: read pages → work the problem set → sit the gate quiz.**

## Standard module build checklist

Every `build <module>` produces, at minimum:

- [ ] Concept page(s) in the teaching format above (hub + sub-pages when the module is broad)
- [ ] A **problem set** `Problems <Module>` with the L1→L4 complexity ladder + hidden worked-solution key
- [ ] A strict **gate quiz** `Quiz <Module>` (100 pts, ≥ 80% to advance) with hidden answer key
- [ ] [[Remediation Loop]] hooks wired in (problem set + quiz both reference it)
- [ ] Updated [[Learning Log]] (mastery rows + Weakness Log), [[Score Log]], `index`, `log`, and the [[Learning Path]] node

## Session pointer

- **2026-06-30** — Infra built. P0 concept pages complete. **P1 built out fully** (3 concept pages + [[Quiz P1 Linear Algebra]]), grounded in the book's Chapter 5 eigenvalue example; remains gated behind the P0 quiz. P2–P4 + Ch 1–13 are skeleton entries above, ready to build in later sessions. **Next action: take [[Quiz P0 Math Toolkit]].**
- **2026-07-01** — **P2 built out fully** (hub + 2 concept pages: [[Derivatives And Integrals]], [[Differential Equations]] + [[Quiz P2 Calculus And Differential Equations]]). Explicitly linked to P0/P1: `d/dt e^{at}=a e^{at}` = the phasor rule, and the ODE characteristic equation = the eigenvalue equation. Gated behind the P1 quiz. P3–P4 + Ch 1–13 remain skeletons.
- **2026-07-01** — **Reinforcement layer added.** Progressive problem sets ([[Problems P0 Math Toolkit]], [[Problems P1 Linear Algebra]], [[Problems P2 Calculus And Differential Equations]]) with an L1→L4 complexity ladder, plus the [[Remediation Loop]] (weakness diagnosis + deeper re-teach on every miss). Baked into the teaching format and the *standard module build checklist* above, so all future modules ship with drills by default. **Next action: still [[Quiz P0 Math Toolkit]] — but warm up on [[Problems P0 Math Toolkit]] first; the gates are strict and sequential.**
