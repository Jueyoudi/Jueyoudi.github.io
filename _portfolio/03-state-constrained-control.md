
---
title: "State-Constrained Ensemble Optimal Control"
excerpt: "Investigating moment-based formulations and numerical methods for ensemble optimal control under state constraints."
collection: portfolio
permalink: /portfolio/state-constrained-control/
---

## Overview

This project investigates state-constrained optimal control problems for parameter-dependent dynamical systems.

Unlike conventional optimal control problems involving a single dynamical system, ensemble control considers a family of systems governed by a common control input.

A key challenge is to ensure that state constraints are satisfied across the entire ensemble while optimizing the control objective.

My work explores moment-based formulations and numerical approaches for representing and incorporating such constraints.

## Problem Formulation

Consider an ensemble of dynamical systems:

$$
\dot{x}(t,\beta)
=
A(\beta)x(t,\beta)+B(\beta)u(t),
$$

where $\beta \in \Omega$ is a parameter and $u(t)$ is a shared control input.

A representative optimal control problem is

$$
\min_{u} \int_0^T \|u(t)\|^2\,dt,
$$

subject to the ensemble dynamics, prescribed boundary conditions, and state constraints of the form

$$
h(x(t,\beta)) \geq 0,
\quad \forall \beta \in \Omega.
$$

The continuous parameter domain makes direct enforcement of the constraints computationally challenging.

## Moment-Based Approximation

To construct a finite-dimensional representation, the ensemble state is expressed through moments:

$$
m_k(t)
=
\int_{\Omega}
\phi_k(\beta)x(t,\beta)\,d\beta,
$$

where $\phi_k(\beta)$ denotes a selected basis function.

The resulting truncated moment system provides a finite-dimensional approximation for numerical optimization.

However, constraints imposed on a finite number of moments do not necessarily guarantee pointwise state feasibility for the original ensemble.

This motivates the investigation of additional conditions for representing state constraints.

## Approaches to State Constraints

### 1. Integral Constraints

One approach is to formulate weighted integral conditions:

$$
\int_{\Omega}
\phi_k(\beta)
h(x(t,\beta))\,d\beta
\geq 0.
$$

These conditions provide a moment-based representation of certain aspects of the state constraints.

An important question is how much information a finite number of such conditions provides about pointwise feasibility.

### 2. Positive Semidefinite Matrix Conditions

Another approach explores positive semidefinite matrix constraints associated with moment sequences.

For suitable moment representations, matrices constructed from the moments may be required to satisfy

$$
M_N(m) \succeq 0.
$$

Such conditions are related to classical moment problems and can provide structured constraints in numerical formulations.

Their interpretation and sufficiency depend on the underlying moment representation and the state domain.

### 3. Effect of Truncation Order

I am interested in understanding how the truncation order affects:

- The representation of state constraints
- Numerical feasibility
- Approximation accuracy
- Computational complexity

## Numerical Investigation

The numerical study focuses on comparing different finite-dimensional constraint formulations and examining their effects on the resulting optimal control solutions.

**Numerical results and constraint comparison figures:** To be added.

## Methods and Tools

- Ensemble optimal control
- Moment-based approximations
- Orthogonal polynomial representations
- Positive semidefinite constraints
- Constrained numerical optimization
- MATLAB

## Research Status

Ongoing, unpublished research.

Selected mathematical derivations and numerical experiments may be shared as research notes.
