---
tags: [math-foundations, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Matrices And Linear Transformations

> **Module P1 · Page 2 of 3.** Needs [[Vectors And Dot Products]]. Next: [[Eigenvalues And Eigenvectors]]. Part of [[Curriculum]] · [[Learning Path]].

## Intuition

A **matrix** is a **machine that turns one vector into another**. Feed it a vector, it spits out a transformed vector — rotated, stretched, sheared, or projected. Nothing more mysterious than that.

Why this matters for the book: a state-space model says *"the system's next state is a matrix times its current state."* The matrix $A$ **is** the system's dynamics — one object that advances the entire state vector one tick into the future. So learning to read a matrix as an action (not a static grid of numbers) is the conceptual key to Chapters 4–6.

The crucial restriction is **linear**: the machine must respect the only two vector operations there are — adding and scaling.
$$A(\mathbf{u}+\mathbf{v}) = A\mathbf{u}+A\mathbf{v}, \qquad A(c\mathbf{u}) = c\,A\mathbf{u}.$$
"Linear" means *no bending*: straight lines stay straight, the origin stays put, grid squares map to parallelograms. That tameness is exactly why we can analyze these systems completely — and why the book linearizes nonlinear models before studying them.

## Math

### A matrix and the matrix–vector product

An $m\times n$ matrix has $m$ rows, $n$ columns; it maps a vector in $\mathbb{R}^n$ to one in $\mathbb{R}^m$. There are **two equally important ways** to read $A\mathbf{x}$:

**View 1 — rows dot the vector** (good for computing):
$$A\mathbf{x} = \begin{bmatrix} \text{—}\,\mathbf{r}_1\,\text{—} \\ \text{—}\,\mathbf{r}_2\,\text{—}\end{bmatrix}\mathbf{x} = \begin{bmatrix}\mathbf{r}_1\cdot\mathbf{x} \\ \mathbf{r}_2\cdot\mathbf{x}\end{bmatrix}.$$
Each output entry is a [[Vectors And Dot Products|dot product]] of one row with $\mathbf{x}$.

**View 2 — columns combine** (good for understanding):
$$A\mathbf{x} = x_1\mathbf{c}_1 + x_2\mathbf{c}_2 + \dots + x_n\mathbf{c}_n.$$
The output is a **linear combination of $A$'s columns**, weighted by $\mathbf{x}$'s entries. This view makes span, rank, and independence obvious in a moment.

Concretely, for $2\times2$:
$$\begin{bmatrix}a&b\\c&d\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix} = \begin{bmatrix}ax+by\\cx+dy\end{bmatrix}.$$

### Matrix–matrix product = composition

$AB$ means "do $B$ first, then $A$" — chaining two machines. The entry in row $i$, column $j$ of $AB$ is (row $i$ of $A$) $\cdot$ (column $j$ of $B$). Consequences worth memorizing:
- **Not commutative:** $AB\neq BA$ in general (rotating then stretching ≠ stretching then rotating).
- Dimensions must match: $(m\times n)(n\times p)=(m\times p)$.

### Identity, inverse, and "can I undo it?"

- **Identity** $I$ — the do-nothing machine ($1$s on the diagonal, $0$s elsewhere): $I\mathbf{x}=\mathbf{x}$.
- **Inverse** $A^{-1}$ — the machine that undoes $A$: $A^{-1}A = I$. It exists only if $A$ doesn't collapse space (doesn't squash a dimension flat). A matrix with an inverse is **nonsingular / invertible**; one without is **singular**.

### Determinant — the "does it collapse?" number

For $2\times2$ (the book states this exact formula in Eq. 5.18):
$$\det\begin{bmatrix}a&b\\c&d\end{bmatrix} = ad-bc.$$
Geometric meaning: $|\det A|$ is the **factor by which areas (volumes) scale** under the transformation. The decisive fact:
$$\det A = 0 \quad\Longleftrightarrow\quad A \text{ is singular (no inverse)} \quad\Longleftrightarrow\quad A \text{ flattens space.}$$
We'll reuse the determinant immediately in [[Eigenvalues And Eigenvectors]] via $\det(\lambda I - A)=0$.

### Independence, span, basis, rank — said simply

