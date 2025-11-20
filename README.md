# Kinematic Analysis of Sewing Machine Needle Bar Mechanism

![MATLAB](https://img.shields.io/badge/Tools-MATLAB%20%7C%20Symbolic%20Math-blue)

## Project Overview
This project presents a computational kinematic analysis of a **6-bar linkage mechanism** utilized in industrial sewing machine needle bar drives. The primary objective is to simulate the mechanism's motion and analyze the velocity profile of the needle bar (slider) relative to a constant rotary input. This analysis is critical for understanding the precise timing required for stitch formation, specifically loop-taking and dwell phases.

## Mechanism Description
The system operates as a **function generator**, converting uniform rotary input from the main shaft (Link 5) into a specific non-uniform reciprocating linear motion at the output slider (Needle Bar). The topology consists of:
* **Input:** Rotating crank driven at constant velocity.
* **Transmission:** A central 4-bar linkage loop ($O_5-C-A-O_2$) transmitting motion to a ternary link.
* **Output:** A connecting rod driving the vertical slider (Needle).

## Methodology
The simulation is implemented in **MATLAB** using the **Symbolic Math Toolbox** to ensure analytical exactness rather than relying solely on numerical approximations.

1.  **Position Analysis:**
    The mechanism is defined by vector loop closure equations. The system solves for unknown joint angles ($\theta_2, \theta_3$) as a function of the driver angle ($\theta_4$) using symbolic solvers to handle non-linear geometric constraints.

2.  **Velocity Analysis:**
    Velocity equations are derived via **exact symbolic differentiation** with respect to time. By applying the chain rule ($\frac{dx}{dt} = \frac{dx}{d\theta} \cdot \omega$), the code calculates the instantaneous linear velocity of the slider without finite difference errors.

## Key Results
The output includes a dynamic animation of the linkage and a velocity profile graph. The analysis reveals the mechanism's inherent **asymmetric velocity characteristics**, highlighting the "quick-return" motion and the specific deceleration near the Bottom Dead Center (BDC), which allows the rotary hook to engage the thread loop effectively.

## Usage
* **Requirements:** MATLAB with Symbolic Math Toolbox.
* **Execution:** Run the main script. The program will solve the symbolic equations, generate the pathing data, and display the velocity plots and animation.
