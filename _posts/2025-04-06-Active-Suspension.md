---
layout: post
title: "Review of Active Suspension Systems"
date: 2025-04-06
categories: Control VehicleDynamics CATEGORY-2
usemathjax: true
---
# This is a compression of the paper "Advances in Active Suspension Systems for Road Vehicles"

## Introduction
Main Focus:
Advances in Hardware Structures and Control Strategies for production cars. (ASS)

Current Technology:
- Mercedes active body control
- Audi predictive active suspension
- series active variable geometry suspension
- active wheel-alignment system

Traits of a better hardware design:
- compact structure
- small mass increment
- low power consumption
- high-frequency response
- acceptable economic cost
- high reliability

Traits of a better control algorithm:
- stabilize chassis attitude
- attenuate the chassis vibration
- enhance ride comfort and handling ability
- improve stability and saftey with cooperative assistance from steering and braking mechanisms
- improve fuel economy
- use algorithms to adapt to driving scenarios

Suspension System must be able to cooperate with other modules such as steering\braking actuators, and sensors on the car. Communicate with higher-level decision-making

## Section 2 - Hardware

Geometric topology and functinos

## Section 3 - Control

Stabilize chassis pitch and roll
1. use PID to control multiple objectives
2. Sliding mode controller to keep the car in a desired subset of sytems
3. Backstepping Control

improve ride comfort through chassis vibration attentuation
- Skyhook, groundhook, LQR/LQG,Hinf, mu synthesis, model predictive control, sliding mode control, backstepping

comunicate with other car modules

## Section 4 - Models, Simulation, Validation

## Section 5 - Conclusion, Vision

## Rivian

Setup:
Independent air suspension.
6.5inches of vertical travel.
Automatic ride-height leveling.
Hydraulic cross-linked suspension

Ride quality is determined by:
variable-rate springs, variable-rate dampers

# Reference
1. Advances in Active Suspension Systems for Road Vehicles (Min Yu, Simous A. Evangelou, Daniele Dini), ScienceDirect

2. Brian Douglas, Analyze the QuaterCar Model of a Car and tune a robust controller: https://www.mathworks.com/help/robust/gs/active-suspension-control-design.html

3. S. Hariharen, "Variable Spring Rate Adaptive Suspension System": https://www.ijser.in/archives/v5i5/IJSER151387.pdf