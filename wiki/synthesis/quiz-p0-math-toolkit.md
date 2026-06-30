---
tags: [learning-progress, assessment, math-foundations]
sources: [discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Quiz P0 Math Toolkit

Strict checkpoint for Module P0: [[Complex Numbers]] · [[Euler's Formula]] · [[Sinusoids And Phasors]]. Graded under the rubric in [[Score Log]] (pass ≥ 80%, no credit for right answer + wrong reasoning, units matter, show your work). Passing unlocks **P1 Linear Algebra** in [[Curriculum]].

**Format:** 10 questions, 100 points. Closed-book. Tell me *"I'm ready for the P0 quiz"* and answer in chat; I deliver them in 3 batches, grade strictly, and append your row to [[Score Log]].

## Section A — Complex Numbers (30 pts)

1. **(6 pts)** State the defining property of `j`, and explain in one or two sentences why `j` is legitimate ("the second axis") rather than a fake number. Why do we use `j` and not `i`?
2. **(8 pts)** Let $z = 2 - 5j$ and $w = -1 + 3j$. Compute (a) $z + w$, (b) $zw$. Show the $j^2 = -1$ substitution.
3. **(8 pts)** For $z = -3 + 3j$: give (a) the conjugate, (b) the magnitude as $\sqrt{zz^*}$, (c) the angle in degrees (mind the quadrant), (d) the polar form $re^{j\theta}$.
4. **(8 pts)** Explain, in words, why multiplying two complex numbers *rotates*. Reference what happens to magnitudes and to angles.

## Section B — Euler's Formula (35 pts)

5. **(6 pts)** Write Euler's formula. Then explain why $e^{j\theta}$ "spins" instead of "grows" — what does the `j` in the exponent change?
6. **(9 pts)** Evaluate and place on the unit circle (state the resulting complex number): (a) $e^{j0}$, (b) $e^{j\pi/2}$, (c) $e^{j\pi}$, (d) $e^{-j\pi/2}$.
7. **(8 pts)** Use polar/Euler form to compute $(1 - j)^4$. Show the "cube/power = scale magnitude, multiply angle" step. Give a rectangular-form final answer.
8. **(12 pts)** State both inverse Euler relations (for $\cos\theta$ and $\sin\theta$). Then explain what "a real cosine is two counter-rotating phasors" means, and why the imaginary parts cancel.

## Section C — Sinusoids & Phasors (35 pts)

9. **(15 pts)** A sinusoid is $x(t) = 10\cos(2\pi\cdot 60\,t + \tfrac{\pi}{3})$. Give, with **units**: (a) amplitude, (b) angular frequency ω, (c) ordinary frequency `f`, (d) period `T`, (e) phase φ in degrees, (f) the phasor `X`.
10. **(20 pts)** Combine $x(t) = 6\cos(\omega t) + 8\sin(\omega t)$ (same ω) into a single $A\cos(\omega t + \phi)$ using phasors. Show: each wave's phasor, the sum, then `A` and `φ`. Finally, explain in one sentence why this phasor trick fails if the two waves had *different* frequencies.

---

_When you're done I total the points, assign a band (A/B/C/D-F), diagnose every miss, and log it. Below ~80% the P1 module stays locked and I'll route you back to the exact sections to redo._

<!-- ============================ GRADER ANSWER KEY (hidden in rendered view) ============================
Total 100. Strict: correct final value from flawed reasoning = 0 for that part. Missing units in Q9 = -1 each.

Q1 (6): j^2 = -1 (2). "Second/vertical axis", not fake — up direction added to the real line; rotations/oscillations need a plane (2). j used because i = electric current in EE (2).
Q2 (8): (a) z+w = (2-1) + j(-5+3) = 1 - 2j (3). (b) zw = (2-5j)(-1+3j) = -2 +6j +5j -15j^2 = -2 +11j +15 = 13 + 11j (5). Must show j^2=-1 step or -2 on the FOIL.
Q3 (8): z=-3+3j. (a) z* = -3 - 3j (2). (b) zz* = 9+9=18, |z|=sqrt(18)=3√2≈4.243 (2). (c) 2nd quadrant: atan2(3,-3)=135° (2). (d) 3√2 e^{j135°} (2).
Q4 (8): magnitudes multiply, angles add (4). Because in polar form (r1 e^{jθ1})(r2 e^{jθ2}) = r1r2 e^{j(θ1+θ2)} — adding the angle IS rotation (4). Reasoning required, not just "it rotates."
Q5 (6): e^{jθ}=cosθ + j sinθ (2). j makes the push perpendicular/sideways at every instant → motion along the unit circle, magnitude stays 1, so it turns rather than grows (4).
Q6 (9, 2.25 each→round): (a) e^{j0}=1 (east). (b) e^{jπ/2}=j (north/up). (c) e^{jπ}=-1 (west). (d) e^{-jπ/2}=-j (south/down).
Q7 (8): 1-j = √2 e^{-j45°}. ^4 → (√2)^4 e^{-j180°} = 4·(-1) = -4. Rectangular: -4 + 0j (= -4). Full credit needs magnitude^4=4 and angle×4=-180°.
Q8 (12): cosθ=(e^{jθ}+e^{-jθ})/2 (3); sinθ=(e^{jθ}-e^{-jθ})/(2j) (3). Explanation (6): cosine = sum of a +ω (CCW) phasor and a -ω (CW) phasor each of half amplitude; their imaginary parts (+sin and -sin) cancel, leaving a purely real wave.
Q9 (15): (a) A=10 (units of the signal, e.g. volts) ; (b) ω=2π·60=120π≈376.99 rad/s ; (c) f=60 Hz ; (d) T=1/60≈0.0167 s ; (e) φ=π/3=60° ; (f) X = 10 e^{jπ/3} = 10∠60° (=5 + j5√3). 2.5 each, -1 per missing unit.
Q10 (20): 6cos→6∠0°=6 (4). 8sin=8cos(ωt-90°)→8∠-90°=-8j (4). Sum X=6-8j (4). A=|X|=10 (3). φ=atan2(-8,6)≈-53.13° (3). So x(t)=10cos(ωt-53.13°). Different-freq explanation (2): phasors drop the shared e^{jωt} clock; unequal ω = different clocks that don't combine into one constant phasor, so the sum isn't a single fixed-frequency sinusoid.
Banding: A 90-100, B 80-89 PASS, C 70-79 FAIL-close, <70 remediate. Below 80 → keep P1 locked; route misses to the cited concept pages.
========================================================================================================= -->
