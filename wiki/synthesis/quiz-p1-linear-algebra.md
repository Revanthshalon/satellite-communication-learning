---
tags: [learning-progress, assessment, math-foundations]
sources: [discussion-2026-06-30]
created: 2026-06-30
updated: 2026-06-30
---

# Quiz P1 Linear Algebra

Strict checkpoint for Module P1: [[Vectors And Dot Products]] · [[Matrices And Linear Transformations]] · [[Eigenvalues And Eigenvectors]]. Graded under the rubric in [[Score Log]] (pass ≥ 80%, no credit for right answer + wrong reasoning, units/definitions count, show your work). Passing unlocks **P2 Calculus & Differential Equations** in [[Curriculum]].

**Gate reminder:** P1 is only attempted *after* [[Quiz P0 Math Toolkit]] is passed.

**Format:** 10 questions, 100 points. Closed-book. Tell me *"I'm ready for the P1 quiz"* and answer in chat; I deliver them in 3 batches, grade strictly, and append your row to [[Score Log]].

**Warm up first (open-book):** [[Problems P1 Linear Algebra]] — the L1→L4 drill ladder. Every solution you share there runs through the [[Remediation Loop]] before you sit this gate.

## Section A — Vectors & Dot Products (30 pts)

1. **(6 pts)** For $\mathbf{a}=\begin{bmatrix}1\\2\\2\end{bmatrix}$, $\mathbf{b}=\begin{bmatrix}3\\0\\-4\end{bmatrix}$: compute (a) $\mathbf{a}\cdot\mathbf{b}$, (b) $\lVert\mathbf{a}\rVert$, (c) $\lVert\mathbf{b}\rVert$.
2. **(8 pts)** Using your Q1 results, find the angle $\theta$ between $\mathbf{a}$ and $\mathbf{b}$. Show the dot-product formula you used.
3. **(8 pts)** Are $\begin{bmatrix}2\\1\end{bmatrix}$ and $\begin{bmatrix}-1\\2\end{bmatrix}$ orthogonal? Show the test, and explain in one sentence what orthogonality *means*.
4. **(8 pts)** Project $\mathbf{c}=\begin{bmatrix}4\\2\end{bmatrix}$ onto $\mathbf{a}=\begin{bmatrix}3\\0\end{bmatrix}$. Show the formula and explain in one sentence why projection gives the "best approximation along $\mathbf{a}$."

## Section B — Matrices & Transformations (35 pts)

5. **(9 pts)** For $A=\begin{bmatrix}1&2\\3&4\end{bmatrix}$, $\mathbf{x}=\begin{bmatrix}2\\1\end{bmatrix}$: compute $A\mathbf{x}$ **two ways** — the row-dot view and the column-combination view. They must match.
6. **(8 pts)** With $A$ from Q5 and $B=\begin{bmatrix}0&1\\1&0\end{bmatrix}$, compute $AB$ and $BA$. State explicitly whether they're equal and what that tells you.
7. **(8 pts)** For $A=\begin{bmatrix}4&2\\1&3\end{bmatrix}$: compute $\det A$, state whether $A$ is invertible and why, and give the rank.
8. **(10 pts)** Define **linear independence**, **span**, **basis**, and **rank** — each in one sentence — and explain how they're connected (the single underlying idea).

## Section C — Eigenvalues & Eigenvectors (35 pts)

