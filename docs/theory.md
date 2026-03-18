# Theory

## 1. Poisson Equation

The Poisson equation is a second-order partial differential equation of the form

$$
\nabla^2 \Phi = f
$$

where:

* $\nabla^2$ is the Laplacian operator
* $\Phi$ is the unknown scalar field (e.g., gravitational potential)
* $f$ is a source term (e.g., mass density)

In the context of gravitation, the equation becomes:

$$
\nabla^2 \Phi = 4 \pi G \rho
$$

where:

* $G$ is the gravitational constant
* $\rho$ is the mass density

---

### 1.1 The Laplacian Operator

In two dimensions, the Laplacian is defined as:

$$
\nabla^2 \Phi = \frac{\partial^2 \Phi}{\partial x^2} + \frac{\partial^2 \Phi}{\partial y^2}
$$

It measures how the value of a function differs from its surroundings. Physically, it describes how the potential is influenced by nearby sources.

**Intuition:** Imagine the potential as a surface over the 2D domain. The Laplacian measures whether a point is higher or lower than the average of its neighbors. Sources like mass density create 'peaks' or 'valleys'.

---

### 1.2 Boundary Conditions

To obtain a unique solution, boundary conditions must be specified.

Common types:

* **Dirichlet boundary condition**: $\Phi = g$ on the boundary
* **Neumann boundary condition**: $\frac{\partial \Phi}{\partial n} = h$, derivative normal to the boundary

Without boundary conditions, the solution is not uniquely defined.

**Example:** For a gravitational potential in a box, setting $\Phi=0$ on the edges is a Dirichlet condition.

---

## 2. Weak Formulation

The classical (strong) form of the Poisson equation requires $\Phi$ to be twice differentiable. This is often too restrictive for numerical methods, especially when the solution has sharp gradients.

The weak formulation relaxes this requirement by integrating against a set of test functions.

### 2.1 Multiplication with a Test Function

Let $v$ be a test function (smooth and vanishes at Dirichlet boundaries). Multiply both sides of the Poisson equation by $v$ and integrate over the domain $\Omega$:

$$
\int_\Omega v , \nabla^2 \Phi , d\Omega = \int_\Omega v f , d\Omega
$$

**Intuition:** We are averaging the residual (difference between left and right sides) over the domain using the weights defined by $v$.

### 2.2 Integration by Parts

Applying integration by parts (or Green’s first identity) transfers derivatives from $\Phi$ to $v$:

$$
\int_\Omega v , \nabla^2 \Phi , d\Omega = - \int_\Omega \nabla v \cdot \nabla \Phi , d\Omega + \int_{\partial \Omega} v , \frac{\partial \Phi}{\partial n} , dS
$$

**Why this is important:**

* Reduces smoothness requirements on $\Phi$ (now it only needs first derivatives)
* Introduces natural handling of Neumann boundary conditions through the boundary term

**Intuition example:** Think of a string stretched across points. Instead of needing the string to be perfectly smooth everywhere, you only need it to be smooth between points. The integral measures the energy stored in stretching, not the exact curvature at every single point.

### 2.3 Weak Form Statement

After removing or appropriately handling boundary terms, the weak form becomes:

$$
\text{Find } \Phi \text{ such that } \int_\Omega \nabla v \cdot \nabla \Phi , d\Omega = \int_\Omega v f , d\Omega \quad \forall v
$$

**Key insight:** This form only requires $\Phi$ to have first derivatives, making it suitable for numerical approximation with FEM.

**Small example:**

* 1D Poisson: $-\frac{d^2\Phi}{dx^2} = f(x)$ on $[0,1]$, $\Phi(0)=\Phi(1)=0$
* Weak form: $\int_0^1 \frac{d v}{dx} \frac{d \Phi}{dx} dx = \int_0^1 v f dx$
* Here, $v$ can be simple linear functions over small segments, capturing the essential behavior without requiring $\Phi$ to be twice differentiable everywhere.

---

## 3. Finite Element Method (FEM)

FEM approximates the solution of the weak form in a finite-dimensional space.

### 3.1 Domain Discretization

Divide the domain $\Omega$ into small elements (triangles in 2D):

$$
\Omega \approx \bigcup_e \Omega_e
$$

### 3.2 Basis Functions

Approximate the solution as:

$$
\Phi(x, y) \approx \sum_i \Phi_i N_i(x, y)
$$

* $N_i$ are basis functions (piecewise linear over elements)
* $\Phi_i$ are unknown nodal values

Test functions are chosen as the same $N_i$ (Galerkin method).

### 3.3 Discrete System

Inserting this approximation into the weak form gives a linear system:

$$
K \Phi = F
$$

* $K$ = stiffness matrix (integrals of $\nabla N_i \cdot \nabla N_j$)
* $F$ = load vector (integrals of $N_i f$)
* $\Phi$ = vector of nodal values

### 3.4 Element-wise Assembly

Compute each element’s contribution $K^e$, then assemble:

$$
K = \sum_e K^e
$$

This builds the global system efficiently.

### 3.5 Intuitive Summary

* Weak formulation turns derivatives into integrals, reducing smoothness requirements
* FEM discretizes these integrals into sums over elements
* Solving the resulting linear system approximates the continuous solution

**Analogy:** Instead of measuring the curvature at every point, FEM measures how the function bends over small patches and stitches the patches together.

---

## Summary

* Poisson equation models physical phenomena like gravity
* Weak formulation is the bridge from continuous PDE to numerical method
* FEM approximates the weak form by a finite set of basis functions, leading to a solvable linear system
* Small examples illustrate how this works even in 1D or simple domains
