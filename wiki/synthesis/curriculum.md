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
| P0 | [[Complex Numbers]], [[Euler's Formula]], [[Sinusoids And Phasors]] | ▶ active | Imaginary unit `j`, complex plane, polar form, magnitude/phase, Euler's identity, sinusoids as rotating phasors | [[Quiz P0 Math Toolkit]] |
| P1 | [[Linear Algebra Essentials]] → [[Vectors And Dot Products]], [[Matrices And Linear Transformations]], [[Eigenvalues And Eigenvectors]] | 📘 built · locked until P0 passed | Vectors, dot product, orthogonality, projection; matrices as transformations, determinant, independence/span/basis/rank; eigenvalues/eigenvectors, characteristic equation, diagonalization & modes | [[Quiz P1 Linear Algebra]] |
| P2 | [[Calculus And Differential Equations]] → [[Derivatives And Integrals]], [[Differential Equations]] | 📘 built · locked until P1 passed | Derivatives, integrals, FTC, the exponential `e^{at}`; 1st/2nd-order linear ODEs, characteristic equation, damping, complex roots ⇒ oscillation, left-half-plane stability, why `e^{st}` solves them | [[Quiz P2 Calculus And Differential Equations]] |
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
5. **Checkpoint** — strict quiz; score logged in [[Score Log]]
6. **My Understanding** / **Open Questions** — your space; landing spots for [[Learning Log]] updates

## Session pointer

- **2026-06-30** — Infra built. P0 concept pages complete. **P1 built out fully** (3 concept pages + [[Quiz P1 Linear Algebra]]), grounded in the book's Chapter 5 eigenvalue example; remains gated behind the P0 quiz. P2–P4 + Ch 1–13 are skeleton entries above, ready to build in later sessions. **Next action: take [[Quiz P0 Math Toolkit]].**
- **2026-07-01** — **P2 built out fully** (hub + 2 concept pages: [[Derivatives And Integrals]], [[Differential Equations]] + [[Quiz P2 Calculus And Differential Equations]]). Explicitly linked to P0/P1: `d/dt e^{at}=a e^{at}` = the phasor rule, and the ODE characteristic equation = the eigenvalue equation. Gated behind the P1 quiz. P3–P4 + Ch 1–13 remain skeletons. **Next action: still [[Quiz P0 Math Toolkit]] — the gates are strict and sequential.**
