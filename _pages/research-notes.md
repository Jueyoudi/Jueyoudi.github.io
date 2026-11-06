
---
layout: single
title: "Research Notes"
permalink: /research-notes/
author_profile: true
---

This page contains selected mathematical notes, derivations, and numerical investigations related to my research in optimal control and dynamical systems.

These materials are part of ongoing or unpublished research and are not peer-reviewed publications.

---

## 1. Moment-Based Representation of Ensemble Systems

**Topics:** Ensemble Control, Orthogonal Polynomials, Finite-Dimensional Approximation

Consider a parameter-dependent dynamical system:

$$
\dot{x}(t,\beta)
=
A(\beta)x(t,\beta)+B(\beta)u(t).
$$

A moment-based representation is introduced as

$$
m_k(t)
=
\int_{\Omega}
\phi_k(\beta)x(t,\beta)\,d\beta,
$$

where $\phi_k(\beta)$ denotes a selected basis function.

By retaining a finite number of moments, the original ensemble system can be approximated by a finite-dimensional dynamical system.

### Topics of Investigation

- Orthogonal polynomial representations
- Moment dynamics and finite-dimensional truncation
- Terminal state approximation
- Numerical optimal control

**Selected derivations (PDF):** Coming soon.

---

## 2. State Constraints in Ensemble Optimal Control

**Topics:** Constrained Control, Moment Conditions, Positive Semidefinite Matrices

Consider state constraints of the form

$$
h(x(t,\beta)) \geq 0,
\quad \forall \beta \in \Omega.
$$

Enforcing these constraints over a continuous parameter domain presents a computational challenge.

My research explores moment-based constraint formulations, including weighted integral conditions and positive semidefinite matrix representations.

### Topics of Investigation

- Integral conditions for state constraints
- Necessary and sufficient conditions
- Positive semidefinite moment matrices
- Effects of finite-dimensional truncation
- Numerical feasibility and constraint satisfaction

**Selected derivations (PDF):** Coming soon.

---

## 3. Numerical Approximation and Error Analysis

**Topics:** Numerical Control, Truncation Error, Approximation Accuracy

Finite-dimensional approximations play an important role in computational ensemble control.

I am interested in investigating how numerical solutions obtained from truncated moment systems relate to the original parameter-dependent dynamical systems.

### Topics of Investigation

- Terminal approximation errors
- Effects of truncation order
- Numerical convergence behavior
- Computational complexity

**Numerical analysis notes (PDF):** Coming soon.

---

## Disclaimer

The materials presented here are selected research notes and do not constitute peer-reviewed publications.

Some derivations and numerical results are part of ongoing collaborative research and will be made publicly available only when appropriate.
