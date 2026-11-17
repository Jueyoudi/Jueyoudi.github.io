---
title: "Distributional Control via Moment-Based Representations"
excerpt: "Transforming a parameter-dependent ensemble system into a finite-dimensional moment system using polynomial bases, with applications to distribution steering and numerical optimal control."
collection: portfolio
permalink: /portfolio/distribution-steering/
---

## Overview

This project investigates a moment-based approach to the distributional control of parameter-dependent dynamical systems.

The objective is to steer an ensemble from a truncated Gaussian distribution toward a truncated Gaussian mixture distribution using a common control input.

My work focuses on **deriving the moment dynamics from the original ensemble system** and transforming the distributional control problem into a finite-dimensional optimal control problem.

In particular, I explored different choices of polynomial bases, including monomial, Legendre, and Chebyshev polynomials, and investigated how these representations affect the numerical properties of the resulting control system.

## 1. Original Ensemble System

Consider a multi-input, scalar-valued linear ensemble system:

$$
\frac{d}{dt}x(t,\beta)
=
\beta x(t,\beta)
+
\sum_{i=1}^{p}\psi_{i-1}(\beta)u_i(t),
$$

where:

- x(t, β) denotes the state of an individual system.
- β represents the ensemble parameter.
- ψᵢ(β) denotes a polynomial basis function.
- uᵢ(t) represents a control input shared across the ensemble.

The goal is to determine control inputs that steer the ensemble toward a prescribed target distribution.

Directly handling the continuously parameterized ensemble can be computationally challenging. To address this, I explored a moment-based representation of the original system.

## 2. Moment-Based Transformation

The key idea is to represent the ensemble state using a sequence of moments rather than directly working with the entire parameter-dependent state function.

For a selected basis function ψₖ(β), define the k-th moment as

$$
m_k(t)
=
\int_{\Omega}
\psi_k(\beta)x(t,\beta)\,d\lambda(\beta).
$$

Differentiating with respect to time gives

$$
\dot{m}_k(t)
=
\int_{\Omega}
\psi_k(\beta)\dot{x}(t,\beta)
\,d\lambda(\beta).
$$

Substituting the original ensemble dynamics yields

$$
\dot{m}_k(t)
=
\int_{\Omega}
\psi_k(\beta)\beta x(t,\beta)
\,d\lambda(\beta)
+
\sum_{i=1}^{p}
u_i(t)
\int_{\Omega}
\psi_k(\beta)\psi_{i-1}(\beta)
\,d\lambda(\beta).
$$

This expression establishes the connection between the original ensemble dynamics and their moment representation.

The resulting moment equations depend on the selected basis functions and their recurrence or orthogonality properties.

## 3. Polynomial Basis Selection

I investigated three polynomial representations and derived the corresponding moment dynamics.

### 3.1 Monomial Basis

For the monomial basis,

$$
\psi_k(\beta)=\beta^k,
$$

with the parameter domain [0, 1], the moment becomes

$$
m_k(t)=\int_0^1\beta^k x(t,\beta)\,d\beta.
$$

Differentiating and substituting the ensemble dynamics gives

$$
\boxed{
\dot{m}_k(t)
=
m_{k+1}(t)
+
\sum_{i=1}^{p}\frac{u_i(t)}{k+i}.
}
$$

This provides an explicit representation of the ensemble dynamics in terms of moments.

However, the corresponding input matrix contains entries of the form

$$
H_{ki}=\frac{1}{k+i},
$$

which form a Hilbert-type matrix.

Such matrices can become severely ill-conditioned as the system dimension increases, creating numerical difficulties in control computation.

### 3.2 Legendre Polynomial Basis

For the Legendre representation, I used the recurrence properties of Legendre polynomials to derive the moment dynamics.

With a suitably normalized Legendre basis, multiplication by the ensemble parameter can be expressed as

$$
\beta\psi_k(\beta)
=
c_k\psi_{k+1}(\beta)
+
c_{k-1}\psi_{k-1}(\beta).
$$

Consequently, the moment dynamics take the form

$$
\dot{m}_k(t)
=
c_km_{k+1}(t)
+
c_{k-1}m_{k-1}(t)
+
\sum_{i=1}^{p}H_{ki}u_i(t).
$$

Here, the coefficients cₖ are determined by the normalization of the Legendre basis.

