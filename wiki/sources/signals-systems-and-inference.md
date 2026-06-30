---
tags: [signal-processing, modulation-coding, probability, estimation, detection, source]
sources: [Signals, Systems and Inference.pdf]
created: 2026-06-30
updated: 2026-06-30
---

# Signals, Systems And Inference

**Source:** Signals, Systems and Inference.pdf (converted to text via the `pdf-to-text` skill / `pdftotext` → `output/Signals, Systems and Inference.txt`)
**Authors:** Alan V. Oppenheim & George C. Verghese (MIT)
**Publisher / Year:** Pearson, 2016 (ISBN 978-0-13-394328-3)
**Type:** Textbook (advanced-undergraduate, MIT EECS)

## Summary

A textbook that fuses three traditionally separate subjects — **signals & systems**, **probability**, and **inference** — into one arc. It begins with deterministic signal/system description (Fourier, Laplace, z-transforms), moves through state-space modeling and control, introduces randomness (probability, random variables, random processes), and culminates in **model-based inference**: estimation, hypothesis testing, optimal filtering (Wiener/Kalman), and signal detection (matched filtering). This inference machinery is the mathematical core of communications — including satellite links.

The authors state two formal prerequisites (p. xi): (1) an introductory course in time- and frequency-domain analysis of signals and systems (itself building on differential equations and basic linear algebra), and (2) an introductory course in probability.

## Key Claims

- Signals, systems, and probability are most powerful when taught **together**, not as isolated specialties.
- Modern engineering inference is **model-based**: build a model of signal + noise, then derive the optimal estimator/detector.
- The same LTI / Fourier machinery that describes deterministic signals extends to **random processes** via correlation functions and power spectral density.
- Optimal linear estimation (LMMSE), Wiener filtering, and the Kalman filter are unified views of the same least-squares idea.
- Detection of a known signal in Gaussian noise leads directly to the **matched filter**, the backbone of digital receivers and radar.

## Structure (13 Chapters)

1. Signals and Systems · 2. Amplitude, Phase, and Group Delay · 3. Pulse-Amplitude Modulation · 4. State-Space Models · 5. LTI State-Space Models · 6. State Observers and State Feedback · 7. Probabilistic Models · 8. Estimation · 9. Hypothesis Testing · 10. Random Processes · 11. Power Spectral Density · 12. Signal Estimation (Wiener/Kalman) · 13. Signal Detection (matched filtering).

## Concepts Covered

This source seeds the entire learning curriculum. See [[Curriculum]] for the full module map. Prerequisite concepts being built first:

- [[Complex Numbers]] — the number system underlying all signal analysis
- [[Euler's Formula]] — the bridge between exponentials and sinusoids
- [[Sinusoids And Phasors]] — how signals are represented and manipulated
- [[Linear Algebra Essentials]] — vectors, matrices, eigenvalues (for state-space)
- [[Calculus And Differential Equations]] — rates, integrals, system dynamics
- [[Signals And Systems Fundamentals]] — LTI systems, convolution, Fourier
- [[Probability Fundamentals]] — randomness, random variables, distributions

## Notes

The 6 MB PDF (555 pages) was converted to a 1.3 MB plain-text file for study. Figures/equations rendered imperfectly in text extraction; derivations in the wiki are reconstructed and verified, not copied verbatim.
