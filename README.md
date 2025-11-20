# Kinematic Analysis of Sewing Machine Needle Bar Mechanism

![MATLAB](https://img.shields.io/badge/Project-MATLAB%20Simscape-orange?style=for-the-badge&logo=matlab) ![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)

## 📌 Overview
This project presents a computational kinematic analysis of a **6-bar linkage mechanism** utilized in industrial sewing machine needle bar drives. The primary objective is to simulate the mechanism's motion and analyze the velocity profile of the needle bar (slider) relative to a constant rotary input.

The simulation uses **MATLAB** to solve vector loop equations and generate precise velocity profiles required for stitch timing (loop-taking and dwell phases).

## ⚙️ Mechanism Description
The system operates as a **function generator**, converting uniform rotary input into a specific reciprocating linear motion.
* **Input:** Rotating crank driven at constant velocity (Link 5).
* **Transmission:** A central 4-bar linkage loop ($O_5-C-A-O_2$) transmitting motion to a ternary link.
* **Output:** A connecting rod driving the vertical slider (Needle Bar).

## 🧮 Methodology
The analysis avoids approximate numerical differentiation by using **Symbolic Math**:

**1. Position Analysis**
Solves non-linear vector loop closure equations:
<div align="center">
  <img src="https://latex.codecogs.com/svg.latex?\Large&space;\vec{R}_{O2}+\vec{R}_{A}=\vec{R}_{O5}+\vec{R}_{C}+\vec{R}_{CA}" />
</div>
<br>

**2. Velocity Analysis**
Derives exact velocity vectors using the Chain Rule:
<div align="center">
  <img src="https://latex.codecogs.com/svg.latex?\Large&space;V_{slider}=\frac{d(D_y)}{dt}=\frac{d(D_y)}{d\theta_{in}}\cdot\omega_{in}" />
</div>

## 📊 Results (Preview)

<div align="center">
  <img src="sliderDvelo.PNG" width="80%" />
  <p><em>Figure 1: Velocity Profile of the Needle Bar (Slider)</em></p>
</div>

> The graph demonstrates the **asymmetric velocity profile**, highlighting the quick-return motion essential for high-speed sewing operations.

## 🚀 Usage
1.  Clone the repository.
2.  Open the main script in MATLAB (R2020b or later recommended).
3.  Run the script to visualize the animation and generate plots.

## 💻 Key Code Highlights

This project leverages MATLAB's **Symbolic Math Toolbox** to perform exact kinematic analysis. Instead of relying on approximate numerical methods, we derive the equations analytically.

**1. Solving Vector Loop Equations (Position Analysis)**
Here, we define the geometric constraints of the 6-bar linkage and solve for the unknown joint angles ($\theta_2, \theta_3$).

```matlab
% Define Symbolic Variables
theta2 = sym('theta_2');
theta3 = sym('theta_3');
theta4 = sym('theta_4'); % Input Driver Angle

% Define Vector Loop Equations (O2 -> A -> C -> O5)
eq1 = Ax == Cx + l3*cos(theta3);
eq2 = Ay == Cy + l3*sin(theta3);

% Solve the non-linear system symbolically
sol = solve([eq1 eq2], [theta2 theta3]);

% Select Assembly Mode 2
theta2_sol = sol.theta_2(2);
theta3_sol = sol.theta_3(2);
```

**2. Exact Velocity Derivation**
Using the Chain Rule, we calculate the instantaneous velocity of the needle bar (slider). This provides a smooth, continuous velocity profile without quantization errors
```matlab
% Define Input Speed
omega_driver = 1; % rad/s

% Calculate Angular Velocities (d_theta/dt)
omega2_sym = diff(theta2_sol, theta4) * omega_driver;
omega3_sym = diff(theta3_sol, theta4) * omega_driver;

% Calculate Linear Velocity of the Needle Bar (Slider D)
% V = d(Position)/dt
VDy_sym = diff(Dy, theta4) * omega_driver;
```
[**📄 View Full Source Code**](needle_bar_position_and_velocity.mlx)
---
*Project by [Yuth Kanjanaprayut/6630276621]*
