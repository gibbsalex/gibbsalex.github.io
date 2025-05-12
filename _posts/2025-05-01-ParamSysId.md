---
layout: post
title: "Notes for Parametric System Identification"
date: 2025-05-01
categories: Control CATEGORY-2
usemathjax: true
---

# Work Flow
1. Determine Model Structure
2. Parameter Estimation
3. Data Collection
4. Validation

Model Estimation and Validation Iterative Process
1. Data(u(t), y(t))
2. Postulate Model
3. Optimization to find theta parameters
4. Validation
5. Repeat or use parameters

# Methods for Parameter Estimation
1. Prediction Error Modeling
2. Correlation Analysis
3. Spectral Analysis
4. Realization or Subspace Methods

# Definitions
1. Power
2. Spectrum 
3. Infinite Impulse Response Filter

# Least Squares
Approximates the solution for x in A x = b.

Sum of squares of the difference b - Ax is minimized.

Sources: https://textbooks.math.gatech.edu/ila/least-squares.html

# Find the solution to Ax = b

Setup:
b is the solution to the linear combination of column vectors in A stretched by the scalars defined in x.

A can give the direction, but b gives the magnitude of the vectors.

Solving Ax is like saying that we want to know if a desired b, b_d, is in the span of A. Ideally, b_d is within the solution Ax, but if it isn't then the closest point to b_d that we can get to in Ax is b_proj.

Least Squares finds the x that gets to b_proj.

Least Squares Recipe from the Resource:

A^T A x = A^T b
1. compute A^T A and vector A^T b
2. form augmented matrix A^T A x = A^T b and row reduce
3. solution is the vector x (which is the scalars that go into the linear combination of cols of A)

# Mass-Spring-Damper to Difference Eq

Nonhomogenous Ordinary Differential Equation:

$$
m \ddot{x} + c \dot{x} + kx = F(t)
$$

Laplace Transform to the Complex Frequency Domain Space:
$$
m s^2 X(s) + c s X(s) + k X(s) = F(s)
$$

Transfer Function from input(F(t)) to output(x(t)):
$$
\frac{X(s)}{F(s)} = \frac{1}{ms^2 + cs + k} = G(s)
$$

Discretization:

Zero-order hold equivalent to G(s)
$$
G(z) = (1 - z^{-1}) \mathcal{Z} \{ \mathcal{L}^{-1}[ \frac{G(s)}{s} ]_{t = k \Delta T} \}
$$

Solve:

$$
\mathcal{L}^{-1} \{ \frac{1}{ms^3 + cs^2 + ks} \} = too complicated!
$$

Plan B: MATLAB c2d() using a zero-order hold

Suggested discrete form:

$$
G(z) = \frac{b_1 z + b_2}{z^2 + a_1 z + a_2}
$$

Difference Form:
$$
x(k) + a_1 x(k-1) + a_2 x(k-2) = b_1 F(k - 1) + b_2 F(k - 2)
$$

$$
x(k) = -a_1 x(k-1) -a_2 x(k-2) + b_1 F(k-1) + b_2 F(k-2)
$$

Regressor and Parameters:
$$
\Phi = [-x(k-1), -x(k-2), F(k-1), F(k-2)]\\

\theta = [ a_1, a_2 , b_1, b_2]
$$

Linear Regression Model:
$$
x(k) = \Phi(k)^T \theta + \epsilon(k, \theta)
$$

# Spectral Analysis
- Frequency Domain Analysis
- Frequency Response Estimation
- Noise Spectrum Estimation
- Coherence Estimation

Frequency Domain immediately tells us quantitative behavior(order and delays) of TF G(s) when looking at the bode plot

# IIR vs FIR
System must lie in the set of models

# Spectral Analysis: (ETFE vs SPA) L6

ETFE does not equal SPA

ETFE * a coveriance window = SPA

More data does not help the ETFE by itself. Soln: Smooth the periodogram. Smoothing not averaging

Options for finding the best W(w): Fourier transform

Choices of covariance windows: Rectangular, Bartlett, Hamming, Welch

Use the coherence spectrum as an inducation of noise. "Kinda like signal to noise ratio"

# IV method L8
Uses an instrument to assist the regressor in finding parameters of the system that are less correlated with the noise signal.

The instrument is correlated with the regressor, but uncorrelated with the equation noise.

Does not find the exact optimal parameters

# Constrained Least Squares (CLS) L9
When a linear constraint is present.

Add a Lagrange Variable to minimize the new overall cost function

# LS and FreqDom ID L10
Find $G(\omega)$ as a division of output to input data.

Use LS to curve fit a line to the bode plot

# Realization Algorithm L11
Determine the state space model A, B, C, D from impulse response coefficients $g_0 (k)$

### methods to estimating $g_0 (k)$
1. input white noise, estimate $R_{yu}(\tau)$, then $g(k) = R_{yu}(k)$
2. input white noise, estimate $\hat\theta_{LS}$ for a FIR model, then $\hat{g}(k) = \hat{\theta}_{LS}(k)$
3. Estimate $\hat{G}_{spa}(\omega)$ via SPA, then $\hat{g}(k) = \mathcal{F}^{-1} \{ \hat{G}_{SPA} (\omega) \}$

Ho-Kalman Algorithm

# subspace algorithm: L12
General I/O data - Hankle - SVD - convex optimization

# Prediction Error Modeling L13
Estimate the parameter value by minimizing the Prediction Error.

One step ahead prediction

Example: Auto Regressive(AR) noise filter, or Moving Average(MA) noise filter, or Auto Regressive Moving Average(ARMA) noise filter

# Convergence and Consistency L14
Convergence depends on signal properties

Consistency depends on chosen model structure

# Parameter Estimation and Convergence L15

Linear Regression Model

How does the variance of the model change with more error

Gradient of the prediction error or output predictor

# Approximate Parameter Estimation L16

How do we know when our estimation is good enough?

# Iterative Methods to PEM L17

Step through the gradient to minimize the prediction error

Direction: Follow the gradient of steepest descent

Engine: Newton-Raphson optimization to step forward