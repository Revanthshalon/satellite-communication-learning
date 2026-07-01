---
tags: [math-foundations, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
refined: [2026-06-30]
---

# Linear Algebra Essentials

> **Module P1 hub.** 📘 Built — **locked until [[Quiz P0 Math Toolkit]] is passed** (the strict gate stands). Needs [[Complex Numbers]]. Feeds the state-space chapters (4–6) and the estimation chapters (8, 12). Part of [[Curriculum]] · [[Learning Path]].

Linear algebra is the **bookkeeping of many numbers at once**. In this book a system's whole condition is a *vector*, its dynamics are a *matrix*, and its natural behaviors are that matrix's *eigenvalues*. Master those three and Chapters 4–6 become readable.

## The three pages of P1 (study in order)

1. **[[Vectors And Dot Products]]** — vectors as arrows/data; addition, scaling; the dot product and its disguises (length, angle, **orthogonality**, projection). The geometry behind correlation and least-squares.
2. **[[Matrices And Linear Transformations]]** — a matrix as a *machine that transforms vectors*; matrix–vector and matrix–matrix products, identity, inverse, determinant; independence, span, basis, rank.
3. **[[Eigenvalues And Eigenvectors]]** — the directions a matrix only *scales*; characteristic equation $\det(\lambda I-A)=0$, complex eigenvalues ⇒ oscillation, diagonalization $A=V\Lambda V^{-1}$ and **modal decomposition** (the engine of Chapter 5).

## Why P1 matters for satellite comms

The state of a receiver's tracking loop, the dynamics of a satellite's attitude, and the optimal-estimation math of Chapters 8 & 12 are all linear algebra. Eigenvalues decide whether a control loop is **stable** or rings; projection (dot products) decides the **best estimate** of a signal buried in noise.

## Where each idea reappears in the book

| P1 idea | Shows up as | Book location |
|---------|-------------|---------------|
| Dot product / orthogonality | Correlation, uncorrelated ⇔ orthogonal | Ch 7–8 |
| Projection | Least-squares / LMMSE estimation | Ch 8, 12 |
| Matrix as dynamics ($A$) | State-space model $\dot{\mathbf{x}}=A\mathbf{x}+B\mathbf{u}$ | Ch 4 |
| Eigenvalues / modes | Natural frequencies, stability, ZIR | Ch 5 |
| Eigenvalue placement | Observer & feedback design | Ch 6 |

## Practice & Checkpoint

Drill first with **[[Problems P1 Linear Algebra]]** — an open-book L1→L4 ladder (mechanics → operations → structure → applied); every solution you share runs through the [[Remediation Loop]]. Then the strict gate: **[[Quiz P1 Linear Algebra]]** (100 pts, pass ≥ 80%). Passing unlocks **P2 [[Calculus And Differential Equations]]** in [[Curriculum]]. Scores logged in [[Score Log]].

## My Understanding

_(Your space — after the three pages, summarize "vector / matrix / eigenvalue" in one sentence each.)_

## Open Questions

- [ ] _Raised on the sub-pages; collected here and in [[Learning Log]]._