9. **(20 pts)** For $A=\begin{bmatrix}2&1\\1&2\end{bmatrix}$: (a) write and solve the characteristic equation $\det(\lambda I-A)=0$ for both eigenvalues; (b) find an eigenvector for each; (c) note that the eigenvector is only defined up to what?
10. **(15 pts)** (a) A real $2\times2$ matrix has eigenvalues $\lambda = -1 \pm 2j$. Explain, citing [[Euler's Formula]], what kind of time behavior these produce and whether the system is stable. (b) Write the diagonalization $A=V\Lambda V^{-1}$ in general form and explain in one sentence why it makes $A^n$ easy to compute.

---

_When you're done I total the points, assign a band (A/B/C/D-F), diagnose every miss, and log it. Below ~80% the P2 module stays locked and I'll route you back to the exact sections to redo._

<!-- ============================ GRADER ANSWER KEY (hidden in rendered view) ============================
Total 100. Strict: correct final value from flawed reasoning = 0 for that part. Missing/incorrect definitions lose points even if arithmetic is right.

Q1 (6, 2 each): (a) a·b = 1·3 + 2·0 + 2·(-4) = 3 + 0 - 8 = -5. (b) ||a|| = sqrt(1+4+4)=sqrt(9)=3. (c) ||b||=sqrt(9+0+16)=sqrt(25)=5.
Q2 (8): cosθ = (a·b)/(||a|| ||b||) = -5/(3·5) = -1/3 ≈ -0.333 (5). θ = arccos(-1/3) ≈ 109.47° (3). Formula must be shown. Negative cos → obtuse angle is correct.
Q3 (8): dot = 2·(-1) + 1·2 = -2 + 2 = 0 → YES orthogonal (5). Meaning (3): perpendicular / no shared direction / independent directions.
Q4 (8): proj = ((c·a)/(a·a)) a. c·a = 4·3 + 2·0 = 12; a·a = 9. proj = (12/9)[3,0]^T = (4/3)[3,0]^T = [4,0]^T (5). Explanation (3): it's the point on a's line closest to c (perpendicular drop minimizes distance), i.e. least-squares best fit along a.
Q5 (9): Row view: [1·2+2·1, 3·2+4·1]^T = [4, 10]^T (4). Column view: 2[1,3]^T + 1[2,4]^T = [2,6]^T+[2,4]^T = [4,10]^T (4). Match stated (1). Either order fine; both must be shown.
Q6 (8): AB = [[1·0+2·1, 1·1+2·0],[3·0+4·1, 3·1+4·0]] = [[2,1],[4,3]] (3). BA = [[0·1+1·3, 0·2+1·4],[1·1+0·3, 1·2+0·4]] = [[3,4],[1,2]] (3). Not equal → matrix multiplication is not commutative; order = order of operations (2).
Q7 (8): det = 4·3 - 2·1 = 10 (3). Nonzero → invertible/nonsingular (3). Rank = 2 (full rank) (2).
Q8 (10): Lin. indep. — no vector is a linear combination of the others / only the all-zero combination gives 0 (2.5). Span — all linear combinations reachable from a set (2.5). Basis — a minimal independent set that spans the space; n vectors for R^n (2.5). Rank — number of independent columns/dimensions of output (2.5). Connection: all measure "how many independent directions" — a basis is a maximal independent spanning set; rank = size of a basis for the column space.
Q9 (20): (a) det([[2-λ,1],[1,2-λ]]) = (2-λ)^2 - 1 = λ^2 -4λ +3 = (λ-1)(λ-3) → λ1=1, λ2=3 (8). 
    (b) λ1=1: (A-1I)v=[[1,1],[1,1]]v=0 → v1=[1,-1]^T (or scalar multiple) (4). λ2=3: (A-3I)v=[[-1,1],[1,-1]]v=0 → v2=[1,1]^T (4). 
    (c) up to a nonzero scale factor (direction only) (4). 
    [Note: this is a symmetric matrix, so eigenvectors are orthogonal: [1,-1]·[1,1]=0 — bonus insight, not required.]
Q10 (15): (a) λ = -1 ± 2j → behavior e^{λt} = e^{-t}(cos2t ± j sin2t) via Euler: a DECAYING OSCILLATION, freq 2 rad/s, envelope e^{-t} (6). Stable because Re{λ} = -1 < 0 (3). 
    (b) A = VΛV^{-1}, V = eigenvectors as columns, Λ = diag(eigenvalues) (3). A^n = VΛ^n V^{-1} because inner V^{-1}V cancel; Λ^n is just each λ_i^n — powers of a diagonal matrix are trivial (3).
Banding: A 90-100, B 80-89 PASS, C 70-79 FAIL-close, <70 remediate. Below 80 → keep P2 locked; route misses to the cited concept pages.
========================================================================================================= -->
