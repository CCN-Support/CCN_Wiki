:orphan:

.. _hoffman2_osprey:

Osprey
======

Use Osprey on Slurm

Load the module
---------------

Available version: 2.9.6. Run programs in a Slurm job, not on a login node.
The module loads MATLAB, SPM and the display dependencies.
Run ``osprey_setup`` in MATLAB to select the Slurm source fixes.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # See the Grid Engine version table in section 2.1

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load osprey/2.9.6

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
---------

Put your MATLAB analysis script in a writable work folder as ``analysis.m``.
Set its input paths and write all results to your own folder, not the shared
installation. Save this job script there as ``osprey.sbatch``.
Submit with ``sbatch osprey.sbatch``.
Checked on Slurm: this script ran as shown (only the PI account changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # See the Grid Engine version table in section 2.1

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=osprey
         #SBATCH --time=00:45:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=osprey-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account
         module use /u/project/CCN/apps/modulefiles_rl9
         module load osprey/2.9.6
         export OMP_NUM_THREADS="$SLURM_CPUS_PER_TASK"
         matlab -batch "osprey_setup; run('analysis.m')"

GUI
---

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal in a writable work folder. Put a saved Osprey container
   named ``processed.mat`` there. It must contain ``MRSCont``.
3. Request a Slurm shell. Replace ``<your pi account>`` with your account.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # From a NoMachine desktop terminal:
            qrsh -X -l h_rt=0:45:00,h_data=8G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your pi account> -c 2 --mem=16G -t 00:45:00 --pty bash

4. Load the module and open the saved container.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # See the Grid Engine version table in section 2.1

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load osprey/2.9.6
            matlab -nodesktop -r "osprey_setup; s=load('processed.mat'); MRSCont=s.MRSCont; MRSCont.outputFolder=pwd; fclose(fopen('LogFile.txt','a')); OspreyGUI(MRSCont)"

Checked on Slurm through DCV: these commands ran as shown (only the PI account changed), and Osprey opened the saved container.
Use GUI **Exit** to close Osprey, then enter ``exit`` at the MATLAB prompt.

Notes
-----

Version 2.9.6 processed two stored example spectra and saved a result and
quality metrics. The Optimization and Statistics and Machine Learning
MATLAB toolboxes were installed and licensed in the pilot.
Raw-file loading, fitting, SPM processing and full analysis were not tested.
The numerical correctness of the results was not tested.

The Slurm module includes fixes for dataset counts and the arrow-key error.
With the deployed GUI fix, connected DCV Viewer input changed subjects with
a click and the Up/Down keys. The ``z`` key press/release and Exit also passed.
Other phase keys, list boundaries and the numerical phase result were not
tested. XQuartz and NoMachine were not tested.
