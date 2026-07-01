---
tags: [learning-progress, assessment, math-foundations]
sources: [discussion-2026-07-01]
created: 2026-07-01
updated: 2026-07-01
---

# Problems P2 Calculus And Differential Equations

Progressive drill set for Module P2: [[Derivatives And Integrals]] · [[Differential Equations]]. **Formative, open-book** — build skill before the closed-book gate [[Quiz P2 Calculus And Differential Equations]]. Share each solution; I run the [[Remediation Loop]] on every miss. Weaknesses logged in [[Learning Log]].

**Complexity ladder (per topic):** **L1** mechanics → **L2** operations → **L3** structure → **L4** applied (satellite-comms / control flavored).

## A · Derivatives & Integrals

- **A1 (L1).** Differentiate (a) $4t^3-2t^2+t$, (b) $e^{-5t}$, (c) $\sin(3t)$.
- **A2 (L2).** Differentiate $x(t)=e^{-t}\cos(2t)$ (product + chain rule).
- **A3 (L3).** Compute (a) $\int_0^\infty e^{-2t}\,dt$ and (b) $\int_0^\infty e^{-2t}\cos t\,dt$ (hint: take the real part of $\int_0^\infty e^{(-2+j)t}dt$).
- **A4 (L4 — pulse energy).** A decaying pulse $x(t)=e^{-t/\tau}$ for $t\ge 0$. Compute its energy $E=\int_0^\infty x^2\,dt$ in terms of $\tau$, and say what a longer $\tau$ does to the energy.

## B · First-Order ODEs

- **B1 (L1).** Solve $\dot x=-5x$, $x(0)=10$. Give $x(t)$, the time constant $\tau$ (with units), and the stability verdict.
- **B2 (L2).** Step response: $\tau\dot x + x = K\,u(t)$ with a unit step $u=1$ and $x(0)=0$. Find $x(t)$ and the steady-state value. At what time is $x$ at 63% of final?
- **B3 (L3 — RC circuit).** $RC\,\dot v + v = V_\text{in}$, step $V_\text{in}=5$ V, $R=1\,\text{k}\Omega$, $C=1\,\mu\text{F}$, $v(0)=0$. Find $\tau$, $v(t)$, and $v$ at $t=1$ ms.

## C · Second-Order ODEs

- **C1 (L1).** For $\ddot x+7\dot x+12x=0$: write the characteristic equation, find the roots, and name the damping regime.
- **C2 (L2).** Solve $\ddot x+2\dot x+5x=0$ with $x(0)=1,\ \dot x(0)=0$.
- **C3 (L3).** For $\ddot x+2\zeta\omega_n\dot x+\omega_n^2x=0$ with $\omega_n=4$ rad/s, $\zeta=0.25$: find the roots, the damped frequency $\omega_d$, the envelope time constant, and the stability verdict.
- **C4 (L4 — phase-locked loop).** A 2nd-order PLL has $\omega_n=2\pi\cdot100$ rad/s and $\zeta=0.707$. (a) Find the roots; (b) is the loop stable and why; (c) describe the step (phase-error) response qualitatively; (d) what would $\zeta<0$ physically mean for the loop?

---

<!-- ============================ SOLUTION KEY (hidden) — I grade + run the Remediation Loop ============================
A1: (a) 12t²-4t+1. (b) -5 e^{-5t}. (c) 3 cos(3t).
A2: x' = -e^{-t}cos2t + e^{-t}(-2 sin2t) = -e^{-t}(cos2t + 2 sin2t).
A3: (a) [-(1/2)e^{-2t}]_0^∞ = 0-(-1/2)=1/2. (b) ∫_0^∞ e^{(-2+j)t}dt = [e^{(-2+j)t}/(-2+j)]_0^∞ = (0-1)/(-2+j)=1/(2-j)=(2+j)/5. Re = 2/5 = 0.4.
A4: ∫_0^∞ e^{-2t/τ}dt = τ/2. So E=τ/2. Longer τ (slower decay) ⇒ more energy — links to signal energy in the link budget.
B1: guess e^{st}: s=-5. x(t)=10 e^{-5t}. τ=1/5=0.2 s. Stable (a=-5<0).
B2: homog e^{-t/τ}, particular x_p=K. x=K+Ce^{-t/τ}; x(0)=0 → C=-K. x(t)=K(1-e^{-t/τ}). SS = K. 63% of final at t=τ.
B3: τ=RC=(1e3)(1e-6)=1e-3 s = 1 ms. v(t)=5(1-e^{-t/1ms}). At t=1ms: 5(1-e^{-1})=5(0.632)=3.16 V.
C1: s²+7s+12=(s+3)(s+4) → s=-3,-4. Two real negative → overdamped, stable.
C2: s²+2s+5=0 → s=-1±2j. x=e^{-t}(C1 cos2t+C2 sin2t). x(0)=C1=1. ẋ(0): derivative at 0 = -C1+2C2=0 → C2=0.5. x(t)=e^{-t}(cos2t+0.5 sin2t).
C3: 2ζω_n=2, ω_n²=16. s=-ζω_n ± jω_n√(1-ζ²)= -1 ± j·4√(0.9375)= -1 ± j3.873. ω_d≈3.873 rad/s. envelope e^{-t}, τ=1 s. Re s=-1<0 → stable, underdamped.
C4: ω_n=2π·100≈628.3. ζω_n=444.3; ω_n√(1-0.5)=628.3·0.707=444.3. s=-444.3 ± 444.3j. (b) stable, both Re<0 (LHP). (c) ζ=0.707 = maximally-flat: small overshoot then quick settle. (d) ζ<0 → Re s>0 → growing oscillation → loop unstable, never locks.
Remediation cues: chain rule dropped inner derivative (A2) → procedural; integrated e^{at} as a e^{at} not (1/a) (A3/B) → conceptual, revisit [[Derivatives And Integrals]] antiderivatives; used ω_n instead of ω_d for the ring (C3) → definitional; read complex roots as unstable (C4) → conceptual, it's Re{s}<0 that decides, revisit [[Differential Equations]] LHP rule; forgot units on τ → definitional.
========================================================================================================= -->
