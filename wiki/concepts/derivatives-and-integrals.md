---
tags: [math-foundations, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-07-01
updated: 2026-07-01
---

# Derivatives And Integrals

> **Module P2 · Page 1 of 2.** Needs [[Complex Numbers]], [[Euler's Formula]]. Next: [[Differential Equations]]. Part of [[Calculus And Differential Equations]] · [[Curriculum]] · [[Learning Path]].

## Intuition

Calculus is the mathematics of **change** and **accumulation**, and it has exactly two verbs:

- The **derivative** answers *"how fast is this changing right now?"* — the **instantaneous rate**, the slope of the curve at a single instant. Speedometer.
- The **integral** answers *"how much has piled up so far?"* — the **accumulated area** under the curve. Odometer.

These two verbs are **inverses of each other** (that's the Fundamental Theorem of Calculus): accumulate a rate and you recover the total; take the rate of a total and you recover the rate. A speedometer and an odometer describe the same trip from two ends.

Why a signals-and-systems course cares: a signal is a function of time, and *everything a system does to it is phrased in calculus*. A capacitor integrates current; an inductor differentiates it; a filter is a differential equation. To read the book's system models you must be fluent in "d/dt" and "∫". And one function — the exponential $e^{at}$ — has a magic property under the derivative that makes it the star of the next page.

## Math

### The derivative — a rate defined by a limit

The derivative of $x(t)$ is the slope of the line just touching the curve at time $t$. Formally it's the limit of the **difference quotient** (rise over run) as the run shrinks to zero:

$$\frac{dx}{dt} \;=\; \dot{x}(t) \;=\; \lim_{\Delta t \to 0}\frac{x(t+\Delta t) - x(t)}{\Delta t}.$$

- **Notation:** $\dfrac{dx}{dt}$ (Leibniz), $x'(t)$ (Lagrange), or $\dot{x}$ (Newton's dot — the book uses the dot for time derivatives, e.g. $\dot{\mathbf{x}} = A\mathbf{x}$).
- **Units:** if $x$ is in volts and $t$ in seconds, $\dot{x}$ is in **volts/second**. A derivative always carries "per unit of the input."

The rules you actually reuse:

| Rule | Statement |
|------|-----------|
| Power | $\dfrac{d}{dt}t^{n} = n\,t^{n-1}$ |
| Constant multiple / sum | $\dfrac{d}{dt}\big(a f + b g\big) = a\dot f + b\dot g$  — the derivative is **linear** |
| Product | $\dfrac{d}{dt}(fg) = \dot f g + f \dot g$ |
| Chain | $\dfrac{d}{dt} f(g(t)) = f'(g)\,\dot g$ |
| Sinusoids | $\dfrac{d}{dt}\cos\omega t = -\omega\sin\omega t,\qquad \dfrac{d}{dt}\sin\omega t = \omega\cos\omega t$ |

That the derivative is **linear** (it distributes over sums and pulls out constants) is not a footnote — it is the property that makes **linear** systems tractable and connects straight to [[Matrices And Linear Transformations|linear maps]].

### The one derivative that runs this whole book

$$\boxed{\;\frac{d}{dt}\,e^{at} = a\,e^{at}\;}$$

The exponential is (up to scale) the **only** function whose derivative is a **constant multiple of itself**. Differentiating it doesn't change its shape — it just multiplies it by the rate $a$. Hold onto this: on the next page it turns differential equations into ordinary algebra, exactly as $\frac{d}{dt}\to \times j\omega$ turned wave algebra into arithmetic in [[Sinusoids And Phasors]]. (Indeed that phasor rule is this same law with $a = j\omega$.)

### The integral — accumulation and area

The **definite integral** of $x(t)$ from $a$ to $b$ is the signed area between the curve and the time axis. Build it as a limit of thin rectangles (a **Riemann sum**), each of width $\Delta t$ and height $x(t_k)$:

$$\int_a^b x(t)\,dt \;=\; \lim_{\Delta t\to 0}\sum_k x(t_k)\,\Delta t.$$

- **Units:** volts × seconds = **volt-seconds**. Integrating multiplies by the axis unit (this is why *energy* — $\int |x|^2\,dt$ — appears later with units of "power × time").
- The **indefinite integral** (antiderivative) $\int x(t)\,dt = X(t) + C$ is *any* function whose derivative is $x$; the $+C$ is the constant that differentiation destroyed and cannot be recovered from the rate alone (it's the **initial condition** in disguise).

### The Fundamental Theorem of Calculus — the two verbs are inverses

$$\frac{d}{dt}\int_a^{t} x(\tau)\,d\tau = x(t), \qquad \int_a^{b}\dot X(t)\,dt = X(b) - X(a).$$

Left: differentiate an accumulation and you get the integrand back. Right: to add up a rate over an interval, just take the difference of the antiderivative at the endpoints. This is *why* solving a differential equation (a statement about a rate) can be done by integrating.

### Antiderivatives you must know cold

$$\int t^{n}\,dt = \frac{t^{n+1}}{n+1}+C\ (n\neq -1),\quad \int \frac{1}{t}\,dt=\ln|t|+C,\quad \int e^{at}\,dt = \frac{1}{a}e^{at}+C,\quad \int\cos\omega t\,dt=\frac{\sin\omega t}{\omega}+C.$$

## Terms Experts Use

- **Derivative / differential** — the instantaneous rate $dx/dt$; "**differentiate**" is the verb. The dot $\dot x$ means $d/dt$ specifically.
- **Slope / tangent line** — the geometric picture of a derivative at a point.
- **Integral / antiderivative** — accumulated area; **definite** (with limits, a number) vs. **indefinite** (a function $+C$).
- **Riemann sum** — the rectangle approximation whose limit *is* the integral.
- **Fundamental Theorem of Calculus (FTC)** — differentiation and integration are inverse operations.
- **Linearity** — $\frac{d}{dt}$ and $\int$ both distribute over sums and pull out constants; the reason "linear" systems are solvable.
- **Higher-order derivative** — $\ddot x = d^2x/dt^2$ (acceleration is the second derivative of position); sets the **order** of a differential equation on the next page.

## Worked Example

Let $x(t) = 3t^2 + e^{-2t}$.

**Differentiate** (power rule + the exponential law, term by term because $d/dt$ is linear):
$$\dot x(t) = 6t + (-2)e^{-2t} = 6t - 2e^{-2t}\quad[\text{units: signal-units per second}].$$

**Integrate** from $0$ to $1$ (FTC): first an antiderivative $X(t) = t^3 - \tfrac{1}{2}e^{-2t}$, then difference the endpoints:
$$\int_0^1 x\,dt = X(1)-X(0) = \big(1 - \tfrac12 e^{-2}\big) - \big(0 - \tfrac12\big) = \tfrac{3}{2} - \tfrac12 e^{-2} \approx 1.432.$$

**Sanity check** the exponential law: $\frac{d}{dt}e^{-2t} = -2e^{-2t}$ — same shape, scaled by the rate $a=-2$. That single fact is the seed of [[Differential Equations]].

## Checkpoint

Tested in [[Quiz P2 Calculus And Differential Equations]]. Cold, you should be able to:
1. Define the derivative as the limit of a difference quotient and give its units.
2. Differentiate polynomials, exponentials, and sinusoids; use product/chain rules.
3. State and *use* $\frac{d}{dt}e^{at} = a e^{at}$ — and explain why it's special.
4. Explain the integral as accumulated area and give its units.
5. State the Fundamental Theorem of Calculus and why the $+C$ is an initial condition.

## My Understanding

_(Your space — the target instinct: "derivative = slope/rate now; integral = area/total so far; and $e^{at}$ is the function that survives differentiation unchanged.")_

## Open Questions

- [ ] _e.g. "What integrates to a step or an impulse?" — leads to the delta function and the [[Signals And Systems Fundamentals|impulse response]]; log in [[Learning Log]]._
