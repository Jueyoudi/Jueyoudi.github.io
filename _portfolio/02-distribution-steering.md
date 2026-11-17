---
title: "Distributional Control via Moment-Based Representations"
excerpt: "Moment-based representations of ensemble systems, finite-dimensional optimal control, and distributional steering with labeled and unlabeled measurements."
collection: portfolio
permalink: /portfolio/distribution-steering/
---

## Overview

This project investigates moment-based approaches to the distributional control of parameter-dependent dynamical systems.

The objective is to steer an ensemble from a truncated Gaussian distribution toward a truncated Gaussian mixture distribution using shared control inputs.

My work primarily focuses on **deriving moment dynamics from the original ensemble system**, constructing finite-dimensional moment representations, and investigating numerical methods for distributional steering.

I considered two types of measurement settings:

- **Labeled measurements:** The system parameter β associated with each state is available.
- **Unlabeled measurements:** Only aggregated observations are available, without identifying which system parameter generated each observation.

These two settings lead to different moment representations and control formulations.

---

## 1. Original Ensemble System

Consider a multi-input, scalar-valued linear ensemble system:

$$
\frac{d}{dt}x(t,\beta)
=
\beta x(t,\beta)
+
\sum_{i=1}^{p}
\psi_{i-1}(\beta)u_i(t),
$$

where:

- x(t, β) represents the state of an individual system.
- β is the ensemble parameter.
- ψᵢ(β) denotes a polynomial basis function.
- uᵢ(t) is a control input applied across the ensemble.
- p is the number of control inputs.

The objective is to design control inputs that steer the ensemble toward a desired terminal configuration or output distribution.

To address the computational challenge of working with a continuously parameterized ensemble, I investigated moment-based representations.

## 2. Moment-Based Transformation

### 2.1 Definition of Ensemble Moments

For a selected basis function ψₖ(β), define the k-th ensemble moment as

$$
m_k(t)
=
\int_{\Omega}
\psi_k(\beta)x(t,\beta)\,d\lambda(\beta).
$$

Differentiating with respect to time yields

$$
\dot{m}_k(t)
=
\int_{\Omega}
\psi_k(\beta)\dot{x}(t,\beta)
\,d\lambda(\beta).
$$

Substituting the original ensemble dynamics gives

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

This establishes a connection between the original ensemble dynamics and their representation in the moment domain.

The resulting moment equations depend on the chosen basis functions and their recurrence or orthogonality properties.

## 3. Polynomial Basis Selection

I investigated three polynomial bases to derive and compare the corresponding moment systems.

### 3.1 Monomial Basis

For the monomial basis,

$$
\psi_k(\beta)=\beta^k,
$$

with β ∈ [0, 1], the moment is

$$
m_k(t)
=
\int_0^1
\beta^k x(t,\beta)\,d\beta.
$$

Differentiating and substituting the ensemble dynamics gives

$$
\boxed{
\dot{m}_k(t)
=
m_{k+1}(t)
+
\sum_{i=1}^{p}
\frac{u_i(t)}{k+i}.
}
$$

The corresponding input matrix contains entries

$$
H_{ki}=\frac{1}{k+i}.
$$

These entries form a Hilbert-type matrix, which can become severely ill-conditioned as the system dimension increases.

This creates numerical difficulties, particularly when solving for control inputs through matrix inversion or related numerical procedures.

### 3.2 Legendre Polynomial Basis

For the Legendre representation, I used the recurrence properties of Legendre polynomials to derive the moment dynamics.

With a suitably normalized Legendre basis,

$$
\beta\psi_k(\beta)
=
c_k\psi_{k+1}(\beta)
+
c_{k-1}\psi_{k-1}(\beta).
$$

Consequently,

$$
\dot{m}_k(t)
=
c_km_{k+1}(t)
+
c_{k-1}m_{k-1}(t)
+
\sum_{i=1}^{p}H_{ki}u_i(t).
$$

The coefficients cₖ are determined by the normalization of the polynomial basis.

For an orthonormal Legendre basis, multiplication by β leads to a tridiagonal moment-coupling matrix.

This provides a sparse and structured representation of the original ensemble dynamics.

### 3.3 Chebyshev Polynomial Basis

I also investigated the Chebyshev polynomial representation.

For k ≥ 1, the recurrence relation is

$$
\beta T_k(\beta)
=
\frac{1}{2}
\left(
T_{k+1}(\beta)+T_{k-1}(\beta)
\right).
$$

Using this relation, the drift component of the moment dynamics can be represented through neighboring moments.

