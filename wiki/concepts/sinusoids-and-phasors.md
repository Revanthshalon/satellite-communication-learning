---
tags: [signal-processing, rf-design, math-foundations]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Sinusoids And Phasors

> **Module P0 · Page 3 of 3.** Needs [[Complex Numbers]] and [[Euler's Formula]]. Completes P0 → take [[Quiz P0 Math Toolkit]]. Part of [[Curriculum]].

## Intuition

A **sinusoid** is the shape of a pure tone, an AC outlet, a radio carrier — a smooth, endlessly repeating wave. It is the single most important signal in this entire field, because (we'll later prove) *every* signal can be built by adding sinusoids together.

Here's the picture that ties P0 together: take the spinning arrow $e^{j\theta}$ from [[Euler's Formula]], set it rotating at a steady rate, and **shine a light on it from the side**. The *shadow* it casts on the floor moves back and forth — and that shadow is a cosine wave. A sinusoid is just **circular motion seen edge-on.** Rotation (complex world) and oscillation (real world) are the same thing from two angles.

That is why engineers stop dragging around clunky $\cos(\omega t + \phi)$ expressions and instead carry a single complex number — a **phasor** — that captures the wave's size and starting angle. The tedious trig of combining waves becomes simple arithmetic on arrows.

## Math

### Anatomy of a sinusoid

$$x(t) = A\cos(\omega t + \phi)$$

Three knobs, each a piece of vocabulary you must own:

- **A — amplitude.** Peak height of the wave (volts, etc.). Always the *size* of the swing.
- **ω — angular frequency**, in radians/second. How fast the arrow spins. Related to ordinary frequency `f` (in **hertz**, cycles/second) and period `T` (seconds/cycle) by
$$\omega = 2\pi f = \frac{2\pi}{T}.$$
The $2\pi$ is there because one full cycle is $2\pi$ radians of rotation.
- **φ — phase**, in radians. *Where the arrow starts* at $t=0$ — a head start (lead) or lag in the cycle. A cosine is a sine shifted by φ = 90°: $\cos\theta = \sin(\theta + \tfrac{\pi}{2})$.

### From wave to phasor

Use Euler ([[Euler's Formula]]) to write the cosine as the real part of a spinning exponential:
$$x(t) = A\cos(\omega t + \phi) = \operatorname{Re}\!\big\{A e^{\,j(\omega t + \phi)}\big\} = \operatorname{Re}\!\big\{\underbrace{A e^{j\phi}}_{\text{phasor } X}\, e^{j\omega t}\big\}.$$

Split the exponential into two factors:
- $e^{j\omega t}$ — the **universal spin**. Every signal at frequency ω carries this same factor; it's just "the clock ticking." We agree to leave it implied.
- $X = A e^{j\phi}$ — the **phasor**: a *single complex number* holding the amplitude (`A` = its magnitude) and phase (`φ` = its angle). This is all the information that distinguishes one sinusoid from another at a given frequency.

**The phasor idea in one sentence:** at a fixed frequency, a sinusoid ↔ a complex number ($A\angle\phi$), so wave algebra becomes complex-number algebra.

### Why this is a superpower: adding two waves

Adding $5\cos(\omega t) + 5\cos(\omega t + 90°)$ by trig identities is miserable. With phasors it's vector addition on the plane:
$$X_1 = 5\,e^{j0} = 5, \qquad X_2 = 5\,e^{j90°} = 5j,$$
$$X_1 + X_2 = 5 + 5j = 5\sqrt2\;e^{j45°}.$$
Read it straight off: the sum is $5\sqrt2\cos(\omega t + 45°)$. Two waves of the same frequency **always** add to one wave of that frequency — obvious as arrows, painful as trig. (Crucial caveat: phasor addition only works when the frequencies match. Different frequencies → different clocks → you cannot collapse them this way.)

### Why this is THE superpower: derivatives become multiplication

Differentiate the spinning form:
$$\frac{d}{dt}\,e^{j\omega t} = j\omega\, e^{j\omega t}.$$
Taking a derivative just **multiplies the phasor by $j\omega$** — calculus turns into multiplication. This is the reason complex exponentials are the "natural language" of any system described by differential equations (every circuit, every filter, every [[Calculus And Differential Equations|differential-equation]] model). Feed a system a complex exponential and it comes out scaled by some complex number — never a new shape. That property (the exponential is an *eigenfunction*) is the foundation of [[Signals And Systems Fundamentals]] and the entire book.

### Positive and negative frequency

From the inverse Euler relation, a real cosine is two counter-rotating phasors:
$$A\cos(\omega t+\phi) = \tfrac{A}{2}e^{j\phi}e^{j\omega t} + \tfrac{A}{2}e^{-j\phi}e^{-j\omega t}.$$
The second term spins *backwards* ($-\omega$). "Negative frequency" isn't mystical — it's just the clockwise twin whose imaginary parts cancel the first's, leaving a purely real wave. This pairing is why spectra in later chapters are symmetric.

## Terms Experts Use

- **Sinusoid** — any $A\cos(\omega t+\phi)$ (or sine; they differ only by phase).
- **Amplitude / angular frequency / phase** — `A` / `ω` / `φ`; know units (—, rad/s, rad).
- **Frequency `f` (Hz) vs. angular frequency `ω` (rad/s)** — $\omega = 2\pi f$. Mixing them up is the single most common beginner error.
- **Period `T`** — seconds per cycle, $T = 1/f$.
- **Phasor** — the complex number $Ae^{j\phi}$ representing the wave at a fixed frequency.
- **Eigenfunction** — a signal a system only *scales*, never reshapes; $e^{j\omega t}$ is the eigenfunction of every LTI system (preview of [[Signals And Systems Fundamentals]]).
- **In-phase / quadrature** — the cosine part vs. the 90°-shifted sine part; the basis of QAM modulation in the book's Chapter 3.

## Worked Example

A signal is $x(t) = 3\cos(100\pi t) + 4\sin(100\pi t)$. Find its single-sinusoid amplitude and phase.

1. Same frequency? $\omega = 100\pi$ rad/s for both → yes, so $f = \omega/2\pi = 50$ Hz. Phasors are valid.
2. Convert each to a phasor (reference = cosine). $3\cos(\omega t) \to 3\,e^{j0} = 3$.
   For the sine: $\sin = \cos(\cdot - 90°)$, so $4\sin(\omega t) = 4\cos(\omega t - 90°) \to 4\,e^{-j90°} = -4j$.
3. Add: $X = 3 - 4j$. Magnitude $|X| = \sqrt{3^2+4^2} = 5$; angle $\angle X = \operatorname{atan2}(-4,3) \approx -53.13°$.
4. Therefore $x(t) = 5\cos(100\pi t - 53.13°)$. One clean wave, found by the same $3-4j$ arrow from [[Complex Numbers]]. The whole module closes the loop.

## Checkpoint

Tested in [[Quiz P0 Math Toolkit]]. Cold, you should be able to:
1. Label A, ω, φ on a sinusoid and give each one's units.
2. Convert between `f` (Hz), `ω` (rad/s), and `T` (s).
3. Write a sinusoid as $\operatorname{Re}\{X e^{j\omega t}\}$ and identify the phasor `X`.
4. Add two same-frequency sinusoids using phasors.
5. Explain "a sinusoid is rotation seen edge-on" and why $\frac{d}{dt}$ becomes $\times j\omega$.

## My Understanding

_(Your space. The goal: see a wave and instinctively picture the spinning arrow behind it.)_

## Open Questions

- [ ] _e.g. "What happens to the phasor picture when amplitude grows or decays over time?" — leads to the complex frequency `s = σ + jω`; log it in [[Learning Log]]._
