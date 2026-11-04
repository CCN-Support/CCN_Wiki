:orphan:

.. _hoffman2_gift:

GIFT
====

Use GIFT on Slurm

GIFT runs group independent component analysis (ICA) in MATLAB.

Load the module
---------------

Available versions: ``4.0c`` and ``4.0b``. Load only one version.
The source modules load MATLAB R2026a and a display helper.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # No GIFT module; add the source folder in MATLAB.
         matlab -r "addpath(genpath('/u/project/CCN/apps/gift/rh7/gift4.0c/icatb'))"

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load gift/4.0c

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
---------

Save this as ``gift.sbatch``. Replace the account and batch-file path.
In your GIFT batch file, set ``parallel_info.mode = 'serial'`` and
``parallel_info.num_workers = 1``. Some supplied examples use parallel mode.
Keep Slurm's short ``TMPDIR``. Use a writable output folder.
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
         #$ -l h_rt=00:45:00,h_data=4G
         #$ -pe shared 2

         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         # No GIFT module; use the source folder.
         matlab -nodisplay -r \
           "addpath(genpath('/u/project/CCN/apps/gift/rh7/gift4.0c/icatb')); icatb_batch_file_run('/absolute/path/my_batch.m'); exit"

      Submit with ``qsub gift.sge`` after saving the script as ``gift.sge``.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=gift
         #SBATCH --time=00:45:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=gift.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load gift/4.0c
         export GIFT_SOURCE="${MATLABPATH%%:*}"
         ccn-xvfb-run matlab -singleCompThread -batch \
           "addpath(genpath(getenv('GIFT_SOURCE'))); icatb_batch_file_run('/absolute/path/my_batch.m')"

Submit with ``sbatch gift.sbatch``.

GUI
---

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal. Request a Slurm shell with your PI account:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         Open the NoMachine desktop, then open a terminal:

         .. code-block:: bash

            qrsh -X -l h_rt=2:00:00,h_data=4G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your_pi_account> -c 2 --mem=8G -t 2:00:00 --pty bash

3. In that shell, load one version and start GIFT:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # No GIFT module; add the source folder in MATLAB.
            matlab -r "addpath(genpath('/u/project/CCN/apps/gift/rh7/gift4.0c/icatb')); groupica"

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load gift/4.0c
            export GIFT_SOURCE="${MATLABPATH%%:*}"
            matlab -r "addpath(genpath(getenv('GIFT_SOURCE'))); groupica"

4. Open results from a writable analysis folder. After GIFT **Exit**, type
   ``exit`` in MATLAB, or close MATLAB, to end its process. GIFT Exit can
   close all GIFT windows while MATLAB stays open.

Notes
-----

- Both versions passed small serial, two-subject batches and saved plots.
- Both displayed component maps on DCV. Version 4.0b also passed connected
  Viewer input checks. Version 4.0c Viewer input was not tested.
- Display writes files in the analysis folder. A read-only folder or a full
  quota can stop it. A full home quota can also stop MATLAB startup.
- First-use MATLAB setup in a new writable home can take about five minutes.
- Full save/reopen, parallel use, standalone use, other GUI routes and
  scientific agreement with lab or SGE results were not tested.
