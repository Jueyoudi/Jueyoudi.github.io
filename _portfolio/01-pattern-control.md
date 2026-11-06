
---
title: "Pattern Control of Ensemble Dynamical Systems"
excerpt: "Steering parameter-dependent dynamical systems toward geometric target patterns using moment-based optimal control."
collection: portfolio
permalink: /portfolio/pattern-control/
date: 2025-08-01
---

## Overview

This project investigates the optimal control of parameter-dependent dynamical systems using a shared control input.

The objective is to steer an ensemble of dynamical systems toward prescribed geometric configurations, including circles, triangles, and star-shaped patterns.

The project combines mathematical modeling, moment-based approximation, and numerical optimization.

## Mathematical Formulation

Consider a parameter-dependent linear dynamical system:

$$
\dot{x}(t,\beta)
=
A(\beta)x(t,\beta)
+
B(\beta)u(t),
$$

where:

- $x(t,\beta)$ represents the state.
- $\beta$ is a system parameter.
- $u(t)$ is a common control input applied to the entire ensemble.

The control objective is to minimize the control energy:

$$
\min_{u}
\int_0^T u(t)^\top u(t)\,dt
$$

subject to prescribed initial and terminal ensemble configurations.

## Numerical Method

A moment-based representation is introduced:

$$
m_k(t)
=
\int_{\Omega}
\phi_k(\beta)x(t,\beta)\,d\beta,
$$

where $\phi_k(\beta)$ denotes a selected basis function.

By truncating the moment expansion, the original ensemble control problem is approximated by a finite-dimensional optimal control problem.

The resulting system is solved numerically to obtain a shared control input.

## Simulation Results

### Circle to Triangle to Star

The simulation demonstrates the transformation of an ensemble of states between prescribed geometric configurations.

<video width="100%" controls playsinline preload="metadata">
  <source src="/videos/pattern-control.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>

*Simulation of ensemble trajectories under a common control input.*

## Implementation

**Methods:** Moment-based approximation, numerical optimal control, finite-dimensional system representation.

**Tools:** MATLAB, numerical optimization, ODE solvers.

## Research Notes

Selected mathematical derivations and additional numerical results will be made available here.

*This project is part of ongoing, unpublished research.*
