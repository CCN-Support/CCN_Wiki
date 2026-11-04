:orphan:

.. _hoffman2_spm:

SPM
===

Use SPM on Slurm

SPM has tools for brain image analysis. Run it in a Slurm job.

Load the module
---------------

Available modules:

* ``spm-standalone/26.10.01``: SPM26; the default standalone version.
* ``spm-standalone/25.01.02``: SPM25.
* ``spm/26.10.01``: SPM26 in MATLAB R2026a.
* ``spm/12-r6906``: SPM12 in MATLAB R2026a.

The standalone modules select their matching MATLAB Runtime.
They do not need a MATLAB licence. Load one SPM version per job.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # SPM26 is not available on Grid Engine.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load spm-standalone/26.10.01

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
---------

Save an SPM batch as ``my_job.m``. Save the script below as ``spm_job.sh``.
Change the PI account, then submit it with ``sbatch spm_job.sh``.
Checked on Slurm: this script ran as shown (only the PI account changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # SPM26 is not available on Grid Engine.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=spm_batch
         #SBATCH --time=00:30:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=spm_batch.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load spm-standalone/26.10.01
         run_spm26 batch my_job.m

For SPM25, load ``spm-standalone/25.01.02`` and use
``run_spm25 batch my_job.m``. For MATLAB, load ``spm/26.10.01`` or
``spm/12-r6906`` and use ``matlab -batch "spm_jobman('run','my_job.m')"``.
The MATLAB modules load the display helper for batch figures.

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

            # SPM26 is not available on Grid Engine.

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your pi account> -c 2 --mem=8G -t 1:00:00 --pty bash -l

4. Load the module and start SPM:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # SPM26 is not available on Grid Engine.

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load spm-standalone/26.10.01
            run_spm26 fmri

5. Use SPM's Quit control, then type ``exit`` to end the Slurm shell.

For SPM25 standalone, load its module and start ``run_spm25 fmri``.
DCV template display, test clicks and clean Quit passed for both standalone
versions and the two MATLAB versions. DCV Viewer input and GUI processing
were not tested.

Notes
-----

The four listed modules passed batch smoothing and Graphics PNG checks.
SPM26 also passed missing-input failure and module unload checks.
A lab workflow comparison with SGE was not tested.
For a noninteractive standalone ``eval`` that makes figures, save the output
and end with ``close all force; exit(0);``. Otherwise it can stay open until
the time limit. The ``batch`` command handles shutdown itself.
