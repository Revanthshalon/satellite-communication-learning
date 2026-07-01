---
tags: [math-foundations, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-07-01
updated: 2026-07-01
---

# Differential Equations

> **Module P2 · Page 2 of 2.** Needs [[Derivatives And Integrals]], [[Euler's Formula]], [[Sinusoids And Phasors]], [[Eigenvalues And Eigenvectors]]. Completes P2 → take [[Quiz P2 Calculus And Differential Equations]]. Part of [[Calculus And Differential Equations]] · [[Curriculum]] · [[Learning Path]].

## Intuition

A **differential equation** (DE) is an equation that relates a quantity to *its own rate of change*. Instead of telling you the answer $x(t)$ directly, it tells you a **rule the answer must obey at every instant**:

> "the rate at which the population grows is proportional to the population itself" → $\dot x = a x$.

This is how nature states its laws — a capacitor voltage, a satellite's tumble, a tracking loop's error — because a system doesn't know its future, it only knows *the rule connecting where it is now to how fast it's moving now.* Solving the DE means turning that local rule into the global trajectory.

The punchline of the whole page: because the exponential is the one function whose derivative is a copy of itself ($\frac{d}{dt}e^{st}=s\,e^{st}$ from [[Derivatives And Integrals]]), **guessing $x=e^{st}$ turns any linear DE into an algebra problem** — the derivatives all become powers of $s$, and you just solve a polynomial. The roots $s$ are the system's **natural frequencies**; they are the continuous-time twin of the [[Eigenvalues And Eigenvectors|eigenvalues]] from P1, and the sign of their real part decides **stability**. This one idea is the engine of the book's Chapters 4–6.

## Math

### First-order linear ODE — the atom of the subject

The simplest and most important DE:

$$\dot x(t) = a\,x(t), \qquad x(0) = x_0.$$

"The rate is $a$ times the current value." Guess the exponential $x=e^{st}$; substitute using $\dot x = s e^{st}$:

$$s\,e^{st} = a\,e^{st} \;\Longrightarrow\; s = a.$$

So the solution is the **exponential**, scaled to hit the initial condition:

$$\boxed{\,x(t) = x_0\,e^{at}\,}$$

Read off the behavior from the single number $a$ (units: **1/seconds**, a rate):

- $a<0$: **decay**. Write $a=-1/\tau$; then $x=x_0 e^{-t/\tau}$ and $\tau$ is the **time constant** — the time to fall to $1/e\approx 37\%$. **Stable.**
- $a>0$: **growth** — runaway, **unstable** (the inverted pendulum's tipping mode in [[Eigenvalues And Eigenvectors]]).
- $a=0$: constant, marginal.

### Forced first-order ODE — input drives the system

Add an input $u(t)$:

$$\dot x = a x + b u.$$

The full solution splits into two physically distinct pieces (the book's language):

- **Zero-input response (ZIR):** what the initial condition does on its own, $x_0 e^{at}$ — the **homogeneous** solution / **transient**.
- **Zero-state response (ZSR):** what the input does starting from rest — the **particular** solution, computed by the convolution integral $\int_0^t e^{a(t-\tau)} b\,u(\tau)\,d\tau$.

**Total = homogeneous + particular = transient + steady-state.** This decomposition is exactly how [[Signals And Systems Fundamentals|LTI systems]] and the state-space models of Chapter 4 are analyzed.

### Second-order linear ODE — and the characteristic equation

A mass–spring–damper, an RLC circuit, any resonant thing:

$$\ddot x + 2\zeta\omega_n\,\dot x + \omega_n^2\,x = 0.$$

Same move — guess $x=e^{st}$, so $\dot x\to s e^{st}$, $\ddot x\to s^2 e^{st}$. Every term carries $e^{st}$; cancel it and a **polynomial in $s$** remains — the **characteristic equation**:

$$s^2 + 2\zeta\omega_n s + \omega_n^2 = 0.$$

This is the *same object* as $\det(\lambda I - A)=0$ from [[Eigenvalues And Eigenvectors]] — differentiation "$d/dt$" has become "multiply by $s$," turning calculus into algebra. Its two roots $s_{1,2}$ are the **natural frequencies / modes**, and the general solution is their superposition:

$$x(t) = C_1 e^{s_1 t} + C_2 e^{s_2 t},$$

with $C_1,C_2$ fixed by the two initial conditions $x(0),\dot x(0)$. The roots

$$s = -\zeta\omega_n \pm \omega_n\sqrt{\zeta^2-1}$$

tell the story through the **damping ratio** $\zeta$:

| Case | Roots | Behavior |
|------|-------|----------|
| $\zeta>1$ **overdamped** | two real negative | decays, no oscillation |
| $\zeta=1$ **critically damped** | real repeated | fastest non-oscillating decay |
| $0<\zeta<1$ **underdamped** | complex pair $-\sigma\pm j\omega_d$ | **decaying oscillation** |
| $\zeta=0$ undamped | $\pm j\omega_n$ | pure sinusoid, rings forever |

### Why complex roots mean oscillation — the P0/P1 payoff

When the roots are a complex pair $s=\sigma\pm j\omega_d$, plug into $e^{st}$ and expand with [[Euler's Formula]]:

$$e^{(\sigma\pm j\omega_d)t} = e^{\sigma t}\big(\cos\omega_d t \pm j\sin\omega_d t\big).$$

A real solution is the sum of the conjugate pair, giving

$$x(t) = e^{\sigma t}\big(C_1\cos\omega_d t + C_2\sin\omega_d t\big) = R\,e^{\sigma t}\cos(\omega_d t + \phi).$$

An **envelope** $e^{\sigma t}$ times a **sinusoid** at the **damped natural frequency** $\omega_d$. The real part $\sigma$ sets growth/decay (the phasor whose amplitude changes — the very [[Sinusoids And Phasors|open question P0 left you]]); the imaginary part $\omega_d$ sets how fast it rings. **Eigenvalues/roots in the left half-plane ⇒ decay ⇒ stable.**

### The complex frequency $s$ and the bridge to Laplace

The exponent $s=\sigma + j\omega$ is the **complex frequency**: $\sigma$ (nepers/s) is the growth/decay rate, $\omega$ (rad/s) is the oscillation rate. A pure imaginary $s=j\omega$ recovers the steady sinusoid of [[Sinusoids And Phasors]] — "on the imaginary axis" = "on the [[Euler's Formula|unit circle]] of no growth." Because feeding $e^{st}$ into a linear system just multiplies it by a number (the exponential is an **eigenfunction**), engineers transform every DE into the $s$-domain — the **Laplace transform** — where $d/dt\to s$ turns calculus into algebra permanently. The book uses this to move between state-space models and transfer functions; you'll meet it fully in [[Signals And Systems Fundamentals]].

## Terms Experts Use

- **Ordinary differential equation (ODE)** — a DE in one variable (time); **order** = highest derivative present.
- **Linear / constant-coefficient** — the unknown and its derivatives appear to the first power, coefficients don't depend on $x$; the class this whole course lives in (superposition holds).
- **Homogeneous vs. forced (particular)** — no input vs. input-driven; equivalently **zero-input response (ZIR)** vs. **zero-state response (ZSR)**.
- **Transient vs. steady-state** — the decaying homogeneous part vs. the part that persists.
- **Characteristic equation / characteristic root** — the polynomial in $s$ and its roots; identical idea to the [[Eigenvalues And Eigenvectors|eigenvalue]] $\det(\lambda I-A)=0$.
- **Natural frequency $\omega_n$ · damped frequency $\omega_d$ · damping ratio $\zeta$ · time constant $\tau$.**
- **Complex frequency $s=\sigma+j\omega$** · **eigenfunction** ($e^{st}$) · **Laplace transform** ($d/dt\to s$).
- **Stability read-off:** continuous-time stable ⇔ every root/eigenvalue has $\operatorname{Re}\{s\}<0$ (left half-plane) — the continuous-time twin of $|\lambda|<1$ for discrete time.

## Worked Example

**(1) First order.** A capacitor discharges: $\dot x = -2x$, $x(0)=5$ V.
Guess $e^{st}$ → $s=-2$. So $x(t)=5e^{-2t}$ V. Time constant $\tau = 1/2 = 0.5$ s; at $t=0.5$ s, $x = 5/e \approx 1.84$ V. Rate $a=-2<0$ → **stable decay**. ✓

**(2) Second order.** $\ddot x + 4\dot x + 13x = 0$, i.e. $2\zeta\omega_n=4$, $\omega_n^2=13$ → $\omega_n=\sqrt{13}\approx3.61$ rad/s, $\zeta=2/\sqrt{13}\approx0.555$ (underdamped).
Characteristic equation $s^2+4s+13=0$ → $s = \dfrac{-4\pm\sqrt{16-52}}{2} = -2\pm 3j$.
Via [[Euler's Formula]]: $x(t)=e^{-2t}\big(C_1\cos 3t + C_2\sin 3t\big)$ — a decaying oscillation, envelope $e^{-2t}$, ring frequency $\omega_d=3$ rad/s. $\operatorname{Re}\{s\}=-2<0$ → **stable**. This is the identical $\lambda=-1\pm 2j$ analysis you saw for matrices in [[Eigenvalues And Eigenvectors]] — now you know *where the $e^{\lambda t}$ came from.*

## Checkpoint

Tested in [[Quiz P2 Calculus And Differential Equations]]. Cold, you should be able to:
1. Solve $\dot x = ax$, $x(0)=x_0$ by the $e^{st}$ guess, and read decay/growth and $\tau$ from $a$.
2. Split a forced response into homogeneous (ZIR) + particular (ZSR), transient + steady-state.
3. Write and solve the characteristic equation of a 2nd-order linear ODE.
4. Classify over/critically/underdamped from $\zeta$ (or the roots), and get $\omega_n,\omega_d$.
5. Explain, via [[Euler's Formula]], why complex roots ⇒ decaying oscillation, and state the left-half-plane stability rule.
6. Say why $e^{st}$ is the natural guess and how it links to [[Eigenvalues And Eigenvectors|eigenvalues]] and the Laplace transform.

## My Understanding

_(Your space — the target instinct: "a linear system's behavior is a sum of $e^{s_i t}$ modes; the roots $s_i$ are its DNA, and their real parts decide if it lives or blows up.")_

## Open Questions

- [ ] _e.g. "How do repeated roots ($\zeta=1$) give a $t\,e^{st}$ term?" — the DE analog of a defective matrix; log in [[Learning Log]]._
