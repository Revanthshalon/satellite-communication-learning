---
tags: [math-foundations, signal-processing, estimation]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Vectors And Dot Products

> **Module P1 · Page 1 of 3.** Needs [[Complex Numbers]]. Next: [[Matrices And Linear Transformations]] → [[Eigenvalues And Eigenvectors]]. Part of [[Curriculum]] · [[Learning Path]].

## Intuition

A **vector** is just a list of numbers that belong together. That's it. Two readings of the same object:

- **As an arrow** — $\begin{bmatrix}3\\4\end{bmatrix}$ is "go 3 east, 4 north," an arrow on the plane (exactly the picture from [[Complex Numbers]], now without the `j`).
- **As a bundle of data** — the *state* of a satellite ("position, velocity, battery charge") is one vector; a chunk of a sampled signal $[x_1, x_2, \dots, x_n]$ is one vector in $n$-dimensional space.

Why bundle them? Because in this book a *system's entire condition* is a single vector, and a system's *action* (next section) is something that acts on that whole vector at once. Linear algebra is the bookkeeping that lets us manipulate many numbers as one object.

The **dot product** is the one operation you must love. It eats two vectors and returns a single number that answers: *"how much do these two point the same way?"* That single question secretly underlies **length**, **angle**, **orthogonality**, and — in [[Probability Fundamentals]] — **correlation** between random quantities. Same math, many disguises.

## Math

### Vectors

We write vectors as **columns** and stack $n$ real numbers to live in $\mathbb{R}^n$ ("real $n$-space"):
$$\mathbf{a} = \begin{bmatrix} a_1 \\ a_2 \\ \vdots \\ a_n \end{bmatrix} \in \mathbb{R}^n.$$
The numbers $a_i$ are the **components**. (When components are complex, the space is $\mathbb{C}^n$ — needed later because eigenvalues can be complex.)

**Addition** (tip-to-tail) and **scalar multiplication** (stretch/shrink) work component by component:
$$\mathbf{a}+\mathbf{b} = \begin{bmatrix} a_1+b_1 \\ \vdots \\ a_n+b_n\end{bmatrix}, \qquad c\,\mathbf{a} = \begin{bmatrix} c\,a_1 \\ \vdots \\ c\,a_n\end{bmatrix}.$$
These two operations — add, scale — are the *only* things "linear" ever means. Hold that thought; it returns everywhere.

### The dot (inner) product

Multiply matching components and sum:
$$\boxed{\;\mathbf{a}\cdot\mathbf{b} = \sum_{i=1}^{n} a_i b_i = a_1b_1 + a_2b_2 + \dots + a_nb_n\;}$$
The result is a **single scalar**. There is also a geometric face of the same number:
$$\mathbf{a}\cdot\mathbf{b} = \lVert\mathbf{a}\rVert\,\lVert\mathbf{b}\rVert\cos\theta,$$
where $\theta$ is the angle between the arrows. So the dot product is "lengths multiplied, scaled by how aligned they are."

### Length (norm) and the unit vector

Set $\mathbf{b}=\mathbf{a}$ (angle 0, $\cos 0=1$): the dot product of a vector with itself is its squared length.
$$\mathbf{a}\cdot\mathbf{a} = \sum a_i^2 = \lVert\mathbf{a}\rVert^2 \quad\Longrightarrow\quad \lVert\mathbf{a}\rVert = \sqrt{\mathbf{a}\cdot\mathbf{a}}.$$
This is the Pythagorean theorem in $n$ dimensions, and the exact analogue of $|z|=\sqrt{zz^*}$ from [[Complex Numbers]]. A **unit vector** has length 1: $\hat{\mathbf{a}} = \mathbf{a}/\lVert\mathbf{a}\rVert$.

### Orthogonality — the star property

If $\theta = 90°$ then $\cos\theta = 0$, so
$$\mathbf{a}\cdot\mathbf{b} = 0 \quad\Longleftrightarrow\quad \mathbf{a}\perp\mathbf{b}\ \ (\text{perpendicular}).$$
"Dot product zero" = "no shared direction" = **independent / non-overlapping**. This is the algebraic seed of huge ideas: perpendicular axes, the Fourier basis of [[Sinusoids And Phasors]] (different frequencies are orthogonal), and **uncorrelated** random variables in [[Probability Fundamentals]] (zero correlation ↔ orthogonal in a vector-space view — a connection the book makes explicitly in its estimation chapters).

