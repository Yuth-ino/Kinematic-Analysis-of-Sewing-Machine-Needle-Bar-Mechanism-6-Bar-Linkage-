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

1.  **Position Analysis:** Solves non-linear vector loop closure equations:
    $$\vec{R}_{O2} + \vec{R}_{A} = \vec{R}_{O5} + \vec{R}_{C} + \vec{R}_{CA}$$
    
2.  **Velocity Analysis:** Derives exact velocity vectors using the Chain Rule:
    $$V_{slider} = \frac{d(D_y)}{dt} = \frac{d(D_y)}{d\theta_{in}} \cdot \omega_{in}$$

## 📊 Results (Preview)
*(Upload your graph image and replace the link below)*
![Velocity Graph](https://via.placeholder.com/800x400?text=Upload+Your+Velocity+Graph+Here)

> The graph demonstrates the **asymmetric velocity profile**, highlighting the quick-return motion essential for high-speed sewing operations.

## 🚀 Usage
1.  Clone the repository.
2.  Open the main script in MATLAB (R2020b or later recommended).
3.  Run the script to visualize the animation and generate plots.

---
*Project by [Yuth Kanjanaprayut/6630276621]*