The recurrence relation produces a structured, sparse representation of the moment dynamics.

For an orthonormal Legendre basis, the matrix associated with multiplication by β has a tridiagonal structure.

### 3.3 Chebyshev Polynomial Basis

I also investigated the Chebyshev polynomial representation.

The Chebyshev recurrence relation is

$$
\beta T_k(\beta)
=
\frac{1}{2}
\left(
T_{k+1}(\beta)+T_{k-1}(\beta)
\right),
\quad k\geq1.
$$

Using this relation, the ensemble dynamics can be expressed in terms of adjacent moments.

This leads to another structured moment system, with the specific input coefficients depending on the chosen polynomial normalization and integration measure.

The comparison of these three bases provides insight into how the choice of moment representation affects the resulting numerical control problem.

## 4. From Ensemble Dynamics to a Moment System

After deriving the individual moment equations, I assembled a truncated moment vector:

$$
m(t)=
\begin{bmatrix}
m_0(t)\\
m_1(t)\\
\vdots\\
m_q(t)
\end{bmatrix}.
$$

The finite-dimensional moment dynamics can be written in matrix form as

$$
\boxed{
\dot{m}(t)=Lm(t)+Hu(t).
}
$$

Here:

- L represents the coupling between moments induced by the original ensemble dynamics.
- H describes how the shared control inputs influence the moments.
- q determines the truncation order of the moment representation.

For the polynomial bases considered, the structure of L and H can be obtained from recurrence relations and basis-function inner products.

This transformation is the central step of the project: it converts the original continuously parameterized ensemble control problem into a finite-dimensional linear control problem.

The resulting representation allows established numerical optimal control techniques to be applied directly in the moment domain.

## 5. Optimal Control in the Moment Domain

Once the moment system is obtained, the distributional control objective can be formulated in terms of the moment vector.

I considered both fixed-endpoint and trajectory-tracking formulations.

### Fixed-Endpoint Control

A representative objective is to minimize control energy:

$$
\min_{u}
\int_0^T
\|u(t)\|^2\,dt
$$

subject to

$$
\dot{m}(t)=Lm(t)+Hu(t),
$$

$$
m(0)=m_0,
\qquad
m(T)=m_{\mathrm{target}}.
$$

### Moment Trajectory Tracking

For a prescribed target moment trajectory m*(t), another objective is

$$
\min_u
\int_0^T
\|m(t)-m^*(t)\|^2\,dt.
$$

These formulations allow the distributional control problem to be investigated through finite-dimensional optimal control methods.

## 6. Numerical Experiments

### Gaussian-to-Gaussian-Mixture Steering

I investigated the transformation from a truncated Gaussian distribution toward a truncated Gaussian mixture distribution.

The experiments used an ensemble of 50 systems and compared different moment representations.

In the reported experiments:

- **Legendre basis:** truncation order q = 25
- **Chebyshev basis:** truncation order q = 25
- **Monomial basis:** truncation order q = 10

The numerical results illustrate how the choice of basis affects the accuracy and stability of the control computation.

**Simulation figures and videos will be added here.**

### Numerical Conditioning

A particularly important observation concerns the monomial representation.

Although it provides a simple analytical expression for the moment dynamics, the associated Hilbert-type input matrix can become poorly conditioned.

This leads to large computed control inputs and increased sensitivity in the original ensemble trajectories.

In contrast, the Legendre and Chebyshev representations provide more favorable numerical behavior in the reported experiments.

These observations highlight the importance of basis selection when using moment-based methods for computational distributional control.

## 7. Key Research Contributions

My work in this project focused on:

1. **Moment Dynamics Derivation:** Deriving the moment equations of a multi-input linear ensemble system using polynomial basis functions.

2. **Finite-Dimensional Representation:** Constructing the associated moment system in the form ṁ = Lm + Hu.

3. **Polynomial Basis Comparison:** Investigating monomial, Legendre, and Chebyshev representations and their corresponding matrix structures.

4. **Optimal Control Formulation:** Formulating distributional steering problems as finite-dimensional optimal control problems in the moment domain.

5. **Numerical Investigation:** Examining distribution steering performance, approximation errors, and numerical conditioning.

## Research Status

This project is based on my contributions to an ongoing, unpublished research manuscript.

The materials presented here focus on my work on moment-based representations, moment-system derivation, and numerical distributional control experiments.
