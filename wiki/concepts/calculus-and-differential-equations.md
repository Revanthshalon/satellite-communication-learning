---
tags: [math-foundations, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-07-01
refined: [2026-07-01]
---

# Calculus And Differential Equations

> **Module P2 hub.** 📘 Built — **locked until [[Quiz P1 Linear Algebra]] is passed** (the strict single-track gate stands). Needs [[Complex Numbers]], [[Euler's Formula]], [[Sinusoids And Phasors]]. Feeds the state-space chapters (4–6) and every continuous-time system in the book. Part of [[Curriculum]] · [[Learning Path]].

Calculus is the **language of change over time**, and a differential equation is **how a system states its own law of motion**. In this book a signal is a function of time, a system's rule is a differential equation, and the exponential $e^{st}$ is the one function that makes those rules solvable by algebra. Master the derivative, the integral, and the linear ODE and Chapters 4–6 (state-space, dynamics, control) become readable.

## The two pages of P2 (study in order)

1. **[[Derivatives And Integrals]]** — the derivative as *instantaneous rate* (slope) and the integral as *accumulated area*; the rules; the Fundamental Theorem tying them together; and the one law that runs the whole book, $\frac{d}{dt}e^{at}=a\,e^{at}$.
2. **[[Differential Equations]]** — equations relating a quantity to its own rate; the $e^{st}$ guess that turns $d/dt$ into "multiply by $s$"; first- and second-order linear ODEs; the **characteristic equation** (the twin of the eigenvalue equation); damping, natural frequencies, and the left-half-plane **stability** rule; the bridge to the Laplace transform.

## Why P2 matters for satellite comms

Every continuous-time system — a receiver's loop filter, a satellite's attitude dynamics, an oscillator, an antenna servo — is written as a differential equation. Whether that loop **locks or oscillates**, how fast it **settles** (time constant), and at what frequency it **rings** are all read straight off the characteristic roots. P2 is the calculus that turns [[Linear Algebra Essentials|linear algebra]]'s static picture into motion: $\dot{\mathbf{x}}=A\mathbf{x}$ says "the eigenvalues of $A$ are the exponents $e^{\lambda t}$ the system moves along."

## Where each idea reappears in the book

| P2 idea | Shows up as | Book location |
|---------|-------------|---------------|
| Derivative $d/dt$ | Continuous-time system operator; $\dot{\mathbf{x}}=A\mathbf{x}+B\mathbf{u}$ | Ch 4 |
| $\frac{d}{dt}e^{at}=ae^{at}$ | Exponential as the natural mode / eigenfunction | Ch 4–5 |
| Characteristic equation | Natural frequencies, ZIR, stability | Ch 5 |
| Complex root $s=\sigma\pm j\omega$ | Decaying oscillation, damping, resonance | Ch 5–6 |
| Left-half-plane rule | Asymptotic stability criterion | Ch 5–6 |
| $e^{st}$ eigenfunction / $d/dt\to s$ | Laplace transform, transfer functions | Ch 2, 5 |

## Checkpoint

Strict gate: **[[Quiz P2 Calculus And Differential Equations]]** (100 pts, pass ≥ 80%). Passing unlocks **P3 [[Signals And Systems Fundamentals]]** in [[Curriculum]]. Scores logged in [[Score Log]].

## My Understanding

_(Your space — after the two pages, summarize in one sentence each: derivative, integral, and "what the roots of the characteristic equation tell you.")_

## Open Questions

- [ ] _Raised on the sub-pages; collected here and in [[Learning Log]]._
