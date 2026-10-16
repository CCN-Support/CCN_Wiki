.. _hoffman2_dmriprep:

dmriprep
========

Use singularity exec to execute a specific command within the container.

.. code-block:: python

  module load apptainer
  apptainer exec /u/project/CCN/apps/dmriprep/dfmriprep.sif dmriprep -h  
  apptainer exec /u/project/CCN/apps/dmriprep/dfmriprep.sif data/bids_root/ out/ participant -w work/

Use apptainer shell to interact with the container's environment through a shell interface.

.. code-block:: python

  module load apptainer
  apptainer shell --userns /u/project/CCN/apps/dmriprep/dfmriprep.sif 
  dmriprep -h

Comprehensive documentation on dmriprep can be found at: https://www.nipreps.org/dmriprep/usage.html#usage
