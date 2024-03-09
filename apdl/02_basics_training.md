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
- Unit system: `/units` lets you specify a unit system, but it is not enforced, simply a book-keeping record.


## 3. Types of analysis:
* Structural (or stress):
  * General term used to describe analyses where the results include displacements, strains, and stresses. Includes several types such as static, transient, modal, spectrum, harmonic, and explicit dynamics.  
  * Static or dynamic?: When a body is subjected to a loading/excitation, it responds with 3 types of forces: static (due to stiffness), intertia (due to mass), and damping forces (due to damping). A static analysis considers the first only. A dynamic analysis considers all 3.
  * Linear or nonlinear?: Does the load changes the stiffness of the structure? Whther the deformation is small (nonlinearity due to large deformation), whether the strains and stresses are within the elastic limit (nonlinearity due to material properties), and whether there's no abrupt change in stiffness such as contact (nonlinearity due to changeing status).
* Thermal
* Fluid
* Coupled

## 4. General steps of an analysis
- 1. problem definition (what type of analysis? what elements?)
- 2. pre (materials, mesh, BCs)
- 3. solve (loads, solve)
- 4. post


### 4.1 Element attributes:
Element types: determines dimensionality, DOFs, element shape, shape function.
  - Line elements (beam, spar, spring)
  - Shells (model thin panels or curved surfaces)
  - 2D solids (works in X-Y plane)
  - 3D solids (8-noded hex SOLID45, 10-noded tets SOLID92, 20-nonded brick SOLID95 which can also degenerate into pyramids, prism, and tets)

Real constants: define propertiese that cannot be defined by element shape (e.g. cross section of a beam element). Most 3D solid elements do not require real constants.

Material properties: use `/mplib`, `mpread`, `mp` commands


### 4.2 Types of loads
1. DOF constraints (e.g. displacement constraints `d`, enforce symmetry or anti-symmetry )
2. Concentrated loads (e.g. point loads `f`)
3. Surface loads (e.g. pressure `sf`, `sfe`, positive=compressive i.e. towards centroid of the element)
4. Body loads (e.g. temperature `tunif`, `tref`)
5. Inertia loads (loads due to structural mass or inertia, such as gravity (`acel`), rotational velocity (`omega` in unit [rad/s] (or more generally, [rad/time unit]) and is applied about the Global Cartesian coordinate system axes), and rotational acceleration (`domega`))


### 4.3 Types of solver
1. Direct elimination (linear)
   a. Frontal
   b. Sparse (usually the default)
2. Iterative (guess answer -> error check -> update)
   a. PCG (Pre-conditioned Conjugate Gradient)
   b. ICCG (Incomplete Cholesky Conjugate Gradient)
   c. JCG (Jacobi Conjugate Gradient)
3. Parallel 


### 4.4 Postprocessing
  - Deformed shape (`pldisp` and `andisp` for animation)
  - Stresses (component and principal stresses). Nodal solution (`plnsol`, `ancntr` for animation) is smooth and continuous (stresses are averaged at nodes). Element solution (`plesol`) is not (no averaging). Regions where they differ a lot are where mesh may be too coarse.
  - Reaction forces (`prrsol`): the sum of reaction forces must equal the sum of applied loads.

displacements are continuous throughout the structure. Stress and strain are not necessarily continuous across element boundaries.
