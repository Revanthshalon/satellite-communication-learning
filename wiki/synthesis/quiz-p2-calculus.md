---
tags: [learning-progress, assessment, math-foundations]
sources: [discussion-2026-07-01]
created: 2026-07-01
updated: 2026-07-01
---

# Quiz P2 Calculus And Differential Equations

Strict checkpoint for Module P2: [[Derivatives And Integrals]] · [[Differential Equations]]. Graded under the rubric in [[Score Log]] (pass ≥ 80%, no credit for right answer + wrong reasoning, units/definitions count, show your work). Passing unlocks **P3 Signals & Systems** in [[Curriculum]].

**Gate reminder:** P2 is only attempted *after* [[Quiz P1 Linear Algebra]] is passed.

**Format:** 10 questions, 100 points. Closed-book. Tell me *"I'm ready for the P2 quiz"* and answer in chat; I deliver them in 3 batches, grade strictly, and append your row to [[Score Log]].

## Section A — Derivatives & Integrals (30 pts)

1. **(6 pts)** Define the derivative $dx/dt$ as a limit (write the difference quotient). If $x$ is in volts and $t$ in seconds, state the units of $\dot x$ and of $\int x\,dt$.
2. **(8 pts)** Differentiate (a) $x(t)=5t^3 - 2t + 7$, (b) $x(t)=e^{-3t}$, (c) $x(t)=\cos(4t)$. State the one rule that lets you do (a) term by term.
3. **(8 pts)** State the law $\frac{d}{dt}e^{at}=a\,e^{at}$ and explain in one sentence why this function is "special." Then connect it to [[Sinusoids And Phasors]]: what does $a=j\omega$ make the rule become, and why?
4. **(8 pts)** Compute $\int_0^2 (3t^2 + e^{-t})\,dt$. Show the antiderivative and cite the Fundamental Theorem of Calculus step. Explain in one sentence what the "$+C$" of an indefinite integral physically represents.

## Section B — First-Order ODEs (30 pts)

5. **(10 pts)** Solve $\dot x = -4x$, $x(0)=6$. Show the $e^{st}$ guess and how you get $s$. Give the time constant $\tau$ **with units**, and state whether the system is stable and why.
6. **(8 pts)** For $\dot x = ax$, explain what the sign of $a$ decides. Sketch (in words) the three cases $a<0$, $a=0$, $a>0$ and name which is stable.
7. **(12 pts)** For a forced system $\dot x = ax + bu$: define the **zero-input response** and the **zero-state response**, and state which one is the *transient* and which contains the *steady-state*. Why is splitting the solution this way legitimate for a **linear** system (name the property)?

## Section C — Second-Order ODEs & Stability (40 pts)

