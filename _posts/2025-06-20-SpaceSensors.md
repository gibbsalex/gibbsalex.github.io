---
layout: post
title: "Space Sensors"
date: 2025-06-18
categories: Control CATEGORY-2
usemathjax: true
---

Sensors used in space to estimate the state of a ship

### Reaction Wheels

Controls orientation

Proved torques around the COM along the wheel spin axis.

Can store and absorb angular momentum after tipoff is applied.

Cons: Once a reaction wheel is at maximum speed it is saturated. Using this in combination with a thruster prevents saturation.

A fourth reaction wheel can be mounted for redundancy. Using a skewed configuration, we can cross-couple torques to apply forces in more than one direction with one wheel.

### Magnetic Torquers

Control torques perpendicular to the external magnetic field.

Apply an electric field through a coiled conductor, generate a magnetic dipole through the center of the coil that loops around. Generated dipole interacts with the external magnetic field to produce a torque perpendicular to the dipole and field.

Strength of dipole = size of coil + number of turns.

Residual affects from this device on magnetometers.

Cannot stabilize to all three axis, as it is dependent on external magnetic field. Pairs well with reaction wheels.

Best suited for low-Earth orbit and interplanetary applications.

### Thrusters 

Can generate forces and torques.

Require expendable fuel source.

Capable of rapid maneuvers, quick reaction wheel desaturation, and spin stabilization.

There will always need to be attitude control systems when attempting to do translational motions.

### Star Trackers

Estimate three-axis attitude.

Compare a digital image to an onboard star catalog.

Critical characteristics: FOV size,magnitude of stars, star tracker internal processing capabilities.

Drawback: Affected by spacecraft angular rate, external light sources, and glare. Must be carful not to contaminate the optics from exhaust plumes.

Bad with angular velocities. Expensive solutions are only good up to 3.0 deg/s

### Magnetometers

Estimates 2-axis attitude.

Measures the local magnetic field.

Requires a well modeled magnetic field model to reference agains the measured magnetic field.

This in combination with sensors like the Sun Senor, can help estimate the 3-axis attitude.

Requires careful placement on the spacecraft.

May require on-orbit recalibration.


### Sunsensors

Used for attitude estimation.

These sensors measure the direction of the sun in a spacecraft body frame.

To obtain a three-axis attitude estimate, one additional independent source of attitude information is required.

Good for fault detection. Be aware of this sensor getting confused by glint from the spacecraft or the Moon.

Types: Cosine detectors, quadrant detectors, digital sun sensor, sun camera.

### Horizon Sensors

Estimates attitude.

Types: infrared horizon crossing indicators, thermopile sensors.

### Inertial Sensing

Gyros for angular change.

Accelerometers for measuring velocity change.

Configurations: single, IRU, IMU.

MEMS are small but are susceptible to radiation and single event upsets.

Consider dynamics range, output resolution, bias, sampling rate. Bias drift can be externally calculated and adjusted for in the attitude determination.

## Resources:
1. https://www.nasa.gov/smallsat-institute/sst-soa/guidance-navigation-and-control/#5.2.2