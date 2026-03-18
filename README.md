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
/root
│── /docs # Theoretical Explanations and Examples
│── /experiments # Experimental environment
│── /src
    │── mesh/ # Mesh generation and handling
    │── fem/ # FEM implementation (basis functions, assembly, solver)
    │── physics/ # Poisson equation & gravitational model
    │── visualization/ # Plotting results (2D fields)
    │── main.py # Entry point
    │── README.md
```

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