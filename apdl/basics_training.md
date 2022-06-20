# Training

## 1. Intro
- FEA: FEA simulates loading conditions on a design and determines the design's response to these conditions.
- Static equilibrium: External forces (loads) balanced by internal forces. FEA is based on equilibrium, `[K]{U}={F}` -> `{U}=[K]^-1{F}`. Solve for U, then strain, stress, etc.
- [U]: DOFs of a `node` are determined by the element type connected to the node (e.g. 3D structural solid has UX, UY, UZ).
- [K]: Stiffness matrix for an `element` is based on material properties, geometry and shape of the element, and type of the element. They are then assembled into a `global stiffness matrix` based on how elements are connected. Its size is the total number of nodes times number of DOFs per node. [K] is singular and cannot be inverted until boundary conditions are defined to prevent rigid-body motions. 
- Element shape function: FEA solves for DOF values only at nodes. Element shape functions give the shape of the results within the element. It can be linear (low-order elems, corner/end nodes only) or quadratic (high-order, corner nodes and mid-side nodes). If using linear elements, then usually a larger number of elements is needed to dsicretize the structure to obtain a smooth realistic distribution of results. 

![image](https://user-images.githubusercontent.com/96508769/174611894-4b3b2562-6e25-498f-95c0-e1d74a432b19.png)
(Link: https://core.ac.uk/download/pdf/38116915.pdf)

- Displacements are continuous throughout structure. Stresses and strains are not necessarily so.

## 2. ANSYS
- Memory: workspace space (`-m`) = database space (`-db`) + scratch space.
- Guideline: Use 1G workspace and 10G disk space per million DOFs.
