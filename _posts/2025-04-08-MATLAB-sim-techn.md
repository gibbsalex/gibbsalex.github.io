---
layout: post
title: "Simulation Techniques Used in MATLAB"
date: 2025-04-08
categories: Control VehicleDynamics CATEGORY-2
usemathjax: true
---

## MATLAB Functions
setup with a function definition

```MATLAB
function dydt = dyn(t, x)
    k = 5;
    b = 1;
    m = 1;

    dydt = [x(2); -k/m * x(1) - b/m * x(2)];
end
```

Simulate with:
ode45()

```MATLAB
tspan = [0 5]; % define time window
x0 = [1; 0];  % define initial conditions (x1 = displacement = 1, x2 = velocity = 0)

ode45(@dyn, tspan, x0) % simulate
```

This method is great for time-dependent functions, such as nonlinear nonautonomous functions.

Simulink is a block view of these functions. Simulink graphical visualization makes it easier to adjust larger models.

## MATLAB System Objects

Option 1: Build the system in state-space form
```MATLAB
k = 5;
b = 1;
m = 1;

A = [0 1; -k/m -b/m];
B = [0; 0];
C = [1 1];
D = [0];

msd_sys = ss(A, B, C, D);
```
Option 2: Build the system in transfer function form
```MATLAB
num = 1;
den = [m, b, k];

msd_sys = tf(num, den)
```


Simulate the System Object
```MATLAB
time = linspace(0, 10, 1000);
u = sin(10 * pi * time);

y = lsim(msd_sys, u, time) % simulate
```

Popular Additional Tools:
```MATLAB
step() % analyze step response
bode() % plot the magnitude and phase
stepinfo() % display info of step response
rlocus() % plot the rootlocus of a transfer function
zpk() % build tf with zero-poles-gain
```

# Bigger Simulation Software
1. Simulink
2. Simscape