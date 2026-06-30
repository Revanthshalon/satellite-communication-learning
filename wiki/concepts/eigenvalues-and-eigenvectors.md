---
tags: [math-foundations, signal-processing]
sources: [Signals, Systems and Inference.pdf, discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Eigenvalues And Eigenvectors

> **Module P1 · Page 3 of 3.** Needs [[Vectors And Dot Products]], [[Matrices And Linear Transformations]], [[Complex Numbers]], [[Euler's Formula]]. Completes P1 → take [[Quiz P1 Linear Algebra]]. Part of [[Curriculum]] · [[Learning Path]].

## Intuition

A matrix usually **rotates and stretches** vectors, so an output points somewhere new. But almost every matrix has a few special directions where it does *no rotating at all* — it only **stretches the vector along its own line**. Those special directions are **eigenvectors**, and the stretch factor for each is its **eigenvalue**.

$$A\mathbf{v} = \lambda \mathbf{v} \qquad\text{“}A\text{ acting on } \mathbf{v} \text{ just scales it by } \lambda\text{.”}$$

Why this is the single most important idea for Chapters 4–6: a state-space system evolves by **repeatedly multiplying by $A$**. Along an ordinary direction that's a tangled mess. But *along an eigenvector, repeated multiplication is just repeated scaling* — the matrix "uncouples" into independent 1-D behaviors. The eigenvectors are the system's **natural axes**, and the eigenvalues are its **natural frequencies / modes**. The book calls $\lambda$ the *characteristic root, natural frequency,* or *eigenvalue* and $\mathbf{v}$ the *characteristic vector* — all synonyms. Finding them is how you predict whether a system rings, decays, or blows up.

## Math

### The eigenvalue equation and the trick to solve it

We want nonzero $\mathbf{v}$ with $A\mathbf{v}=\lambda\mathbf{v}$. Rewrite using the identity $I$:
$$A\mathbf{v}-\lambda\mathbf{v}=\mathbf{0} \;\Longrightarrow\; (\lambda I - A)\mathbf{v}=\mathbf{0}.$$
For a **nonzero** $\mathbf{v}$ to exist, the matrix $(\lambda I - A)$ must **collapse space** — i.e. be singular — which (from [[Matrices And Linear Transformations]]) means its determinant is zero:
$$\boxed{\;\det(\lambda I - A) = 0\;}$$
This is the **characteristic equation**. Expanding the determinant gives the **characteristic polynomial** in $\lambda$; its roots are the eigenvalues. Then for each eigenvalue you solve $(\lambda I - A)\mathbf{v}=\mathbf{0}$ for its eigenvector.

**Two facts the book stresses:**
- Eigenvectors are **defined only up to a nonzero scale factor** — if $\mathbf{v}$ works, so does $5\mathbf{v}$. What matters is the *direction* (the line through the origin), not the length. So we're free to fix one convenient component (e.g. set the first entry to 1).
- For a **real** matrix the characteristic polynomial has real coefficients, so **complex eigenvalues come in conjugate pairs** $\lambda, \lambda^{*}$ — and their eigenvectors are conjugates too. This is why oscillation appears: a complex $\lambda=\sigma\pm j\omega$ plugged into the system's $e^{\lambda t}$ behavior gives, via [[Euler's Formula]], a decaying/growing sinusoid $e^{\sigma t}(\cos\omega t \pm j\sin\omega t)$. **Eigenvalues literally set the frequencies a system can ring at.**

### Worked example — the book's Chapter 5 matrix

Take $A=\begin{bmatrix}0&1\\8&-2\end{bmatrix}$ (the linearized inverted-pendulum model, Eq. 5.16).

**Step 1 — characteristic polynomial** (using $\det\begin{bmatrix}a&b\\c&d\end{bmatrix}=ad-bc$):
$$\det(\lambda I - A)=\det\begin{bmatrix}\lambda&-1\\-8&\lambda+2\end{bmatrix}=\lambda(\lambda+2)-(-1)(-8)=\lambda^2+2\lambda-8=(\lambda-2)(\lambda+4).$$

**Step 2 — eigenvalues:** $\lambda_1=2,\ \lambda_2=-4$.

**Step 3 — eigenvectors.** For $\lambda_1=2$, solve $(\,2I-A)\mathbf{v}_1=\begin{bmatrix}2&-1\\-8&4\end{bmatrix}\mathbf{v}_1=\mathbf{0}$. Both rows say $2v_{11}=v_{21}$; fix $v_{11}=1\Rightarrow v_{21}=2$:
$$\mathbf{v}_1=\begin{bmatrix}1\\2\end{bmatrix}.$$
For $\lambda_2=-4$, solve $\begin{bmatrix}-4&-1\\-8&-2\end{bmatrix}\mathbf{v}_2=\mathbf{0}$; both rows say $-4v_{12}=v_{22}$; fix $v_{12}=1\Rightarrow v_{22}=-4$:
$$\mathbf{v}_2=\begin{bmatrix}1\\-4\end{bmatrix}.$$
**Interpretation:** $\lambda_1=2>0$ means a *growing* mode (the pendulum tips over — unstable), while $\lambda_2=-4<0$ is a *decaying* mode. The sign of the eigenvalue is the verdict on stability. This is exactly the analysis Chapter 5 builds.

### Diagonalization — why eigenvectors are worth the trouble

Stack the eigenvectors as columns of $V$ and the eigenvalues on the diagonal of $\Lambda$:
$$A = V\Lambda V^{-1}, \qquad \Lambda=\begin{bmatrix}\lambda_1&0\\0&\lambda_2\end{bmatrix}.$$
This says: *change to eigenvector coordinates ($V^{-1}$), simply scale each axis ($\Lambda$), change back ($V$).* The payoff is that **powers become trivial**, because the inner $V^{-1}V$ cancel:
$$A^n = V\Lambda^n V^{-1}, \qquad \Lambda^n=\begin{bmatrix}\lambda_1^n&0\\0&\lambda_2^n\end{bmatrix}.$$
Raising a full matrix to the 100th power is brutal; raising a diagonal one is just raising each $\lambda$ to the 100th. This is the **modal decomposition**: the system's response splits into independent modes $\propto \lambda_i^{n}$ (discrete time) or $\propto e^{\lambda_i t}$ (continuous time), each living on its own eigenvector. The book calls working in these coordinates the **modal representation**, and the change of basis a **similarity transformation**. It is the entire engine of Chapter 5.

## Terms Experts Use

- **Eigenvalue $\lambda$** — the scale factor; a.k.a. **characteristic root, characteristic value, natural frequency, mode, pole** (across contexts). The set of all eigenvalues is the **spectrum**.
- **Eigenvector $\mathbf{v}$** — the invariant direction; a.k.a. **characteristic vector**. Defined **up to scale**.
- **Characteristic equation / polynomial** — $\det(\lambda I-A)=0$ and its expansion.
- **Algebraic multiplicity** — how many times a $\lambda$ repeats as a root.
- **Diagonalization** $A=V\Lambda V^{-1}$ · **similarity transformation** (change of basis $V^{-1}AV$) · **modal coordinates / modal representation**.
- **Stability read-off:** continuous-time stable ⇔ all $\operatorname{Re}\{\lambda\}<0$; discrete-time stable ⇔ all $|\lambda|<1$ (the book's asymptotic-stability criterion).
- **Eigenvalue placement** — designing feedback so the *closed-loop* eigenvalues sit where you want (Chapter 6).

## Worked Example (your turn to verify)

Check the diagonalization of the book matrix above. With $V=\begin{bmatrix}1&1\\2&-4\end{bmatrix}$, confirm $AV=V\Lambda$ column by column:
- Column 1: $A\mathbf{v}_1=\begin{bmatrix}0&1\\8&-2\end{bmatrix}\begin{bmatrix}1\\2\end{bmatrix}=\begin{bmatrix}2\\4\end{bmatrix}=2\begin{bmatrix}1\\2\end{bmatrix}=\lambda_1\mathbf{v}_1.$ ✓
- Column 2: $A\mathbf{v}_2=\begin{bmatrix}0&1\\8&-2\end{bmatrix}\begin{bmatrix}1\\-4\end{bmatrix}=\begin{bmatrix}-4\\16\end{bmatrix}=-4\begin{bmatrix}1\\-4\end{bmatrix}=\lambda_2\mathbf{v}_2.$ ✓

Each eigenvector is merely scaled — the defining property, made concrete.

## Checkpoint

Tested in [[Quiz P1 Linear Algebra]]. Cold, you should be able to:
1. State $A\mathbf{v}=\lambda\mathbf{v}$ and explain it as "a direction the matrix only scales."
2. Find eigenvalues via $\det(\lambda I-A)=0$ for a 2×2 matrix.
3. Find an eigenvector for a given eigenvalue (and know it's only defined up to scale).
4. Explain why complex eigenvalues ⇒ oscillation (link to [[Euler's Formula]]).
5. Write $A=V\Lambda V^{-1}$ and explain why it makes $A^n$ easy — the meaning of "modes."

## My Understanding

_(Your space — the target instinct: "eigenvalues = the natural behaviors a system settles into.")_

## Open Questions

- [ ] _e.g. "What if a matrix doesn't have enough independent eigenvectors to diagonalize?" (defective matrices / Jordan form) — log in [[Learning Log]]._
