:orphan:

.. _hoffman2_gradunwarp:

gradunwarp
==========

Use gradunwarp on Slurm

gradunwarp corrects image distortion from the scanner's gradient field.

Load the module
---------------

Available version: ``1.1.0``. The module loads the shared Python 2.7 runtime
and loads FSL if FSL is not already loaded. FSL 6.0.7.23 was tested.
Other FSL versions were not tested with this tool.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # Historical route; Python 2.7.13 is no longer available.
         module use /u/project/CCN/apps/modulefiles
         module use /u/project/CCN/apps/modulefiles_rh6
         module load gradunwarp/1.1.0

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load gradunwarp/1.1.0

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
---------

Save this as ``gradunwarp.sbatch``. Replace the account and absolute paths.
Supply your scanner's approved coefficient file (``.grad``).
No scanner coefficient file is supplied with the tool.
Create a new run folder before submission. Use a separate folder for each
run: the program writes ``fullWarp_abs.nii.gz`` in the current folder.
The example uses Siemens-format coefficients.
Checked on Slurm: this script ran as shown (only the PI account and example paths changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #$ -cwd
         #$ -o joblog.$JOB_ID
         #$ -j y
         #$ -l h_rt=01:00:00,h_data=4G
         #$ -pe shared 2

         # Historical route; fails because Python 2.7.13 is absent.
         . /u/local/Modules/default/init/modules.sh
         set -euo pipefail
         module use /u/project/CCN/apps/modulefiles
         module use /u/project/CCN/apps/modulefiles_rh6
         module load gradunwarp/1.1.0
         cd /absolute/path/to/new-run-folder
         gradient_unwarp.py /absolute/path/to/input.nii.gz output.nii.gz siemens \
           -g /absolute/path/to/scanner.grad

      Submit with ``qsub gradunwarp.sge`` after saving as ``gradunwarp.sge``.
      This old route does not work: its Python interpreter is absent.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=gradunwarp
         #SBATCH --time=01:00:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=gradunwarp.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         set -euo pipefail
         module use /u/project/CCN/apps/modulefiles_rl9
         module load gradunwarp/1.1.0
         cd /absolute/path/to/new-run-folder
         gradient_unwarp.py /absolute/path/to/input.nii.gz output.nii.gz siemens \
           -g /absolute/path/to/scanner.grad

Submit with ``sbatch gradunwarp.sbatch``. Run only inside a Slurm job;
the launcher refuses to run on a login node.

Notes
-----

- Version 1.1.0 passed known-answer checks with made-up coefficients:
  zero distortion and a 1% linear change.
- A public T1w image run and a rerun gave identical image and warp data.
  A rerun on a different compute node was not tested.
- Accuracy with a lab's scanner ``.grad`` file and lab data was not checked.
- The output keeps the image shape, position matrices and voxel sizes.
  It changes the qform code to 0, the sform code to 2, and units to unknown.
  The tested input changed from int16 to float32. Check headers before use.
- The original code has a field-grid offset. Its Jacobian is 1 for the
  tested 1% x-only change, not the physical value 1.01. These were not fixed.
- The shared source files have restricted access. Runs by other intended
  users were not tested. This is a command-line tool; it has no GUI.
