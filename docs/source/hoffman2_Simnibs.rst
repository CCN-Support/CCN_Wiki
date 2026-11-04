.. _hoffman2_Simnibs:

Simnibs
=======

To use Simnibs's GUI interface:

Start an interactive mode first, then

.. code-block:: python

  module load apptainer
  apptainer shell --userns /u/project/CCN/apps/simnibs/simnibs.sif  
  simnibs_gui


Use SimNIBS on Slurm
--------------------

Use the container module below on Slurm instead of the direct image route
above.

Load the module
~~~~~~~~~~~~~~~

Available version: 4.6.0.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module load apptainer
         apptainer shell --userns /u/project/CCN/apps/simnibs/simnibs.sif

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load simnibs/4.6.0

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
~~~~~~~~~

Save this as ``simnibs.sbatch`` beside your SimNIBS Python script,
``analysis.py``. Make the script write to a writable working folder.
Submit with ``sbatch simnibs.sbatch``. Adjust resources for your analysis.
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
         #$ -l h_rt=01:00:00,h_data=4G
         #$ -pe shared 4

         . /u/local/Modules/default/init/modules.sh
         set -euo pipefail
         module load apptainer
         apptainer exec --userns /u/project/CCN/apps/simnibs/simnibs.sif \
           simnibs_python analysis.py

      Submit the saved script:

      .. code-block:: bash

         qsub simnibs.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=simnibs
         #SBATCH --time=01:00:00
         #SBATCH --mem=16G
         #SBATCH --cpus-per-task=4
         #SBATCH --output=simnibs-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         set -euo pipefail
         export TMPDIR="/work/$USER/$SLURM_JOB_ID"
         mkdir -p "$TMPDIR"
         module use /u/project/CCN/apps/modulefiles_rl9
         module load simnibs/4.6.0
         simnibs-exec /bin/bash -c 'exec simnibs_python analysis.py'

GUI
~~~

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal in that desktop. Request a Slurm allocation:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # Connect to the NoMachine desktop and open a terminal.
            qrsh -X -l h_rt=2:00:00,h_data=8G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 --mpi=none -A <your_pi_account> -c 2 --mem=16G -t 2:00:00 --pty bash

3. Go to the working folder that contains your head mesh. Load and start:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module load apptainer
            apptainer shell --userns /u/project/CCN/apps/simnibs/simnibs.sif
            simnibs_gui

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            export TMPDIR="/work/$USER/$SLURM_JOB_ID"
            mkdir -p "$TMPDIR"
            module use /u/project/CCN/apps/modulefiles_rl9
            module load simnibs/4.6.0
            simnibs-exec /bin/bash -c 'exec simnibs_gui'

4. Select a full head mesh with a skin surface, such as
   ``m2m_<subject>/<subject>.msh``. Keep it in the job's home or working
   folder so the container can see it.

Notes
~~~~~

* A CPU pilot ran a magnetic-dipole field simulation on a synthetic sphere.
  The saved field was finite and nonzero. This was not a full head workflow.
* An official Ernie example head loaded through DCV. Scalp and gray matter
  rendered, and a position could be picked. GUI simulation **Run** was not
  tested. Other desktop routes and scientific comparisons were not tested.
* Do not load a cropped tetrahedra-only field output as the head mesh.
  The checked output had no scalp surface and caused a GUI error.
* First start can be slow while the container is converted. Use node-local
  ``TMPDIR`` as above; a scratch-based conversion timed out.
* The checked container could not write to ``/u/scratch``. Access by another
  intended user was not tested.
