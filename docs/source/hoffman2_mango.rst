:orphan:

.. _hoffman2_mango:

MANGO
=====

Use MANGO on Slurm

Load the module
---------------

Available version: 4.1. Run programs in a Slurm job, not on a login node.
Do not load the old SGE Mango module at the same time.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load mango/20210308

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load mango/4.1

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
---------

Copy your image to a writable work folder as ``input.nii.gz``.
Save this script there as ``mango.sbatch``. Submit with ``sbatch mango.sbatch``.
The threshold of 4000 is an example; choose a value for your image.
Checked on Slurm: this script ran as shown (only the PI account changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # The mango-* launchers are not available on Grid Engine.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=mango
         #SBATCH --time=00:15:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=mango-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account
         set -e
         module use /u/project/CCN/apps/modulefiles_rl9
         module load mango/4.1
         mango-imageinfo input.nii.gz
         mango-convert2nii -out converted.nii input.nii.gz
         mango-makeroi -min 4000 input.nii.gz

These command-line tools do not need a screen. With a compressed input,
``-out converted.nii`` writes ``converted.nii.gz``. The ROI is saved as
``input_roi.nii.gz``.

GUI
---

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal.
3. Request a Slurm shell. Replace ``<your pi account>`` with your account.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # From a NoMachine desktop terminal:
            qrsh -X -l h_rt=2:00:00,h_data=4G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your pi account> -c 2 --mem=8G -t 2:00:00 --pty bash

4. Load the module and open your image. Replace ``input.nii.gz`` with its path.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles
            module load mango/20210308
            mango "$PWD/input.nii.gz"

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load mango/4.1
            mango input.nii.gz

5. On first start, read the licence dialog and make your choice. Close Mango
   with **Quit** so that it saves the choice. A killed job does not save it.

Notes
-----

Version 4.1 passed image information, conversion and ROI creation checks.
Converted image and ROI geometry matched FSL. Relative file names worked.
The other seven ``mango-*`` wrappers showed usage text, but image processing
with them was not tested.

DCV passed eight specified GUI steps with input sent on the desktop display.
Connected DCV Viewer input and zoom were not tested. On NoMachine, image
viewing, slice keys, brightness, ROI draw/save/reopen and Quit passed.
Access by users outside the tested shared application group was not tested.