8. **(18 pts)** For $\ddot x + 6\dot x + 25x = 0$: (a) write the characteristic equation; (b) find both roots $s_{1,2}$; (c) using [[Euler's Formula]], write the real general solution $x(t)$ and identify the envelope and the ring frequency $\omega_d$; (d) state whether the system is stable and the exact criterion you used.
9. **(12 pts)** (a) Define **damping ratio** $\zeta$ and **natural frequency** $\omega_n$. (b) Name the four damping regimes ($\zeta>1$, $=1$, $0<\zeta<1$, $=0$) and the qualitative behavior of each. (c) Which regime does Q8 fall in? Justify from its roots.
10. **(10 pts)** The characteristic equation $s^2+\dots=0$ of an ODE and the eigenvalue equation $\det(\lambda I - A)=0$ of a matrix are "the same object." (a) Explain the correspondence — what operation does "multiply by $s$" replace? (b) State the continuous-time stability rule in terms of the roots/eigenvalues, and contrast it with the discrete-time rule $|\lambda|<1$.

---

_When you're done I total the points, assign a band (A/B/C/D-F), diagnose every miss, and log it. Below ~80% the P3 module stays locked and I'll route you back to the exact sections to redo._

<!-- ============================ GRADER ANSWER KEY (hidden in rendered view) ============================
Total 100. Strict: correct final value from flawed reasoning = 0 for that part. Missing units where asked loses points even if the math is right.

Q1 (6): dx/dt = lim_{Δt→0} [x(t+Δt) - x(t)] / Δt (3). Units: ẋ in volts/second (1.5); ∫x dt in volt-seconds (1.5).
Q2 (8): (a) 15t^2 - 2 (3). (b) -3 e^{-3t} (2). (c) -4 sin(4t) (2). Rule enabling term-by-term = linearity of the derivative (distributes over sums, pulls out constants) (1).
Q3 (8): law stated (2). Special because it is (up to scale) the only function whose derivative is a constant multiple of itself — differentiation preserves its shape (3). With a=jω: d/dt e^{jωt}=jω e^{jωt}, so differentiation becomes "multiply by jω" — the phasor derivative rule; the exponential doesn't grow, it spins, so d/dt just rotates+scales it (3).
Q4 (8): antiderivative X(t)=t^3 - e^{-t} (3). FTC: ∫_0^2 = X(2)-X(0) (2). = (8 - e^{-2}) - (0 - 1) = 9 - e^{-2} ≈ 8.865 (2). +C = the initial condition / constant of integration that differentiation destroyed (1).
Q5 (10): guess x=e^{st} → ṡe^{st}... s e^{st} = -4 e^{st} → s=-4 (4). x(t)=6 e^{-4t} (2). τ = 1/4 = 0.25 s, MUST have seconds (2). Stable because a=-4<0 → decays (2).
Q6 (8): sign of a decides growth vs decay of x=x0 e^{at} (2). a<0 → decays to 0 (stable) (2); a=0 → constant/marginal (2); a>0 → grows without bound (unstable) (2). Only a<0 is stable.
Q7 (12): ZIR = response to initial condition x0 with input=0 (the homogeneous solution x0 e^{at}) (3). ZSR = response to input u with zero initial state (the particular solution / convolution ∫e^{a(t-τ)}b u dτ) (3). ZIR/homogeneous is the transient; ZSR carries the steady-state (3). Legitimate because the system is linear → superposition: total response = response to IC alone + response to input alone (3).
Q8 (18): (a) s^2 + 6s + 25 = 0 (4). (b) s = [-6 ± sqrt(36-100)]/2 = -3 ± 4j (5). (c) x(t)=e^{-3t}(C1 cos4t + C2 sin4t) [or R e^{-3t}cos(4t+φ)] via Euler; envelope e^{-3t}, ω_d = 4 rad/s (5). (d) Stable because Re{s} = -3 < 0 (left half-plane) (4).
Q9 (12): (a) ω_n = undamped natural frequency (√(k/m)-type), sqrt of the constant term here ω_n=5 rad/s; ζ = damping ratio, 2ζω_n = 6 → ζ=0.6 (4). (b) ζ>1 overdamped: two real roots, no oscillation; ζ=1 critically damped: fastest non-oscillating; 0<ζ<1 underdamped: decaying oscillation; ζ=0 undamped: pure sinusoid rings forever (6). (c) Underdamped (0<ζ<1), because the roots are a complex conjugate pair -3±4j (2).
Q10 (10): (a) guessing x=e^{st} turns d/dt into "multiply by s"; each derivative d^n/dt^n → s^n, so the ODE becomes a polynomial in s — identical in form to det(λI-A)=0, and the roots s ARE the continuous-time analog of eigenvalues λ (5). (b) Continuous-time stable ⇔ every root/eigenvalue has Re{s}<0 (strict left half-plane) (3); discrete-time stable ⇔ |λ|<1 (inside the unit circle) — CT axis-boundary is the imaginary axis, DT boundary is the unit circle (2).
Banding: A 90-100, B 80-89 PASS, C 70-79 FAIL-close, <70 remediate. Below 80 → keep P3 locked; route misses to the cited concept pages.
========================================================================================================= -->
