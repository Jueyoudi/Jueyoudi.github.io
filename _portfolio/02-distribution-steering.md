
---
title: "Distribution Steering via Moment-Based Optimal Control"
excerpt: "Steering parameter-dependent ensembles toward prescribed target distributions using moment-based representations."
collection: portfolio
permalink: /portfolio/distribution-steering/
---

## Overview

This project explores the numerical control of parameter-dependent dynamical systems toward prescribed terminal distributions.

The objective is to design a common control input that steers an ensemble from an initial configuration toward a desired distribution.

My numerical experiments include the transformation of an initially unimodal distribution toward a bimodal target.

## Mathematical Formulation

Consider an ensemble of dynamical systems:

$$
\dot{x}(t,\beta)
=
f(x(t,\beta),u(t),\beta),
$$

where $\beta$ represents the parameter distinguishing individual systems within the ensemble.

The objective is to steer the ensemble toward a desired terminal configuration while optimizing a prescribed performance criterion.

## Moment-Based Representation

To obtain a finite-dimensional approximation, the ensemble state is represented using moments:

$$
m_k(t)
=
\int_{\Omega}
\phi_k(\beta)x(t,\beta)\,d\beta.
$$

Here, $\phi_k(\beta)$ denotes a basis function, such as a Legendre or Chebyshev polynomial.

A truncated moment representation is used to approximate the original ensemble control problem and construct a numerical optimization problem.

## Numerical Experiments

### Unimodal-to-Bimodal Distribution Steering

One numerical experiment investigates the transformation of an initially unimodal configuration toward a bimodal target.

The experiment illustrates how a shared control input can influence the terminal distribution of an ensemble.

**Simulation results:** To be added.

### Approximation Accuracy

Additional numerical experiments investigate how the number of retained moments affects the quality of the approximation.

**Numerical results and convergence plots:** To be added.

## Computational Methods

- Moment-based approximation
- Orthogonal polynomial representations
- Finite-dimensional optimal control
- Numerical optimization
- MATLAB-based simulation

## Research Status

This project is part of ongoing, unpublished research. Selected numerical results and mathematical derivations may be shared as research notes.
