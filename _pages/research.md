---
layout: single
title: "Research"
permalink: /research/
author_profile: true
---

## Research Interests

My research interests lie primarily in **optimal control, ensemble control, dynamical systems, and numerical methods for control and optimization**.

I am particularly interested in mathematical and computational approaches to controlling parameter-dependent dynamical systems, including moment-based representations, constrained optimal control, and numerical approximation.

My current research interests include:

- **Optimal Control and Dynamical Systems**
- **Ensemble Control and Moment-Based Methods**
- **State-Constrained Optimal Control**
- **Numerical Optimization and Computational Control**
- **Truncation Error Analysis and Approximation Methods**

My research combines mathematical analysis with numerical implementation, with an emphasis on developing computationally tractable methods for high-dimensional and parameter-dependent control problems.

---

## Research Experience

### 1. Constrained Ensemble Control

**Research Assistant | August 2025 – Present**

My current research focuses on incorporating state constraints into ensemble optimal control problems through moment-based representations.

A key challenge is that ensemble systems consist of continuously parameterized dynamical systems, while state constraints may need to hold across the entire parameter domain.

I investigate how these constraints can be represented and analyzed in moment coordinates.

My work includes:

- Reformulating constrained ensemble control problems using moment-based representations.
- Deriving finite-dimensional moment dynamics and associated control formulations.
- Investigating the relationship between pointwise state constraints, integral conditions, and positive semidefinite moment matrices.
- Constructing structured matrix representations, including Hankel-type constraints.
- Analyzing truncation errors and convergence properties of moment-based approximations.

An important part of this research is studying when moment-based constraints provide necessary or sufficient conditions for pointwise state feasibility.

I am also interested in how the number of retained moments and the order of constraint matrices affect numerical feasibility and approximation accuracy.

**Related Project:** [State-Constrained Ensemble Optimal Control](/portfolio/state-constrained-control/)

---

### 2. Error Analysis of Truncated Bilinear Ensembles

**Research Assistant | March 2025 – May 2025**

This project investigated approximation errors in finite-dimensional representations of bilinear ensemble systems.

Moment-based methods provide a computational approach to representing parameter-dependent dynamical systems through truncated moment sequences.

However, finite-dimensional truncation introduces approximation errors that must be analyzed to understand the accuracy of the resulting control system.

Building on an existing explicit truncation-error bound for linear ensembles, I derived a corresponding upper bound for bilinear ensemble systems under piecewise-constant control inputs.

The research focused on:

- Truncation of parameter-dependent dynamical systems
- Error bounds for bilinear ensemble models
- Piecewise-constant control inputs
- Numerical approximation of ensemble dynamics

This project strengthened my interest in the mathematical foundations of numerical methods for optimal control.

---

### 3. Numerical Methods for Pattern Control

**Research Assistant | November 2024 – March 2025**

This project investigated numerical difficulties arising in the pattern control of ensemble harmonic oscillators.

The objective was to steer ensembles toward prescribed geometric configurations using shared control inputs.

A major computational challenge was the ill-conditioning of the control matrix, particularly when the controllability Gramian became nearly singular.

My work focused on improving numerical stability through reformulation of the system representation.

The research involved:

- Ensemble harmonic oscillator models
- Geometric pattern steering
- Controllability Gramian conditioning
- Numerical stability and system reformulation
- Moment-based numerical control

The numerical simulations included transformations between different geometric patterns, illustrating the ability of shared control inputs to coordinate an ensemble of parameter-dependent systems.

**Related Project:** [Pattern Control of Ensemble Dynamical Systems](/portfolio/pattern-control/)

---

### 4. Numerical Methods for Distributional Control

**Research Assistant | November 2024 – January 2025**

This project investigated the numerical control of ensemble distributions using moment-based methods.

The objective was to steer an ensemble from an initial distribution toward a prescribed target distribution.

A central challenge was the numerical instability associated with the control matrix obtained from the monomial moment representation.

