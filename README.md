# Stochastic Dynamics, Inhomogeneous Diffusion, and Polymer Physics

> **Langevin Simulations in Python**: From Free Brownian Motion and Non-Equilibrium Ratchets to 3D Bead-Spring Macromolecules.

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg?logo=python&logoColor=white)](https://www.python.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Vectorized-013243.svg?logo=numpy&logoColor=white)](https://numpy.org/)
[![SciPy](https://img.shields.io/badge/SciPy-Integrate-8CAAE6.svg?logo=scipy&logoColor=white)](https://scipy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Publication%20Plots-11557c.svg)](https://matplotlib.org/)
[![Numba](https://img.shields.io/badge/Numba-JIT%20Accelerated-00A3E0.svg?logo=numba&logoColor=white)](https://numba.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📖 Overview

This repository contains an end-to-end computational physics and statistical mechanics project investigating stochastic differential equations (SDEs), Brownian dynamics, inhomogeneous diffusion landscapes, non-equilibrium symmetry breaking in active dimers, and 3D macromolecular polymer dynamics.

All simulations are implemented with modern numerical practices: **vectorized NumPy Monte Carlo ensembles**, **adaptive numerical quadrature (`scipy.integrate.quad`)**, **Numba JIT hardware compilation (`@njit`)**, and **publication-standard visualizations**.

---

## 🔬 Topics & Modules Covered

### 1. Free Brownian Motion & Simple Diffusion
- Overdamped Langevin equation integration using Euler-Maruyama discretization.
- High-efficiency vectorized Monte Carlo random walks (10,000 trajectories).
- Empirical Mean Squared Displacement (MSD) validation: $\langle x^2(t) \rangle = 2Dt$.
- Temporal evolution of the Gaussian propagator:

$$P(x, t) = \frac{1}{\sqrt{4\pi D t}} e^{-x^2 / (4Dt)}$$

### 2. Confined Brownian Motion in a Harmonic Potential (Ornstein-Uhlenbeck)
- Particle relaxation dynamics from non-equilibrium initial positions.
- Relaxation timescale $\tau_{\text{rel}} = \gamma / k$.
- Ensemble convergence to the stationary Gibbs-Boltzmann distribution:

$$P_{\text{eq}}(x) = \sqrt{\frac{k}{2\pi k_B T}} e^{-kx^2 / (2k_BT)}$$

- Time-slice variance broadening towards steady-state thermal equilibrium.

### 3. Inhomogeneous Diffusion & Coordinate-Dependent Damping $\gamma(x)$
- Smooth sigmoidal friction transition: $\gamma(x) = \gamma_0 + \frac{\Delta\gamma}{1 + e^{-\lambda (x - x_c)}}$.
- Spatially varying diffusivity: $D(x) = \frac{k_B T}{\gamma(x)}$.
- Numerical quadrature of the partition function $\mathcal{Z} = \int \gamma(x) e^{-U(x)/k_BT} dx$.
- Verification of the modified steady-state probability density function.

### 4. Symmetry-Broken Dimer & Autonomous Directed Transport (Thermal Ratchet)
- Coupled Langevin dynamics of an elastic two-particle dimer under internal separation-dependent asymmetric damping $\Gamma_1(z) \neq \Gamma_2(z)$.
- Rectification of thermal fluctuations producing autonomous directed center-of-mass motion ($\langle v_{\text{cm}} \rangle \neq 0$).
- Linear regression velocity extraction and relative separation distribution $P(z)$ verification.

### 5. 2D & 3D Bead-Spring Polymer Chains (Rouse & Excluded Volume Models)
- Conformational relaxation of a 2D macromolecular chain.
- 3D polymer simulation with harmonic bonds and Weeks-Chandler-Andersen (WCA) repulsive excluded-volume potential.
- Accelerated with **Numba JIT compilation (`@njit(fastmath=True)`)**.
- Center-of-mass 3D diffusion scaling law: $\langle \Delta \mathbf{R}_{\text{cm}}^2(t) \rangle = 6 D_{\text{com}} t$ with $D_{\text{com}} = \frac{k_B T}{N_{\text{beads}} \gamma_0}$.
---

## 🚀 Getting Started

### Prerequisites
Make sure you have Python 3.9+ installed along with the required scientific computing libraries:

```bash
pip install numpy scipy matplotlib numba ipykernel jupyter
