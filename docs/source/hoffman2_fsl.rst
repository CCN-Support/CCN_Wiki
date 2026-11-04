:orphan:

.. _hoffman2_fsl:

FSL
===

Use FSL on Slurm

FSL has tools for MRI, fMRI and diffusion image analysis.
Run commands in a Slurm job, not on the login host.

Load the module
---------------

Available versions: 6.0.7.23, 6.0.7.15, 6.0.7.4, 6.0.7.1, 6.0.4,
6.0.3, 6.0.1, 6.0.0, 5.0.11 and 5.0.9.
Version 5.0.9 is command line only; its GUI is retired.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load fsl/6.0.4

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load fsl/6.0.7.23

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
---------

Save this as ``fsl_job.sh``. Change the PI account, then submit it with
``sbatch fsl_job.sh``. The example copies the bundled standard image.
Checked on Slurm: this script ran as shown (only the PI account changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #$ -cwd
         #$ -o joblog.$JOB_ID
         #$ -j y
         #$ -l h_rt=00:05:00,h_data=1G
         #$ -pe shared 1

         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         module load fsl/6.0.4
         export NO_FSL_JOBS=true
         fslmaths "$FSLDIR/data/standard/MNI152_T1_2mm.nii.gz" -mul 1 template_copy
         fslstats template_copy -R

      Submit the saved script from the terminal:

      .. code-block:: bash

         qsub fsl_job.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=fsl_copy
         #SBATCH --time=00:05:00
         #SBATCH --mem=1G
         #SBATCH --cpus-per-task=1
         #SBATCH --output=fsl_copy.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load fsl/6.0.7.23
         fslmaths "$FSLDIR/data/standard/MNI152_T1_2mm.nii.gz" -mul 1 template_copy
         fslstats template_copy -R

The Slurm ``fsl_sub`` setup passed single jobs, arrays and job dependencies.
``randomise_parallel`` matched a serial run. For 6.0.7.15 and 6.0.7.23,
``fsl_sub -T`` sets minutes and ``-R`` sets GB. Older versions use UCLA
resource rules instead. Pass a script file for several commands; do not
pass them as a quoted ``bash -c`` string.

GUI
---

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal on that desktop.
3. Start a Slurm shell. Replace the account text before running the command:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # Connect to the NoMachine desktop and open a terminal.
            qrsh -X -l h_rt=1:00:00,h_data=4G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your pi account> -c 2 --mem=8G -t 1:00:00 --pty bash -l

4. Load FSL and start FSLeyes:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles
            module load fsl/6.0.4
            fsleyes "$FSLDIR/data/standard/MNI152_T1_2mm.nii.gz"

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load fsl/6.0.7.23
            fsleyes "$FSLDIR/data/standard/MNI152_T1_2mm.nii.gz"

5. Close FSLeyes, then type ``exit`` to end the Slurm shell.

FSLView is also available for 6.0.4, 6.0.3, 6.0.1, 6.0.0 and 5.0.11.
Load the required version and use ``fslview`` in place of ``fsleyes``.

Notes
-----

All listed versions passed bounded command-line and Slurm submission checks.
FSL 6.0.4 is restricted to Intel processors by its module setup.
FSLeyes 6.0.7.23 passed template display, input and clean close on DCV
from the new module folder. A normal close can ask to save the layout.
For 6.0.7.4 and 6.0.7.1, the launcher sets the graphics libraries;
DCV template display passed, but image save and reopen were not tested
after that change. GPU computation was not tested.
