---
title: "Pattern Control of Ensemble Dynamical Systems"
excerpt: "Moment-based optimal control for steering an ensemble of dynamical systems through prescribed geometric configurations: Triangle, Square, and Maple Leaf."
collection: portfolio
permalink: /portfolio/pattern-control/
---

## Overview

This project investigates the optimal control of parameter-dependent ensemble dynamical systems, with a particular focus on **geometric pattern transformation using moment-based methods**.

The objective is to design a common control input that steers an ensemble of systems through a sequence of prescribed geometric configurations.

In the numerical experiment, the ensemble undergoes the following transformation:

**Triangle → Square → Maple Leaf**

Rather than controlling each individual system separately, the method uses a shared control input to coordinate the collective evolution of the entire ensemble.

My work focuses on transforming the original ensemble dynamics into a finite-dimensional moment system and solving the resulting optimal control problem numerically.

---

## 1. Mathematical Formulation

Consider a parameter-dependent linear ensemble system:

$$
\dot{x}(t,\beta)
=
A(\beta)x(t,\beta)
+
B(\beta)u(t),
$$

where:

- x(t, β) represents the state of an individual system.
- β denotes the parameter distinguishing systems within the ensemble.
- A(β) and B(β) describe the parameter-dependent system dynamics.
- u(t) is a shared control input applied to all systems.

For a two-dimensional state, the collection of ensemble states forms a geometric configuration in the plane.

The objective is to find a common control input that steers this configuration toward prescribed target patterns at selected times.

In this project, the initial configuration is a triangle, followed by a square-shaped intermediate target and a maple-leaf-shaped final target.

## 2. Moment-Based Representation

Directly controlling a continuously parameterized ensemble is computationally challenging.

To obtain a finite-dimensional representation, I introduced a moment-based transformation.

For a selected basis function ψₖ(β), define the k-th moment as

$$
m_k(t)
=
\int_{\Omega}
\psi_k(\beta)x(t,\beta)\,d\beta.
$$

Differentiating with respect to time gives

$$
\dot{m}_k(t)
=
\int_{\Omega}
\psi_k(\beta)\dot{x}(t,\beta)\,d\beta.
$$

Substituting the original ensemble dynamics yields

$$
\dot{m}_k(t)
=
\int_{\Omega}
\psi_k(\beta)A(\beta)x(t,\beta)\,d\beta
+
\int_{\Omega}
\psi_k(\beta)B(\beta)u(t)\,d\beta.
$$

Using the properties of the chosen basis functions, the ensemble dynamics can be represented in moment coordinates.

After finite-dimensional truncation, a representative moment system takes the form

$$
\boxed{
\dot{m}(t)=Lm(t)+Hu(t).
}
$$

Here:

- m(t) is the truncated moment vector.
- L represents the coupling between moments.
- H describes how the common control input influences the moments.

This transformation allows the original ensemble control problem to be approximated using finite-dimensional numerical optimal control methods.

## 3. Geometric Pattern Steering

The objective is to steer the ensemble through three prescribed configurations.

### Stage I: Triangle

The ensemble is initially distributed along the boundary of a triangular pattern.

Each parameter value β corresponds to a particular system within the ensemble.

The initial configuration determines the initial moment vector.

### Stage II: Square

The first steering objective is to transform the triangular configuration into a square.

A common control input is designed to move the ensemble toward the prescribed intermediate target configuration.

The transformation requires coordinating the evolution of all parameter-dependent systems simultaneously.

### Stage III: Maple Leaf

The final objective is to transform the square into a maple-leaf-shaped configuration.

Compared with simple geometric shapes, the maple leaf has a more irregular boundary containing multiple corners, lobes, and concave regions.

This provides a more challenging target for investigating geometric pattern control.

The experiment illustrates how moment-based methods can be applied to steering ensembles toward complex target configurations.

## 4. Optimal Control in the Moment Domain

After obtaining the finite-dimensional moment representation, the geometric steering problem can be formulated as an optimal control problem.

A representative objective is to minimize control energy:

$$
\min_u
\int_0^T
u(t)^\top u(t)\,dt
$$

subject to the moment dynamics

$$
\dot{m}(t)=Lm(t)+Hu(t)
$$

and prescribed moment targets at selected times.

For the triangle-to-square-to-maple-leaf experiment, these targets correspond to:

- Initial moment configuration: Triangle
- Intermediate moment configuration: Square
- Final moment configuration: Maple Leaf

The numerical control problem is solved to obtain shared control inputs that guide the ensemble through the desired sequence.

## 5. Simulation Results

### Triangle → Square → Maple Leaf

The following simulation demonstrates the geometric evolution of the controlled ensemble.

The ensemble starts from a triangular configuration, transforms toward a square, and finally approaches a maple-leaf-shaped target.

Throughout the process, systems with different parameter values evolve under a common control input.

<video width="100%" controls playsinline preload="metadata">
  <source src="/videos/triangle_square_maple_controls.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>

*Video 1. Moment-based geometric pattern control of an ensemble dynamical system. The simulation illustrates the sequential transformation from a triangle to a square and finally to a maple-leaf-shaped configuration under shared control inputs.*

### Interpretation

The simulation highlights three aspects of the control problem:

**1. Collective Pattern Transformation**

Instead of independently controlling individual points, the control input acts on the entire ensemble simultaneously.

**2. Moment-Based Control**

The original parameter-dependent system is represented through a finite-dimensional moment approximation, allowing numerical optimal control techniques to be applied.

**3. Complex Geometric Targets**

The final maple-leaf configuration demonstrates the application of the method to a more intricate geometric pattern than simple triangles or squares.

The simulation provides a visual illustration of geometric steering under a shared control input.

Quantitative evaluation of the terminal approximation accuracy can be added through moment errors and state-space reconstruction errors.

---

## 6. Computational Methods

The numerical study involves:

- Ensemble dynamical systems
- Moment-based representations
- Finite-dimensional approximation
- Optimal control
- Numerical integration
- MATLAB simulation

## 7. Research Focus

My work on this project focuses on:

1. **Moment Transformation:** Representing continuously parameterized ensemble systems using moment coordinates.

2. **Finite-Dimensional Control:** Converting the original ensemble problem into a numerically tractable optimal control formulation.

3. **Geometric Pattern Steering:** Investigating how shared control inputs can steer ensembles through prescribed geometric configurations.

4. **Numerical Simulation:** Evaluating the resulting control trajectories and their ability to approximate complex target patterns.

## Research Status

This project is part of ongoing, unpublished research in ensemble optimal control and moment-based numerical methods.

The simulation illustrates the geometric pattern steering problem and the computational use of moment-based control.
