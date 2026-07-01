---
tags: [learning-progress, assessment, math-foundations]
sources: [discussion-2026-07-01]
created: 2026-07-01
updated: 2026-07-01
---

# Problems P1 Linear Algebra

Progressive drill set for Module P1: [[Vectors And Dot Products]] · [[Matrices And Linear Transformations]] · [[Eigenvalues And Eigenvectors]]. **Formative, open-book** — build skill before the closed-book gate [[Quiz P1 Linear Algebra]]. Share each solution; I run the [[Remediation Loop]] on every miss. Weaknesses logged in [[Learning Log]].

**Complexity ladder (per topic):** **L1** mechanics → **L2** operations → **L3** structure → **L4** applied (satellite-comms / control flavored).

## A · Vectors & Dot Products

- **A1 (L1).** For $\mathbf a=[2,-1,2]^T$, $\mathbf b=[1,2,2]^T$: compute $\mathbf a\cdot\mathbf b$, $\lVert\mathbf a\rVert$, $\lVert\mathbf b\rVert$, and the angle between them.
- **A2 (L2).** Project $\mathbf c=[3,4]^T$ onto $\mathbf a=[1,0]^T$. Give the projection **and** the residual $\mathbf r=\mathbf c-\text{proj}$, then verify $\mathbf r\perp\mathbf a$.
- **A3 (L3).** From $\mathbf u=[1,1,0]^T$, $\mathbf v=[1,0,1]^T$ build an **orthonormal** basis for their span (Gram–Schmidt). Verify your two vectors are orthonormal.
- **A4 (L4 — correlation/matched filter).** Sampled signals $\mathbf s=[1,1,-1,-1]^T$, $\mathbf r=[1,1,1,-1]^T$. Compute the normalized correlation $\rho=\dfrac{\mathbf s\cdot\mathbf r}{\lVert\mathbf s\rVert\lVert\mathbf r\rVert}$ and say what $\rho=1$ vs $\rho=0$ would mean for detection.

## B · Matrices & Transformations

- **B1 (L1).** $A=\begin{bmatrix}1&2\\3&4\end{bmatrix}$, $\mathbf x=[1,-1]^T$: compute $A\mathbf x$ the row-dot way and the column-combination way; they must match.
- **B2 (L2).** For $A=\begin{bmatrix}2&1\\1&2\end{bmatrix}$: find $\det A$ and $A^{-1}$.
- **B3 (L3).** Solve $\begin{cases}2x+y=5\\ x+3y=10\end{cases}$ by matrix inverse; state the rank of the coefficient matrix and why the solution is unique.
- **B4 (L4 — rotation ≡ complex multiply).** $R(\theta)=\begin{bmatrix}\cos\theta&-\sin\theta\\\sin\theta&\cos\theta\end{bmatrix}$. (a) Show $R(\theta)[1,0]^T=[\cos\theta,\sin\theta]^T$. (b) Prove $R(\theta)R(\phi)=R(\theta+\phi)$. (c) Explain how this is the $2\times2$ real form of multiplying by $e^{j\theta}$ from [[Euler's Formula]].

## C · Eigenvalues & Eigenvectors

- **C1 (L1).** $A=\begin{bmatrix}3&1\\0&2\end{bmatrix}$ (triangular): find both eigenvalues and an eigenvector for each.
- **C2 (L2).** $A=\begin{bmatrix}0&-1\\1&0\end{bmatrix}$ (90° rotation): find the eigenvalues and say what kind of time behavior a complex-conjugate, purely-imaginary pair implies.
- **C3 (L3).** $A=\begin{bmatrix}2&1\\1&2\end{bmatrix}$: use diagonalization ($\lambda=1,3$) to compute $A^4\mathbf x$ for $\mathbf x=[1,0]^T$ **without** multiplying $A$ four times. Verify against a direct $A^4$.
- **C4 (L4 — continuous-time stability).** For $\dot{\mathbf x}=A\mathbf x$ with $A=\begin{bmatrix}0&1\\-2&-3\end{bmatrix}$: (a) find the eigenvalues; (b) is the system asymptotically stable, and by what criterion; (c) describe the mode behavior. (This is the P1→P2 bridge — see [[Differential Equations]].)

---

<!-- ============================ SOLUTION KEY (hidden) — I grade + run the Remediation Loop ============================
A1: a·b=2-2+4=4. ||a||=√(4+1+4)=3, ||b||=√(1+4+4)=3. cosθ=4/9≈0.444 → θ≈63.6°.
A2: proj=((c·a)/(a·a))a=(3/1)[1,0]=[3,0]. r=c-proj=[0,4]. r·a=0 ✓ (residual ⟂ direction projected onto).
A3: e1=u/||u||=[1,1,0]/√2. w=v-(v·e1)e1; v·e1=1/√2; (v·e1)e1=(1/2)[1,1,0]=[.5,.5,0]; w=[.5,-.5,1]; ||w||=√1.5. e2=[.5,-.5,1]/√1.5. Check e1·e2=(1/√2√1.5)(.5-.5+0)=0 ✓, both unit.
A4: s·r=1+1-1+1=2. ||s||=2, ||r||=2. ρ=2/4=0.5. ρ=1 ⇔ identical direction = perfect match (matched-filter max); ρ=0 ⇔ orthogonal = no correlation. Preview Ch 13.
B1: row: [1-2, 3-4]=[-1,-1]. col: 1[1,3]-1[2,4]=[-1,-1] ✓.
B2: det=4-1=3. A^{-1}=(1/3)[[2,-1],[-1,2]].
B3: A=[[2,1],[1,3]], det=5, inv=(1/5)[[3,-1],[-1,2]]. x=inv[5,10]=(1/5)[15-10,-5+20]=(1/5)[5,15]=[1,3]. rank=2 (det≠0 ⇒ full rank ⇒ unique solution).
B4: (a) direct. (b) product entries use cos θ cos φ - sin θ sin φ = cos(θ+φ), etc. → R(θ+φ). (c) rotating a vector by θ = multiplying its complex number by e^{jθ}; magnitudes preserved, angles add — same law as P0.
C1: eigenvalues on diagonal 3,2. λ=3: (A-3I)=[[0,1],[0,-1]] → v=[1,0]. λ=2: (A-2I)=[[1,1],[0,0]] → x+y=0 → v=[1,-1].
C2: char λ²+1=0 → λ=±j. Pure-imaginary conjugate pair ⇒ pure (undamped) oscillation — marginal stability, rings forever. eigenvectors [1,∓j].
C3: x=[1,0]=α[1,-1]+β[1,1]; α+β=1,-α+β=0 → α=β=1/2. A^4 x = (1/2)1^4[1,-1]+(1/2)3^4[1,1]=[.5,-.5]+[40.5,40.5]=[41,40]. Direct: A²=[[5,4],[4,5]], A⁴=[[41,40],[40,41]] → [41,40] ✓.
C4: det([[-λ,1],[-2,-3-λ]])=λ²+3λ+2=(λ+1)(λ+2) → λ=-1,-2. (b) stable: all Re λ<0 (left half-plane). (c) two real decaying modes e^{-t}, e^{-2t}, no oscillation (overdamped).
Remediation cues: forgot √ in norm → procedural; projected onto wrong denominator (a·a) → conceptual, revisit [[Vectors And Dot Products]] projection; AB vs BA confusion → definitional (noncommutativity); took eigenvector length as meaningful → conceptual (defined up to scale); read complex λ as instability → conceptual, it's the SIGN of Re λ that decides, revisit [[Eigenvalues And Eigenvectors]].
========================================================================================================= -->
