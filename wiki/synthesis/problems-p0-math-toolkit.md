---
tags: [learning-progress, assessment, math-foundations, signal-processing]
sources: [discussion-2026-07-01]
created: 2026-07-01
updated: 2026-07-01
---

# Problems P0 Math Toolkit

Progressive drill set for Module P0: [[Complex Numbers]] · [[Euler's Formula]] · [[Sinusoids And Phasors]]. **Formative, open-book** — work these to *build* the skill before the closed-book gate [[Quiz P0 Math Toolkit]]. Share each solution and I run the [[Remediation Loop]] on every miss (name the weakness → deeper re-explanation → twin problem). Weaknesses logged in [[Learning Log]].

**Complexity ladder (per topic):** **L1** mechanics → **L2** operations → **L3** structure/rotation → **L4** applied (satellite-comms flavored). Do them in order; each L builds on the last.

## A · Complex Numbers

- **A1 (L1).** For $z = 3 + 4j$: find (a) $z^*$, (b) $|z|$, (c) the angle $\theta$ in degrees, (d) the polar form $re^{j\theta}$.
- **A2 (L2).** Compute in rectangular form: (a) $(2+j)(1-3j)$, (b) $\dfrac{2+j}{1-3j}$ (multiply by the conjugate).
- **A3 (L3).** For $z=-1+j\sqrt3$: (a) write it in polar form; (b) describe geometrically what multiplying by $j$ does to it; (c) compute $z^6$.
- **A4 (L4).** Find **all three** cube roots of $8j$; give each in polar and rectangular form, and verify they sum to zero.

## B · Euler's Formula

- **B1 (L1).** Evaluate $e^{j\pi/3}$ in rectangular form.
- **B2 (L2).** Using $e^{j2\theta}=(e^{j\theta})^2$, derive the double-angle identities for $\cos 2\theta$ and $\sin 2\theta$.
- **B3 (L3).** Compute $(\sqrt3 + j)^5$ via Euler form; give a rectangular final answer.
- **B4 (L4).** Prove $\cos^3\theta = \tfrac{1}{4}(3\cos\theta + \cos 3\theta)$ using the inverse-Euler relation. (This is *why* a nonlinearity generates harmonics — the seed of intermodulation in RF.)

## C · Sinusoids & Phasors

- **C1 (L1).** For $x(t)=5\cos(2\pi\cdot 1000\,t + \tfrac{\pi}{4})$ give, with units: $A,\ f,\ \omega,\ T,\ \phi$ (deg), and the phasor $X$.
- **C2 (L2).** Combine $x(t)=3\cos\omega t - 4\sin\omega t$ into a single $A\cos(\omega t+\phi)$ using phasors; verify by expanding your answer back.
- **C3 (L3).** With $X = 2\angle 30^\circ$ and $\omega=100$ rad/s, find the phasor of $\dfrac{dx}{dt}$ and of $\int x\,dt$. State in words what each does to magnitude and phase.
- **C4 (L4 — multipath fade).** A direct and a reflected ray, equal amplitude $A$, same frequency, arrive with relative phase $\phi$: $y(t)=A\cos\omega t + A\cos(\omega t+\phi)$. (a) Find the resultant amplitude $R(\phi)$; (b) which $\phi$ gives the constructive peak and which the destructive **null (deep fade)**; (c) evaluate $R$ at $\phi=120^\circ$.

---

<!-- ============================ SOLUTION KEY (hidden in rendered view) — I grade + run the Remediation Loop ============================
A1: z*=3-4j; |z|=√(9+16)=5; θ=atan2(4,3)=53.13°; polar 5 e^{j53.13°}.
A2: (a) (2+j)(1-3j)=2-6j+j-3j²=2-5j+3=5-5j. (b) ×(1+3j)/(1+3j): num=(2+j)(1+3j)=2+6j+j-3=-1+7j; den=1+9=10 → -0.1+0.7j.
A3: |z|=√(1+3)=2, angle in Q2 = atan2(√3,-1)=120° → 2 e^{j120°}. (b) ×j = ×e^{j90°} rotates +90° (mag unchanged) → 2 e^{j210°}. (c) z^6 = 2^6 e^{j720°}=64 e^{j0}=64.
A4: 8j = 8 e^{j90°}. Cube roots: mag=2, angles (90+360k)/3 = 30°,150°,270°. → 2e^{j30}=√3+j ; 2e^{j150}=-√3+j ; 2e^{j270}=-2j. Sum: (√3-√3)+(j+j-2j)=0 ✓ (no s² term ⇒ roots sum to 0).
B1: cos60°+j sin60° = 1/2 + j√3/2.
B2: e^{j2θ}=(cosθ+j sinθ)² = (cos²θ-sin²θ) + j(2 sinθ cosθ). Also = cos2θ + j sin2θ. Match: cos2θ=cos²θ-sin²θ, sin2θ=2 sinθ cosθ.
B3: √3+j = 2 e^{j30°}. ^5 = 32 e^{j150°} = 32(-√3/2 + j/2) = -16√3 + 16j.
B4: cos³θ=(1/8)(e^{jθ}+e^{-jθ})³ = (1/8)(e^{j3θ}+3e^{jθ}+3e^{-jθ}+e^{-j3θ}) = (1/8)(2cos3θ + 6cosθ) = (3cosθ+cos3θ)/4.
C1: A=5 (signal units); f=1000 Hz; ω=2π·1000=2000π≈6283 rad/s; T=1/1000=1 ms; φ=45°; X=5 e^{j45°}=5∠45° ≈ 3.54+3.54j. (-1 per missing unit, per rubric.)
C2: 3cosωt→3∠0=3. sin ωt=cos(ωt-90°)→1∠-90°=-j, so -4sinωt→-4(-j)=4j. Wait sign: -4·(-j)=+4j. X=3+4j. A=|X|=5, φ=atan2(4,3)=53.13°. x=5cos(ωt+53.13°). Check: 5[cosφ cosωt - sinφ sinωt]=5[0.6cos -0.8 sin]=3cos-4sin ✓.
C3: d/dt → ×jω: phasor jωX = 100·2 e^{j(30+90)}=200 e^{j120°} (scales by ω=100, +90° phase). ∫ → ÷jω: X/(jω)=0.02 e^{-j60°} (scales by 1/ω, -90° phase).
C4: X=A+A e^{jφ}=A·2cos(φ/2)e^{jφ/2}. R=2A|cos(φ/2)|. (b) max 2A at φ=0 (constructive); null 0 at φ=180° (deep fade). (c) φ=120° → R=2A|cos60°|=2A(0.5)=A.
Remediation cues by error: magnitudes-add-instead-of-multiply → conceptual, revisit [[Complex Numbers]] "why multiplication rotates"; dropped units in C1 → definitional; sin→phasor sign flip in C2 → procedural; missed 2cos(φ/2) factoring in C4 → transfer (didn't reuse inverse-Euler from B).
========================================================================================================= -->
