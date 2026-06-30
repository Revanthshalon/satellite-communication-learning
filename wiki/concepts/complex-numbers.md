---
tags: [signal-processing, math-foundations]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Complex Numbers

> **Module P0 · Page 1 of 3.** Prerequisite for everything. Next: [[Euler's Formula]] → [[Sinusoids And Phasors]]. Part of [[Curriculum]].

## Intuition

Ordinary ("real") numbers live on a **line** — left is negative, right is positive. Complex numbers live on a **plane**. That one upgrade — from a line to a plane — is the whole idea.

Why would we want that? Because a huge amount of engineering is about things that **rotate or oscillate**: an AC voltage, a radio wave, a spinning motor, a satellite signal. A point on a line can only go back and forth. A point on a *plane* can go *around*. Complex numbers are the natural language for anything that spins, and a wave is just a spin viewed from the side.

The historical name is unfortunate. "Imaginary" makes it sound fake. Think of it instead as **"the second axis"** — the up/down direction you add to the usual left/right number line. Nothing imaginary about up.

**Analogy.** A real number is an address on a one-way street ("house number 7"). A complex number is an address in a city grid ("3 blocks east, 4 blocks north"). The second one needs *two* numbers because the plane has two directions. Same idea, more room.

## Math

### The imaginary unit

We invent one new number, called **j** (engineers write `j`; mathematicians write `i`), defined by a single rule:

$$j^2 = -1 \qquad\Longleftrightarrow\qquad j = \sqrt{-1}$$

This is the one thing you accept on faith. No real number squares to a negative, so `j` is genuinely new — it's the unit step in the *second* (vertical) direction. **This book and all of signal processing use `j`, not `i`** (because `i` already means electric current), so we use `j` throughout.

### Rectangular form

Every complex number is written as a real part plus an imaginary part:

$$z = a + jb$$

- `a` = **real part**, written $\operatorname{Re}\{z\}$ — how far east (horizontal axis)
- `b` = **imaginary part**, written $\operatorname{Im}\{z\}$ — how far north (vertical axis)
- Note: `b` is itself an ordinary real number; the `j` just tags it as belonging to the vertical axis.

So `z = 3 + 4j` means "3 east, 4 north" on the **complex plane** (horizontal = real axis, vertical = imaginary axis).

### Arithmetic — it's just algebra with one extra rule

**Add/subtract** — combine like axes (like adding vectors tip-to-tail):
$$(a+jb) + (c+jd) = (a+c) + j(b+d)$$

**Multiply** — expand normally (FOIL), then replace every $j^2$ with $-1$:
$$(a+jb)(c+jd) = ac + jad + jbc + j^2bd = (ac - bd) + j(ad + bc)$$

The magic of signal processing hides in that multiplication rule: as we'll see in [[Sinusoids And Phasors]], **multiplying complex numbers adds their angles** — i.e., multiplication *rotates*.

### Complex conjugate

Flip the sign of the imaginary part (a mirror reflection across the real axis):
$$z = a + jb \quad\Longrightarrow\quad z^* = a - jb$$

Its key property — multiplying a number by its own conjugate kills the `j` and gives a real, non-negative number:
$$z z^* = (a+jb)(a-jb) = a^2 - (jb)^2 = a^2 + b^2$$

That result, $a^2+b^2$, is the squared *length* of the arrow — which leads straight to magnitude.

### Magnitude and angle (polar form) — the engineer's view

Instead of "east `a`, north `b`," describe the arrow by its **length** and **direction**:

$$|z| = \sqrt{a^2 + b^2} \quad\text{(magnitude / modulus)}, \qquad \angle z = \theta = \arctan\!\left(\tfrac{b}{a}\right) \quad\text{(angle / argument)}$$

- **Magnitude** $|z|$ = distance from the origin = $\sqrt{zz^*}$. Always ≥ 0. In signals this becomes *amplitude* / *strength*.
- **Angle** $\theta$ = direction measured counter-clockwise from the positive real axis, in **radians**. In signals this becomes *phase*. (Use the *full* `atan2(b, a)` to get the quadrant right — plain `arctan(b/a)` can't tell 1+j from −1−j.)

Going back the other way (polar → rectangular):
$$a = |z|\cos\theta, \qquad b = |z|\sin\theta$$

This magnitude/angle picture is exactly why complex numbers describe rotation, and it's the doorway to [[Euler's Formula]].

## Terms Experts Use

- **Real / imaginary part** — the two coordinates; $\operatorname{Re}\{z\}, \operatorname{Im}\{z\}$.
- **Complex plane** (a.k.a. *Argand plane*, *s-plane*, *z-plane* in later chapters) — the 2-D space these numbers live in.
- **Modulus / magnitude / absolute value** — all mean $|z|$.
- **Argument / phase / angle** — all mean $\theta$.
- **Conjugate** — $z^*$ (engineers) or $\bar z$ (mathematicians).
- **Rectangular (Cartesian) form** $a+jb$ vs. **polar form** $|z|\angle\theta$ — two descriptions of the same point. Pros switch between them fluidly: rectangular for add/subtract, polar for multiply/divide.

## Worked Example

Let $z = 3 + 4j$.

- $\operatorname{Re}\{z\} = 3$, $\operatorname{Im}\{z\} = 4$.
- Conjugate: $z^* = 3 - 4j$.
- $zz^* = 3^2 + 4^2 = 25$, so magnitude $|z| = \sqrt{25} = 5$.
- Angle: $\theta = \operatorname{atan2}(4,3) \approx 0.927$ rad $\approx 53.13°$.
- Polar form: $z = 5\,\angle\,53.13°$.

Multiply by $w = 1 + j$ (which has $|w|=\sqrt2$, $\angle w = 45°$):
$$zw = (3+4j)(1+j) = (3-4) + j(3+4) = -1 + 7j.$$
Check via polar: $|zw|$ should be $5\sqrt2 \approx 7.07$, and indeed $\sqrt{(-1)^2+7^2}=\sqrt{50}=7.07$. ✓ The angle should be $53.13°+45° = 98.13°$ — note multiplication **added the angles**. Hold onto that; it is the engine of [[Sinusoids And Phasors]].

## Checkpoint

Tested in [[Quiz P0 Math Toolkit]]. You should be able to, cold:
1. State $j^2=-1$ and explain why `j` is "the second axis," not something fake.
2. Add and multiply two complex numbers in rectangular form.
3. Convert between rectangular and polar form, both directions.
4. Compute a magnitude as $\sqrt{zz^*}$ and explain why the conjugate makes it real.
5. Explain in words why complex multiplication corresponds to rotation.

## My Understanding

_(Your space — write what clicked and in your own words. Updated via `/second-brain-refine`.)_

## Open Questions

- [ ] _Raise anything that still feels arbitrary (e.g. "why is angle measured in radians, not degrees?") — we'll resolve it and log it in [[Learning Log]]._
