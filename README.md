# -OpenFOAM-Porous-flow-Project-
This repository contains OpenFOAM simulations of multiphase flow in constructed porous media geometries. The geometries and meshes were generated using Gmsh, and the simulations are performed using the interFoam solver to study the interaction between immiscible fluids within structured and random porous media.

The main objective of this project is to investigate how fluid displacement occurs in porous media under the effect of gravity-driven flow, without imposing any inlet or outlet velocity. The flow is driven solely by gravitational forces, allowing for a more physically realistic representation of drainage and infiltration processes.

## Project Overview

The repository is organized around a Porous Flow framework using the interFoam solver. Within this framework, both 2D extruded and fully 3D configurations are considered.

- **2D extruded cases** correspond to essentially two-dimensional geometries extended with a small thickness in the z-direction, allowing for reduced computational cost while preserving 3D solver capabilities.
- **3D cases** represent fully three-dimensional porous media configurations.

Within the 2D extruded cases, three types of porous media structures are investigated:

- **Regular arrays:** particles arranged in a uniform grid
- **Staggered arrays:** particles arranged in offset configurations to enhance pore connectivity
- **Random arrangements:** particles distributed non-uniformly to mimic more realistic porous structures

## 3D Cases

The 3D configurations follow a structure similar to the 2D extruded cases, including regular, staggered, and random porous media arrangements. The same multiphase flow scenarios (water–air and water–oil) are investigated under gravity-driven conditions.

However, in contrast to the 2D random cases, only particles of uniform size are considered in the 3D simulations. This allows for a clearer analysis of three-dimensional flow behavior while keeping the geometric complexity manageable.


## Multiphase Flow Cases

Two main fluid configurations are studied:

- **Water–Air system**
- **Water–Oil system**

In all cases:

- Water is initially placed at the top of the domain
- The porous medium is initially filled with either air or oil
- Flow occurs due to gravity only (no imposed velocity at inlet or outlet)
  
## Additional variations (Random media only)

For the random porous media cases, two additional configurations are considered:

-**Particles of uniform size**
-**Particles of varying sizes**

This allows investigation of the effect of pore size distribution on flow dynamics.

## Boundary and Physical Conditions
**Driving mechanism:** Gravity-driven flow only
**No imposed velocity** at inlet or outlet
**All external boundaries and particle surfaces** are treated as **walls**
A **no-slip boundary condition** is applied on all walls and solid surfaces

## Pressure Treatment (interFoam)

The simulations use the standard pressure formulation of the interFoam solver. FixedFluxPressure on boundaries.

## Cases Structure
PorousFlow/
└── interFoam/
    ├── 2D_extruded/
    │   ├── regular/
    │   ├── staggered/
    │   └── random/
    │       ├── same_size_particles/
    │       └── different_size_particles/
    └── 3D/
        ├── regular/
        ├── staggered/
        └── random/
            └── same_size_particles/


Each individual case follows the standard OpenFOAM structure:

- `0/` : Initial and boundary field files
- `constant/` : Physical properties and mesh files
- `system/` : Solver settings and numerical schemes
- `scripts/` : Post-processing utilities
- `geometry.geo` : Geometry defined using Gmsh
- `geometry.msh` : Mesh generated using Gmsh
  
## Computational Resources

Due to the high computational cost of the 3D simulations, particularly the large meshes containing millions of cells, these cases were not feasible to run on a standard laptop. As a result, the 3D simulations were executed using CloudHPC resources, which provide the necessary computational power and memory to handle large-scale multiphase flow problems.

The use of CloudHPC enabled:

- Efficient handling of complex 3D porous geometries
- Faster simulation times compared to local execution
- Stable computation of gravity-driven multiphase flow in large domains

In contrast, the 2D extruded cases, which are significantly less demanding, were run locally.

## Purpose of the Study
This project allows:

- Analysis of fluid displacement mechanisms in porous media
- Comparison between structured and random geometries
- Study of multiphase interactions (water–air vs water–oil)
- Investigation of the impact of particle arrangement and size distribution
