# Finite Element Method for Gravitational Potential (2D)

Implementation of the Finite Element Method (FEM) for solving the Poisson equation, including weak formulation, discretization, and linear system solving. Applied to modeling gravitational potentials from mass distributions with visualized field behavior.

## Project Goal

The goal of this project is to numerically solve the gravitational potential in a two-dimensional domain using the **Finite Element Method (FEM)**.

We aim to:
- Implement a basic FEM solver from scratch
- Solve the Poisson equation for gravity
- Visualize the resulting potential field
- Build an intuitive understanding of FEM through a physics-based example

---

## Background

### Gravitational Potential

In physics, the gravitational potential $\Phi$ describes the potential energy per unit mass at a point in space. It satisfies the **Poisson equation**:

$$
\nabla^2 \Phi = 4 \pi G \rho
$$

where:
- $\nabla^2$ is the Laplacian operator
- $G$ is the gravitational constant
- $\rho$ is the mass density

In this project, we solve this equation numerically in **2D**.

---

### Finite Element Method (FEM)

The Finite Element Method is a numerical technique used to solve partial differential equations (PDEs).

The key idea:
1. Divide the domain into small elements (mesh)
2. Approximate the solution locally using simple functions
3. Assemble a global system of equations
4. Solve for the unknown values at mesh nodes

FEM is widely used in:
- Engineering (structural analysis)
- Physics simulations
- Fluid dynamics
- Electromagnetics

---

## Project Structure (EXPERIMENTAL)

```text
fem-gravity/
│
├── README.md
├── docs/
│   └── theory.md
│
├── src/
│   ├── mesh/
│   ├── fem/
│   ├── solver/
│   ├── physics/
│   └── visualization/
│
├── experiments/
│
├── results/
│   ├── plots/
│   └── data/
│
└── requirements.txt
```

### Overview

- [docs/](docs/) – Contains theoretical background and explanations (e.g. FEM derivation, Poisson equation, small illustrative examples).
- [src/](src/) – Core implementation of the project:
- [src/mesh/](src/mesh/) – Mesh generation and domain discretization
- [src/fem/](src/fem/) – Finite Element Method logic (basis functions, element computations)
- [src/solver/](src/solver/) – Assembly of the global system and linear solver
- [src/physics/](src/physics/) – Problem definition (mass density, constants, equations)
- [src/visualization/](src/visualization/) – Plotting and rendering of results
- [experiments/](experiments/) – Runnable scripts for testing different scenarios (e.g. single mass, multiple masses, convergence studies).
- [results/](results/) – Stores generated outputs such as plots and numerical data.
- [requirements.txt](requirements.txt) – Lists all required Python dependencies.

---

## Learning Objectives

- Understand the mathematical foundation of FEM
- Learn how PDEs are solved numerically
- Connect physics (gravity) with numerical methods
- Build a full simulation pipeline from scratch

---

## Notes

- This project is intentionally implemented from scratch for learning purposes.
- Performance is not the primary goal — clarity and understanding are.