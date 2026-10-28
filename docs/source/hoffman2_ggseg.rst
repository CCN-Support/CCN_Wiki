.. _hoffman2_ggseg:

ggseg
=====

From a Hoffman2 node

Load the required modules:

.. code-block :: python

  module load R/4.2.2 
  module load anaconda3/2022.05 
  module load freesurfer/7.3.2 
  module load proj/7.1.1 
  module load gdal/3.1.3

Add the path

.. code-block :: python

  export PATH=$PATH:/u/project/CCN/apps/conda/rh7/R4.2.2_ggseg:/u/project/CCN/apps/R_libs/rh7/4.2.2_ggseg

Activate the conda environment:

.. code-block :: python

  conda activate /u/project/CCN/apps/conda/rh7/R4.2.2_ggseg

Launch R with the command "R" and enter the following:

.. code-block :: python

  .libPaths("/u/project/CCN/apps/R_libs/rh7/4.2.2_ggseg")

Load the library in R

.. code-block :: python

  library(ggseg)
  library(ggseg3d)
  library(ggsegExtra)
