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

# Methods for Parameter Estimation
1. Prediction Error Modeling
2. Correlation Analysis
3. Spectral Analysis
4. Realization or Subspace Methods

# Definitions
1. Power
2. Spectrum 

# Least Squares
Approximates the solution for x in A x = b.

Sum of squares of the difference b - Ax is minimized.

Sources: https://textbooks.math.gatech.edu/ila/least-squares.html

# Ax = b
b is the solution to the linear combination of column vectors in A stretched by the scalars defined in x.

A can give the direction, but b gives the magnitude of the vectors.

We want to know if a desired b, b_d, is in the span of A. Such that, we can find it with x when doing Ax. Ideally, b_d is within the solution Ax, but if it isn't then the closest point to b_d that we can get to in Ax is b_proj.

Least Squares finds the x that gets to b_proj.

Least Squares Recipe from the Resource
A^T A x = A^T b
1. compute A^T A and vector A^T b
2. form augmented matrix A^T A x = A^T b and row reduce
3. solution is the vector x (which is the scalars that go into the linear combination of cols of A)


# Spectral Analysis
- Frequency Domain Analysis
- Frequency Response Estimation
- Noise Spectrum Estimation
- Coherence Estimation

Frequency Domain immediately tells us quantitative behavior(order and delays) of TF G(s) when looking at the bode plot