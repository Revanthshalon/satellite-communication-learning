---
tags: [signal-processing, math-foundations]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Euler's Formula

> **Module P0 · Page 2 of 3.** Needs [[Complex Numbers]]. Next: [[Sinusoids And Phasors]]. Part of [[Curriculum]].

## Intuition

[[Complex Numbers]] gave us a plane and showed that *multiplying rotates*. Euler's formula answers the natural next question: **is there a single, clean object whose only job is "rotate by angle θ"?** Yes — and it's a complex exponential:

$$e^{j\theta}$$

Read it as a verb, not a number: $e^{j\theta}$ is **"the unit arrow pointed at angle θ."** It always sits on the circle of radius 1 (the **unit circle**). Plug in θ = 0 and it points east (the number 1). Increase θ and it sweeps counter-clockwise. At θ = 90° it points straight up (that's `j`); at 180° it points west (−1).

Why should an *exponential* — the growth function from compound interest — have anything to do with *circles*? Because the imaginary `j` in the exponent reinterprets "growth" as "turning." Ordinary $e^{at}$ grows along the line. Put a `j` in front, $e^{jat}$, and that same relentless push becomes a push *sideways at every instant*, which is exactly what keeps a point moving in a circle. **An exponential with an imaginary rate doesn't grow — it spins.** That single substitution is the most important idea in this entire prerequisite.

## Math

### The formula

$$\boxed{\,e^{j\theta} = \cos\theta + j\sin\theta\,}$$

The right-hand side is just a point in polar form with **magnitude 1** and **angle θ** (recall from [[Complex Numbers]]: $a=\cos\theta$, $b=\sin\theta$, so $|e^{j\theta}| = \sqrt{\cos^2\theta+\sin^2\theta}=1$). So $e^{j\theta}$ literally *is* the unit arrow at angle θ — the intuition made exact.

**Euler's identity**, the famous special case at θ = π (180°):
$$e^{j\pi} = \cos\pi + j\sin\pi = -1 \qquad\Longrightarrow\qquad e^{j\pi} + 1 = 0.$$
Five fundamental constants ($e, j, \pi, 1, 0$) in one line — but for us it's just "rotate the arrow 180°, you land on −1."

### Where it comes from (the power-series sketch)

You don't need to memorize this, but seeing it once removes the mystery. Each function equals an infinite polynomial (its Taylor series):
$$e^x = 1 + x + \tfrac{x^2}{2!} + \tfrac{x^3}{3!} + \cdots$$
Substitute $x = j\theta$ and use the cycle $j^1=j,\ j^2=-1,\ j^3=-j,\ j^4=1,\ \dots$ to sort the terms into those *without* a `j` and those *with* one:
$$e^{j\theta} = \underbrace{\left(1 - \tfrac{\theta^2}{2!} + \tfrac{\theta^4}{4!} - \cdots\right)}_{=\,\cos\theta} \;+\; j\underbrace{\left(\theta - \tfrac{\theta^3}{3!} + \tfrac{\theta^5}{5!} - \cdots\right)}_{=\,\sin\theta}.$$
The two leftover series are *exactly* the known series for cosine and sine. So the identity isn't a coincidence — it falls out of the algebra of `j`.

### Polar form, finally clean

Euler lets us write **any** complex number compactly. A number with magnitude `r` and angle θ is:
$$z = r\,e^{j\theta} = r\cos\theta + jr\sin\theta.$$
Now the rotation rule from [[Complex Numbers]] becomes one line of exponent algebra:
$$(r_1 e^{j\theta_1})(r_2 e^{j\theta_2}) = r_1 r_2\, e^{j(\theta_1+\theta_2)}.$$
**Multiply the magnitudes, add the angles** — because exponents add. This is why engineers do all multiplication, division, and powers in polar form.

### Sine and cosine, recovered (the inverse Euler relations)

Add $e^{j\theta}$ and its conjugate $e^{-j\theta} = \cos\theta - j\sin\theta$, or subtract them, to isolate each piece:
$$\cos\theta = \frac{e^{j\theta} + e^{-j\theta}}{2}, \qquad \sin\theta = \frac{e^{j\theta} - e^{-j\theta}}{2j}.$$
These two are the workhorses of signal processing: they turn *every* sine and cosine into a pair of complex exponentials — one spinning counter-clockwise ($e^{+j\theta}$), one clockwise ($e^{-j\theta}$). That's the seed of the Fourier transform in [[Signals And Systems Fundamentals]].

## Terms Experts Use

- **Complex exponential** — $e^{j\theta}$; the fundamental "rotator."
- **Unit circle** — all points $e^{j\theta}$, radius 1; the home of pure rotation.
- **Phasor** — a complex number $re^{j\theta}$ used to represent a sinusoid's amplitude (`r`) and phase (θ). Developed in [[Sinusoids And Phasors]].
- **Inverse Euler relations** — the $\cos = (e^{j\theta}+e^{-j\theta})/2$ pair above.
- **Argument** — the θ in the exponent (same "angle" as in [[Complex Numbers]]).
- Pros say *"on the unit circle"* to mean "magnitude 1, pure phase, no growth/decay" — a phrase you'll meet again with the z-transform and Laplace transform.

## Worked Example

Express $z = 1 + j$ in Euler form, then cube it.
- Magnitude $r = \sqrt{1^2+1^2} = \sqrt2$; angle $\theta = \operatorname{atan2}(1,1) = 45° = \pi/4$.
- So $z = \sqrt2\, e\,^{j\pi/4}$.
- Cube it by tripling the angle and cubing the magnitude (trivial in polar form): $z^3 = (\sqrt2)^3 e^{j\,3\pi/4} = 2\sqrt2\, e^{j135°}$.
- Convert back: $2\sqrt2(\cos135° + j\sin135°) = 2\sqrt2(-\tfrac{1}{\sqrt2} + j\tfrac{1}{\sqrt2}) = -2 + 2j$.
- Sanity check by brute force: $(1+j)^2 = 2j$, then $(2j)(1+j) = 2j + 2j^2 = -2 + 2j$. ✓ Polar form did in one step what rectangular form took two.

## Checkpoint

Tested in [[Quiz P0 Math Toolkit]]. Cold, you should be able to:
1. Write $e^{j\theta} = \cos\theta + j\sin\theta$ and explain *in words* why it represents rotation, not growth.
2. Evaluate $e^{j0}, e^{j\pi/2}, e^{j\pi}$ and place each on the unit circle.
3. Use $re^{j\theta}$ to multiply/take powers of complex numbers.
4. State both inverse Euler relations for $\cos$ and $\sin$.
5. Explain why a real cosine is "two spinning exponentials."

## My Understanding

_(Your space — paraphrase "an exponential with an imaginary rate spins" until it feels obvious.)_

## Open Questions

- [ ] _e.g. "What does a negative or complex exponent rate mean physically?" — that's the bridge to growing/decaying signals; flag it for [[Learning Log]]._
