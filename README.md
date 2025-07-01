
# Steady-State 2D Temperature Distribution in a Channel | CFD Project

## 📘 Project Overview

This project implements a numerical simulation to analyze the **steady-state temperature variation** in a 2D channel under a **parabolic velocity profile**. The study models convective and conductive heat transfer using the **finite difference method**.

> Developed as a part of the **Computational Fluid Dynamics (CFD)** coursework under the guidance of **Dr. Jyotirmay Banerjee** at NIT Surat.

---

## 👨‍💻 Contributors

- Mohammed Faizan  
- Dhruv Chheda  
- Ved Patel  

---

## 🧩 Problem Statement

Develop a C-based numerical code to obtain the steady-state temperature profile in a 2D channel subjected to a parabolic inlet velocity. Simulate for multiple combinations of:
- **Maximum velocity (u_max)**
- **Thermal diffusivity (α)**

---

## 🔬 Governing Equation

Steady-state energy transport equation:

```
ρCp(u ∂T/∂x) = K(∂²T/∂x² + ∂²T/∂y²)
```

Where:
- `T` = Temperature
- `u(y)` = Parabolic velocity (in x-direction)
- `K` = Thermal conductivity
- `α = K / (ρCp)` = Thermal diffusivity

---

## ⚙️ Assumptions

- 2D, steady-state, incompressible flow
- Parabolic velocity profile (fully developed at inlet)
- Constant wall temperature
- No internal heat generation
- Uniform 3x3 grid
- Velocity only in x-direction

---

## 🧱 Grid Setup

- Grid: 3×3 (uniform spacing)
- Inlet temperature: 100 units
- Wall temperature: 300 units
- Δx = Δy = 1/3

---

## 🧮 Velocity Profile

```
u(y) = u_max * (1 - 4*y² / H²)
```

- Maximum at centerline
- Zero at walls
- Symmetric profile for y ∈ [0, H]

---

## 🧪 Boundary Conditions

| Location       | Type        | Condition       |
|----------------|-------------|-----------------|
| Left (Inlet)   | Dirichlet   | T = 100 units   |
| Right (Outlet) | Neumann     | ∂T/∂x = 0       |
| Top/Bottom     | Dirichlet   | T = 300 units   |

---

## 🧾 Numerical Method

- Finite Difference Method
- Central Difference for Advection & Diffusion
- Convergence based on change threshold (ε = 1e-6)
- Iterative Time-Marching Loop

---

## 💻 Code Implementation

Written in C, the code calculates updated temperature values based on discretized transport equations.

> See [`code.c`](./code.c) for the full implementation.

---

## 📊 Results Summary

### 🔺 By Velocity (u)
- Higher `u`: Dominant advection, steeper x-gradient
- Lower `u`: Higher wall influence, more symmetric profiles

### 🔻 By Thermal Diffusivity (α)
- Higher `α`: Faster convergence, smoother gradients
- Lower `α`: Sharper temp changes, more iterations needed

---

## 📌 Conclusion

- Velocity affects longitudinal heat transport (advection)
- Thermal diffusivity affects vertical smoothing (conduction)
- The model shows expected behavior: flatter profiles with higher `u`, smoother gradients with higher `α`.

---

