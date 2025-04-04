---
layout: post
title: "Kalman Filter Notes"
date: 2025-03-28
categories: Control CATEGORY-2
usemathjax: true
---

New change 3

The Kalman filter is a state-estimation technique that fuses data from multiple sensors. The KF requires knowledge of the model, and the covariances of the sensors. It assumes white noise, and guassian estimations.

**State-Space Model**

$$
x_t = F x_{t-1} + G u_t + w_t \\ y_t = H x_t + v_t
$$


where:

$$
\begin{array}{ll}
x_{t} & \text{state, at time t} \\
F & \text{signal model(forces acting on the model)} \\
G & \text{input model(how the inputs act on the model)} \\
u_t & \text{input vector} \\
y_t & \text{measurements from sensors} \\
H & \text{observation matrix} \\
w_t & \text{system model noise}\\
v_t & \text{measurement noise}
\end{array}
$$

**Kalman Prediction**

$$
x_{t|t-1} = F x_{t-1|t-1} + G u_t \\
\Sigma_{t|t-1} = F \Sigma_{t-1|t-1}F^T + Q_t
$$

**Kalman Update**

$$
x_{t|t} = x_{t|t-1} + K_t(y_t - H x_{t|t-1}) \\
K_t = \Sigma_{t|t-1} H^T S_t^{-1} \\
S_t = H\Sigma_{t|t-1}H^T + R_t \\
\Sigma_{t|t} = (I - K_t H)\Sigma_{t|t-1}
$$




# Optimization
The Kalman Filter is always trying to reduce the trace of the conditional covariance matrix $\Sigma_{t|t}$

Minimize this least squares proble(a.k.a Cost Function):

$$
\mathbb{E}[(x_k - z)^T(x_k-z)|Z] = \mathbb{E}[x_k^Tx_k|Z] - 2z^T\mathbb{E}[x_k|Z] + z^Tz
$$

The minimal solution is $z = \mathbb{E}(x_k|Z)$, this would mean that our measurement exactly matches our actual position

# Assumptions
1. Sensors experience white noise. Prof. Henrik Christenson says "we always assume this, and it is never exact".
2. Guassian distributions of sensor measurements.

# Procedure:
## 1. Prediction Step (time update)
Propogate forward the model of the system using this line:

$$
x_{t|t-1} = F x_{t-1|t-1} + G u_t
$$

Track the changes to our state covariance $\Sigma_t$ with this line:

$$
\Sigma_{t|t-1} = F \Sigma_{t-1|t-1}F^T + Q_t
$$

## 2. Update Step (measurement update)
Correct the state location, using the sensor measurements.

# The "Gimmick"

Follow this procedure:

1. Take a guess at the new state $ x_{t} $.
2.  Use the optimal gain $K$, to update the guess with sensor measurements $y_{t}$.



# Challenges:
1. Coming up with the Signal Model
2. What happens when we lose sensor information?
3. How to determine the quality of the estimate?

# Resources
1. Prof. Bob Bitmead's, MAE 288b Optimal Estimation
2. Prof. Henrik Christenson's, CSE ??? 

# Further Research
1. Nonlinear Extended Kalman Filter(EKf)
2. Hybrid System Salted Kalman Filter
