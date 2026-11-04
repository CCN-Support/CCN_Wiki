.. _hoffman2_HCPBench:

HCP
===

.. code-block:: python

  module load hcp

If you are experiencing crashing trying to load hcp (mesa or other related crashing errors) do the following:

.. code-block:: python

  cd ~
  wget https://www.humanconnectome.org/storage/app/media/workbench/workbench-rh_linux64-v1.5.0.zip
  unzip workbench-rh_linux64-v1.5.0.zip
  cd workbench/exe_rh_linux64/
  ./wb_view

Use HCP Workbench on Slurm
--------------------------

Load the module
~~~~~~~~~~~~~~~

Available module versions: 2.2.1, 2.0.1, 1.5.0, 1.3.2, 1.2.3, 1.1.1 and 1.0.
Run programs in a Slurm job, not on a login node.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load hcp/1.3.2

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load hcp/2.2.1

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
~~~~~~~~~

Save this script as ``workbench.sbatch``. Put a surface metric named
``input.func.gii`` in the same folder. Submit with ``sbatch workbench.sbatch``.
Checked on Slurm: this script ran as shown (only the PI account changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         # Save as workbench.sh.
         #$ -cwd
         #$ -o joblog.$JOB_ID
         #$ -j y
         #$ -l h_rt=0:20:00,h_data=2G
         #$ -pe shared 1
         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         module load hcp/1.3.2
         wb_command -metric-math 'x*2+1' output.func.gii -var x input.func.gii

         # Submit from the work folder:
         qsub workbench.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=workbench
         #SBATCH --time=00:20:00
         #SBATCH --mem=2G
         #SBATCH --cpus-per-task=1
         #SBATCH --output=workbench-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account
         module use /u/project/CCN/apps/modulefiles_rl9
         module load hcp/2.2.1
         wb_command -metric-math 'x*2+1' output.func.gii -var x input.func.gii

GUI
~~~

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

4. Load the module and start the viewer.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles
            module load hcp/1.3.2
            wb_view

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load hcp/2.2.1
            wb_view

Use DCV for the viewer. The 2.2.1 image area was blank over XQuartz.

Notes
~~~~~

All seven module versions passed a batch metric calculation on synthetic data.
DCV checks showed a synthetic surface, input responses and clean exit.
The 1.5.0 module now uses system OpenGL; overlay redraw and Exit passed with
connected DCV Viewer input. Fullscreen for 1.5.0 was not tested; the 1.3.2
fullscreen check timed out. Scene save/reopen and scientific workflows were
not tested.

The ``hcp/2.0.1`` module reports version 1.5.0.
The ``hcp/1.5.0`` module reports version 1.4.2.