Using the **column view** above:
- **Linearly independent** vectors: none is a linear combination of the others — each adds a genuinely new direction. (Test: the only way $c_1\mathbf{v}_1+\dots+c_k\mathbf{v}_k=\mathbf{0}$ is all $c_i=0$.)
- **Span**: all vectors you can reach as linear combinations of a given set — the "territory they cover."
- **Basis**: a minimal set that spans the whole space — independent *and* complete. $\mathbb{R}^n$ needs exactly $n$ basis vectors (e.g. the axes).
- **Rank**: the number of independent columns — how many true dimensions the matrix's output actually fills. Full rank ⇔ nonsingular ⇔ $\det\neq0$.

These four words are one idea seen from four sides: *how many independent directions are in play.*

### Transpose (and a link back to dot products)

The **transpose** $A^{\mathsf T}$ flips rows and columns. Handy identity: the dot product is a transpose-product, $\mathbf{a}\cdot\mathbf{b} = \mathbf{a}^{\mathsf T}\mathbf{b}$. A **symmetric** matrix ($A=A^{\mathsf T}$) has especially nice eigenvalues (real) — relevant to covariance matrices in [[Probability Fundamentals]].

## Terms Experts Use

- **Matrix / dimension ($m\times n$) / square matrix / diagonal matrix.**
- **Linear transformation / map / operator** — the action a matrix performs.
- **Matrix–vector product, matrix–matrix product (composition).**
- **Identity $I$ · inverse $A^{-1}$ · singular vs. nonsingular (invertible).**
- **Determinant** — area/volume scale factor; zero ⇔ singular.
- **Transpose $A^{\mathsf T}$ · symmetric matrix.**
- **Linear independence · span · basis · rank** — facets of "number of independent directions."
- In the book: $A,B,C,D$ are the standard **state-space matrices** ($A$ = state dynamics) — you'll meet them in Chapter 4.

## Worked Example

Let $A=\begin{bmatrix}2&1\\1&2\end{bmatrix}$, $\mathbf{x}=\begin{bmatrix}1\\3\end{bmatrix}$.

- **Action (row view):** $A\mathbf{x}=\begin{bmatrix}2(1)+1(3)\\1(1)+2(3)\end{bmatrix}=\begin{bmatrix}5\\7\end{bmatrix}$.
- **Same answer (column view):** $1\begin{bmatrix}2\\1\end{bmatrix}+3\begin{bmatrix}1\\2\end{bmatrix}=\begin{bmatrix}2\\1\end{bmatrix}+\begin{bmatrix}3\\6\end{bmatrix}=\begin{bmatrix}5\\7\end{bmatrix}$. ✓
- **Determinant:** $\det A = (2)(2)-(1)(1)=3 \neq 0$ → nonsingular, invertible, full rank 2. The columns $\begin{bmatrix}2\\1\end{bmatrix},\begin{bmatrix}1\\2\end{bmatrix}$ are independent (neither is a multiple of the other), so they form a basis of $\mathbb{R}^2$.
- **Inverse (2×2 formula $\frac{1}{\det}\begin{bmatrix}d&-b\\-c&a\end{bmatrix}$):** $A^{-1}=\frac{1}{3}\begin{bmatrix}2&-1\\-1&2\end{bmatrix}$. Check $A^{-1}\begin{bmatrix}5\\7\end{bmatrix}=\frac13\begin{bmatrix}10-7\\-5+14\end{bmatrix}=\frac13\begin{bmatrix}3\\9\end{bmatrix}=\begin{bmatrix}1\\3\end{bmatrix}=\mathbf{x}$. ✓ It undid the action.

## Checkpoint

Tested in [[Quiz P1 Linear Algebra]]. Cold, you should be able to:
1. Compute a matrix–vector product **both** ways (rows-dot and columns-combine).
2. Multiply two matrices and explain why order matters.
3. Compute a 2×2 determinant and say what $\det=0$ means.
4. Define linear independence, span, basis, rank in your own words and connect them.
5. Explain "a matrix is a linear transformation" and why *linear* forbids bending.

## My Understanding

_(Your space — aim to look at a matrix and ask "what does this DO to a vector?")_

## Open Questions

- [ ] _e.g. "How do I see rank without grinding through algebra?" — log it in [[Learning Log]]._