The resulting system has a structured matrix representation, with input coefficients depending on the basis normalization and integration measure.

The comparison of these three bases illustrates how polynomial representations influence the structure and numerical properties of moment-based control systems.

## 4. Finite-Dimensional Moment System

After deriving the individual moment equations, I constructed a truncated moment vector:

$$
m(t)=
\begin{bmatrix}
m_0(t)\\
m_1(t)\\
\vdots\\
m_q(t)
\end{bmatrix}.
$$

The resulting finite-dimensional approximation is expressed as

$$
\boxed{
\dot{m}(t)=Lm(t)+Hu(t).
}
$$

Here:

- L represents coupling between moments induced by the ensemble dynamics.
- H describes the influence of shared control inputs on the moments.
- q determines the truncation order.

For the polynomial bases considered, the matrices L and H can be constructed using polynomial recurrence relations and basis-function inner products.

This transformation allows the original ensemble control problem to be approximated and studied using finite-dimensional linear control methods.

## 5. Optimal Control Formulation

After constructing the moment system, I investigated optimal control formulations in the moment domain.

### 5.1 Fixed-Endpoint Control

A representative objective is to minimize control energy:

$$
\min_u
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

### 5.2 Moment Trajectory Tracking

For a prescribed target moment trajectory m*(t), the tracking problem can be formulated as

$$
\min_u
\int_0^T
\|m(t)-m^*(t)\|^2\,dt.
$$

These formulations provide computational approaches for controlling the desired ensemble configuration through its finite-dimensional moment representation.

---

## 6. Numerical Experiments: Labeled Measurements

### 6.1 Measurement Setting

In the labeled setting, each observation retains the association between the system parameter β and the corresponding state x(t, β).

Therefore, the ensemble state can be represented through moments of the form

$$
m_k(t)
=
\int_{\Omega}
\psi_k(\beta)x(t,\beta)\,d\lambda(\beta).
$$

This is the setting used in the polynomial-basis derivations above.

### 6.2 Gaussian-to-Gaussian-Mixture Steering

I investigated the transformation from a truncated Gaussian distribution toward a truncated Gaussian mixture distribution.

The numerical experiments used an ensemble of 50 systems and compared the performance of different polynomial bases.

The reported settings include:

- **Legendre basis:** truncation order q = 25
- **Chebyshev basis:** truncation order q = 25
- **Monomial basis:** truncation order q = 10

The experiments examine the accuracy and numerical behavior of the resulting moment-based control methods.

**Simulation figures and videos will be added here.**

### 6.3 Numerical Conditioning

An important observation concerns the monomial representation.

Although the monomial basis leads to a relatively simple analytical representation, the corresponding Hilbert-type input matrix can become poorly conditioned.

This can produce excessively large control inputs and increase sensitivity in the original ensemble trajectories.

The reported Legendre and Chebyshev experiments exhibit more favorable numerical behavior.

These observations highlight the importance of basis selection for computational distributional control.

---

## 7. Numerical Experiments: Unlabeled Measurements

### 7.1 Aggregated Measurements without Labels

I also examined distributional control in a setting where individual system labels are unavailable.

Unlike the labeled case, the observed data no longer contain the correspondence between the system parameter β and the state x(t, β).

Instead, the available information consists of aggregated measurements of the ensemble states.

Consider the same class of parameter-dependent linear systems:

$$
\frac{d}{dt}x(t,\beta)
=
\beta x(t,\beta)
+
\sum_{i=1}^{p}
\beta^{i-1}u_i(t).
$$

With an identity output function, the observed output is

$$
y(t,\beta)=x(t,\beta).
$$

However, the individual parameter β associated with each observation is not available.

The control objective is therefore formulated in terms of the distribution of the ensemble outputs rather than the labeled state function.

### 7.2 Output Distribution and Moment Representation

Let μₜ denote the probability measure induced by the aggregated ensemble observations.

Using the pushforward representation,