In particular, the resulting Hilbert-like matrix could become severely ill-conditioned, making the computation of control inputs difficult.

To address this issue, I investigated alternative moment bases and their effects on the structure and numerical properties of the moment system.

My work included:

- Deriving moment dynamics for parameter-dependent linear ensembles.
- Transforming the original ensemble model into a finite-dimensional moment system.
- Investigating monomial, Legendre, and Chebyshev polynomial bases.
- Comparing the numerical properties of different moment representations.
- Improving numerical conditioning through basis selection.

The numerical experiments included steering a truncated Gaussian distribution toward a truncated Gaussian mixture distribution.

I also explored distributional control formulations involving aggregated measurements without individual system labels.

**Related Project:** [Distributional Control via Moment-Based Representations](/portfolio/distribution-steering/)

---

### 5. Iterative Optimal Control for Inhomogeneous Spin Ensembles

**Research Assistant | September 2024 – December 2024**

This project focused on the numerical solution of fixed-endpoint optimal control problems for inhomogeneous spin ensembles.

The objective was to compute control inputs capable of steering a collection of systems with parameter-dependent dynamics toward prescribed terminal states.

I applied an iterative optimal control method to solve the fixed-endpoint control problem.

The research provided experience in:

- Iterative optimal control methods
- Fixed-endpoint control formulations
- Parameter-dependent dynamical systems
- Numerical computation of optimal controls

This work introduced me to computational approaches for controlling large populations of dynamical systems under shared control inputs.

---

### 6. Numerical Reproduction of Iterative Optimal Control for Nonlinear Systems

**Research Assistant | September 2024 – December 2024**

This project involved reproducing and studying iterative optimal control methods for nonlinear dynamical systems.

The computational approach used linearized representations of the nonlinear dynamics to simplify the control formulation.

Through this reformulation, the objective function could be expressed in a quadratic form, making the resulting numerical computations more manageable.

My work involved:

- Nonlinear dynamical systems
- Linearization-based representations
- Quadratic objective functions
- Iterative optimal control algorithms
- Numerical implementation and simulation

This project provided an early foundation for my subsequent research in ensemble control and numerical optimal control.

---

## Selected Research Projects and Simulations

The following projects provide more detailed mathematical formulations, numerical experiments, and simulation results.

### Pattern Control of Ensemble Dynamical Systems

Moment-based optimal control for geometric pattern transformations, including Triangle → Square → Maple Leaf.

[View Project and Simulation](/portfolio/pattern-control/)

### Distributional Control via Moment-Based Representations

Derivation and numerical investigation of moment systems using different polynomial bases, with applications to Gaussian-to-Gaussian-mixture distribution steering.

[View Project and Simulation Results](/portfolio/distribution-steering/)

### State-Constrained Ensemble Optimal Control

Moment-based state constraint representations, positive semidefinite matrix conditions, convergence analysis, and numerical experiments involving constrained trajectories.

[View Project and Simulation Results](/portfolio/state-constrained-control/)

---

## Computational Methods and Tools

My research involves mathematical modeling, numerical optimization, and computational simulation.

**Programming:** MATLAB, Python

**Mathematical and Computational Methods:**

- Optimal control
- Numerical integration
- Moment-based approximation
- Orthogonal polynomial representations
- Constrained optimization
- Truncation error analysis
- Iterative numerical methods

---

## Future Research Directions

For my doctoral studies, I hope to continue investigating mathematical and computational methods for controlling complex dynamical systems.

I am particularly interested in:

- Optimal control of high-dimensional and parameter-dependent systems
- State-constrained and nonlinear optimal control
- Numerical approximation and computational efficiency
- Connections between dynamical systems, optimization, and control theory

My long-term goal is to develop a deeper understanding of optimal control theory while exploring computational methods that make challenging control problems more tractable.

---

## Research Notes

Selected mathematical derivations and numerical investigations are available on my [Research Notes](/research-notes/) page.

Some of these materials are part of ongoing collaborative research and have not been formally published.
