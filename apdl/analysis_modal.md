# Modal analysis


## Set up
Mode extraction options (`modopt`): Specify mode extraction method (typically Block Lanczos) and the number of modes to be extracted. By default the mode shape normalization (`nmkey`) is normalized to mass matrix.

Mode expansion options (`maxpand`): Specify whether mode shapes should be expanded (for postprocessing), the number of modes to be expanded, and whether element results are calculated

Prestress effect: Can be acounted for by running an initial static analysis (either large or small deflection) followed by a modal analysis, so that the stress stiffening matrix S is added to the stiffness matrix. If the static analysis is a large-deformation static analysis, then the coordinates are updated prior to the modal analysis, effectively updating both the K and M matrices too.

Sping softening: Can be accounted for by activating spin softening (`omega,,,,1`) prior to the modal analysis 

Loads: Only displacement constraints are used. Applied forces will be ignored.

## Postprocess
Moe shape animation (`anmode`)