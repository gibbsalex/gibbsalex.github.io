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
ode45(@(t, x))
```




Usecases:
1. Nonlinear time-dependent functions
2. Simulink is just a block view of this

## MATLAB System Objects

# Bigger Simulation Software
1. Simulink
2. Simscape