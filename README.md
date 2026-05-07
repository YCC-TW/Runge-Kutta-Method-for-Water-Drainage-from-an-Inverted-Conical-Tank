# Runge-Kutta Method for Water Drainage from an Inverted Conical Tank

## Overview

This project was created for **Math-CS-143C Project 4** in Spring 2022. The assignment applies the **fourth-order Runge-Kutta method (RK4)** to model water draining from an inverted conical tank.

The goal is to numerically solve a differential equation that describes the height of water in the tank over time. The original problem uses a step size of **20 seconds** and requires printing water height values at specific time intervals.

## Problem Description

The project is based on a water-drainage problem involving an inverted conical tank.

Given:

```text
Initial water height: x = 8 ft
Initial time: t = 0 seconds
Step size: h = 20 seconds
```

The volume of water in a cone is:

```text
V = (1/3)πR²x
```

Using similar triangles, the radius and cross-sectional area can be expressed in terms of the water height. After simplifying the drainage model, the differential equation can be written in the form:

```text
dx/dt = -0.0003755 * sqrt(x)
```

where:

* `t` is time in seconds
* `x` is the height of the water in feet

## Assignment Goals

The original project required the following tasks:

* Derive the cross-sectional area `A(x)` of the water surface.
* Simplify the differential equation for the tank-drainage model.
* Write the initial condition.
* Use fourth-order Runge-Kutta with step size `h = 20` seconds.
* Print water height values at 60-second intervals for the first 10 minutes.
* Continue the approximation to estimate when the tank becomes empty.
* Attach a working computer program.

## Files

| File                | Description                                                                                                           |
| ------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `differential.java` | Java implementation of the fourth-order Runge-Kutta method for approximating the tank-drainage differential equation. |

## How the Program Works

The program defines a derivative function:

```java
double dydx(double x, double y) {
    return (-0.0003755 * Math.pow(x, 0.5));
}
```

It then applies the standard RK4 update formulas:

```text
k1 = h * f(tn, yn)
k2 = h * f(tn + h/2, yn + k1/2)
k3 = h * f(tn + h/2, yn + k2/2)
k4 = h * f(tn + h, yn + k3)

y(n+1) = yn + (1/6)(k1 + 2k2 + 2k3 + k4)
```

The program starts with:

```java
double x0 = 0;   // initial time
double y = 8;    // initial water height
double x = 600;  // target time in seconds
double h = 20;   // step size
```

and prints the estimated water height at the target time.

## How to Run

Compile the Java file:

```bash
javac differential.java
```

Run the program:

```bash
java differential
```

Example output format:

```text
The value of y at x is : [computed value]
```

## Key Concepts Demonstrated

* Java programming fundamentals
* Differential equations
* Numerical methods
* Fourth-order Runge-Kutta method
* Initial value problems
* Step-size based approximation
* Modeling a real-world physical system
* Translating a mathematical model into code

## Important Note About the Current Code

The mathematical model uses water height as the variable inside the square root:

```text
dx/dt = -0.0003755 * sqrt(x)
```

In the current Java implementation, the derivative method is written as:

```java
return (-0.0003755 * Math.pow(x, 0.5));
```

Because the program uses `x0` as the time variable and `y` as the water height, the code should be carefully reviewed before using it as a finalized GitHub project. A clearer implementation would rename the variables to `time` and `height`, and the derivative function should likely depend on the current water height rather than the current time.

A clearer version would use logic similar to:

```java
double derivative(double time, double height) {
    return -0.0003755 * Math.sqrt(height);
}
```

## Possible Improvements

* Rename the class from `differential` to `RungeKuttaTankDrainage`.
* Use Java class naming conventions with an uppercase class name.
* Rename variables so `t` represents time and `x` or `height` represents water height.
* Print results at 60-second and 180-second intervals as required by the assignment.
* Format output to six decimal places using `System.out.printf()`.
* Add a loop that automatically estimates the time when the tank becomes empty.
* Add comments explaining the physical meaning of each variable.
* Separate the RK4 method from the tank-specific derivative function for better reusability.

## Project Summary

This project demonstrates how the fourth-order Runge-Kutta method can be used to approximate the solution of an initial value problem. The model estimates how the height of water in an inverted conical tank changes over time as the tank drains. The project combines calculus, differential equations, physics-based modeling, and Java programming.