$$
\mu_t=(x_t)_{\#}\lambda,
$$

where λ is the parameter-space probability measure.

For the monomial basis, the k-th moment of the output distribution is defined as

$$
m_k(t)
=
\int_{\mathbb{R}}
y^k\,d\mu_t(y).
$$

By the definition of the pushforward measure,

$$
\boxed{
m_k(t)
=
\int_0^1
x(t,\beta)^k\,d\beta.
}
$$

This is the key distinction from the labeled case.

In the labeled setting, moments are obtained by integrating the state against basis functions of β.

In the unlabeled setting, moments are calculated directly from the output distribution.

Thus, the unlabeled moments describe statistical properties of the ensemble without requiring individual parameter-state associations.

### 7.3 Moment Dynamics for Unlabeled Outputs

Differentiating the distributional moments gives

$$
\dot{m}_k(t)
=
k\int_0^1
x(t,\beta)^{k-1}
\dot{x}(t,\beta)\,d\beta.
$$

Substituting the original ensemble dynamics yields

$$
\dot{m}_k(t)
=
k\int_0^1
\beta x(t,\beta)^k\,d\beta
+
k\sum_{i=1}^{p}u_i(t)
\int_0^1
\beta^{i-1}x(t,\beta)^{k-1}\,d\beta.
$$

Unlike the labeled moment equations, this representation generally involves mixed terms containing both β and x(t, β).

Consequently, the unlabeled moment dynamics do not automatically reduce to the same linear system derived for labeled measurements.

This distinction motivates a distributional control formulation using moments of the output measure.

### 7.4 Optimal Transport and Moment Tracking

For the unlabeled setting, a target distributional trajectory can be constructed using optimal transport.

Let μ₀ and μ₁ denote the initial and target distributions.

A reference distribution trajectory μₜ* can be generated through displacement interpolation between these two distributions.

The associated target moment trajectory is

$$
m_k^*(t)
=
\int_{\mathbb{R}}
y^k\,d\mu_t^*(y).
$$

The distributional control problem can then be studied as a moment-tracking problem.

For an order-q truncated moment representation, a representative optimal tracking formulation is

$$
\min_u
\int_0^1
d_M
\left(
P_qm^*(t),
\hat{m}^{q}(t)
\right)\,dt
$$

subject to the corresponding truncated moment dynamics.

Here:

- μₜ* is the target distributional trajectory.
- m*(t) denotes its moment sequence.
- Pq denotes truncation to the selected moment order.
- m̂ᵠ(t) represents the controlled truncated moment trajectory.
- dM measures the discrepancy between the moment representations.

This approach allows distributional steering to be formulated without explicitly matching the states of individual labeled systems.

### 7.5 Unlabeled Distribution Steering Experiment

The unlabeled experiment considers steering the ensemble output distribution from a truncated Gaussian distribution toward a truncated Gaussian mixture distribution.

The reported numerical setting uses:

- **Measurement type:** Unlabeled aggregated measurements
- **Moment basis:** Monomial basis
- **Moment truncation order:** q = 8
- **Number of control inputs:** p = 8
- **Number of sampled systems for visualization:** 1000
- **Control interval:** t ∈ [0, 1]

The resulting controlled distributions are evaluated at

t = 0, 0.2, 0.4, 0.6, 0.8, and 1.

The simulation illustrates the evolution of the empirical output distribution under the computed control inputs.

**Unlabeled distribution evolution figure: To be added.**

**Control input figure: To be added.**

### 7.6 Labeled vs. Unlabeled Measurements

The two cases illustrate different perspectives on ensemble control.

| Aspect | Labeled Measurements | Unlabeled Measurements |
|---|---|---|
| Available information | State associated with β | Aggregated output distribution |
| Moment representation | Moments of the parameter-dependent state | Moments of the output measure |
| Mathematical focus | Polynomial basis transformation | Distributional moment representation |
| Control formulation | Finite-dimensional linear moment control | Optimal transport-based moment tracking |
| Main challenge | Basis selection and numerical conditioning | Loss of individual parameter-state correspondence |

The unlabeled formulation demonstrates how moment-based representations can also be used when the available information is distributional rather than individually labeled.

---

## 8. Key Research Work

My work on this project focuses on the computational aspects of moment-based distributional control.

The main areas include:

1. **Moment-Based Transformation:** Deriving moment representations for parameter-dependent ensemble systems.

2. **Polynomial Basis Investigation:** Studying monomial, Legendre, and Chebyshev bases and their corresponding moment dynamics.

3. **Finite-Dimensional Control:** Formulating the labeled ensemble control problem in the form ṁ = Lm + Hu.

4. **Numerical Optimal Control:** Investigating fixed-endpoint and moment-tracking formulations.

5. **Distributional Control Experiments:** Studying Gaussian-to-Gaussian-mixture steering and comparing numerical behavior across different representations.

6. **Unlabeled Measurement Setting:** Examining the use of output-distribution moments when individual system labels are unavailable.

## Research Status

This page presents selected mathematical derivations and computational investigations from ongoing, collaborative research.

The labeled case focuses on moment-system derivation and numerical control using polynomial bases. The unlabeled case illustrates a related distributional-control formulation based on aggregated measurements and optimal transport.

These materials are not presented as peer-reviewed publications.