### Projection — "how much of a lies along b"

The component of $\mathbf{a}$ in the direction of a unit vector $\hat{\mathbf{b}}$ is the scalar $\mathbf{a}\cdot\hat{\mathbf{b}}$, and the projection vector is
$$\operatorname{proj}_{\mathbf{b}}\mathbf{a} = \left(\frac{\mathbf{a}\cdot\mathbf{b}}{\mathbf{b}\cdot\mathbf{b}}\right)\mathbf{b}.$$
Projection is literally "drop a perpendicular shadow." It is the engine of **least-squares estimation** (Chapters 8 & 12): the best estimate is the projection of the truth onto the space of what you can measure. Keep this picture; it's the whole idea of optimal estimation in one move.

### Complex vectors (a heads-up for eigenvalues)

When components are complex, the honest length must stay real and non-negative, so we **conjugate one factor** (the *Hermitian* inner product):
$$\langle \mathbf{a},\mathbf{b}\rangle = \sum_i a_i^{*}\,b_i, \qquad \lVert\mathbf{a}\rVert^2 = \sum_i |a_i|^2 \ge 0.$$
Same idea as $zz^*$. You'll need this because [[Eigenvalues And Eigenvectors]] of real matrices can be complex.

## Terms Experts Use

- **Scalar** — a single number; **vector** — an ordered list; **components / entries** — the numbers inside.
- $\mathbb{R}^n$ / $\mathbb{C}^n$ — real / complex $n$-dimensional space.
- **Dot product / inner product / scalar product** — all the same $\mathbf{a}\cdot\mathbf{b}$ (inner product is the general name, also covers the complex case).
- **Norm / magnitude / length** — $\lVert\mathbf{a}\rVert=\sqrt{\mathbf{a}\cdot\mathbf{a}}$. **Unit vector** — length 1.
- **Orthogonal** — perpendicular, dot product 0. **Orthonormal** — mutually orthogonal *and* each unit length.
- **Projection** — the shadow of one vector onto another (or onto a subspace).
- **Linear combination** — any $c_1\mathbf{a}+c_2\mathbf{b}+\cdots$; the bridge to span/basis in [[Matrices And Linear Transformations]].

## Worked Example

Let $\mathbf{a}=\begin{bmatrix}3\\4\end{bmatrix}$, $\mathbf{b}=\begin{bmatrix}4\\-3\end{bmatrix}$.

- Dot product: $\mathbf{a}\cdot\mathbf{b} = (3)(4)+(4)(-3) = 12-12 = 0$ → **orthogonal**. The arrows are at 90°.
- Lengths: $\lVert\mathbf{a}\rVert=\sqrt{9+16}=5$, $\lVert\mathbf{b}\rVert=\sqrt{16+9}=5$.
- Angle check: $\cos\theta = \dfrac{\mathbf{a}\cdot\mathbf{b}}{\lVert\mathbf{a}\rVert\lVert\mathbf{b}\rVert}=\dfrac{0}{25}=0 \Rightarrow \theta=90°$. ✓
- Projection of $\mathbf{c}=\begin{bmatrix}2\\1\end{bmatrix}$ onto $\mathbf{a}$: $\dfrac{\mathbf{c}\cdot\mathbf{a}}{\mathbf{a}\cdot\mathbf{a}}\mathbf{a} = \dfrac{(2)(3)+(1)(4)}{25}\begin{bmatrix}3\\4\end{bmatrix} = \dfrac{10}{25}\begin{bmatrix}3\\4\end{bmatrix} = \begin{bmatrix}1.2\\1.6\end{bmatrix}$ — the part of $\mathbf{c}$ that lies along $\mathbf{a}$.

## Checkpoint

Tested in [[Quiz P1 Linear Algebra]]. Cold, you should be able to:
1. Add/scale vectors and compute a dot product.
2. Get a vector's length from the dot product, and explain why $\lVert\mathbf{a}\rVert=\sqrt{\mathbf{a}\cdot\mathbf{a}}$.
3. Test two vectors for orthogonality and say what orthogonality *means*.
4. Compute the angle between two vectors via the dot product.
5. Project one vector onto another and explain why projection = "best approximation in that direction."

## My Understanding

_(Your space — the goal: see a dot product and instantly think "alignment → length, angle, orthogonality.")_

## Open Questions

- [ ] _e.g. "Why does the complex inner product conjugate one side?" — resolve and log in [[Learning Log]]._
