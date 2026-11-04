.. _hoffman2_CONN:
  
CONN
====

The newest version in Hoffman2 currently is 19.b

To use it, you need to load Matlab and set path for SPM

.. code-block::
  
  module load Matlab/9.7
  module load conn/19.b

Start Matlab GUI.

In MatLab GUI, set path for

.. code-block::
  
  /u/project/CCN/apps/conn/conn19b
  /u/project/CCN/apps/spm12

Then in MatLab terminal, type conn to start it.


Use CONN on Slurm
-----------------

The instructions above describe the older setup.
For Slurm, use the modules below. They set the MATLAB and SPM paths.

**Load the module**

Available versions: 22.a and 19.b. Both are source versions.
They load MATLAB R2026a, SPM12 r6906 and the batch display helper.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load Matlab/9.7
         module load conn/19.b

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load conn/22.a

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

**Batch job**

Prepare your CONN batch script as ``my_conn_job.m``.
Save this shell script as ``conn_job.sh``, change the PI account, then
submit it with ``sbatch conn_job.sh``.
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
         #$ -l h_rt=00:40:00,h_data=4G
         #$ -pe shared 2

         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         module load Matlab/9.7
         module load conn/19.b
         matlab -batch "addpath('/u/project/CCN/apps/conn/conn19b'); addpath('/u/project/CCN/apps/spm12'); conn_batch('my_conn_job.m')"

      Submit the saved script from the terminal:

      .. code-block:: bash

         qsub conn_job.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=conn_batch
         #SBATCH --time=00:40:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=conn_batch.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load conn/22.a
         matlab -batch "conn_batch('my_conn_job.m')"

Use ``conn/19.b`` instead to select 19.b.
Keep Slurm's short ``TMPDIR``. A long path can prevent MATLAB from starting.
CONN's default Slurm profile passed a child-job check for both versions.
Set the resources in your CONN batch for the work that it will run.

**GUI**

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal on that desktop.
3. Start a Slurm shell. Replace the account text before running the command:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # Connect to the NoMachine desktop and open a terminal.
            qrsh -X -l h_rt=0:40:00,h_data=4G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your pi account> -c 2 --mem=8G -t 0:40:00 --pty bash -l

4. Load CONN and start MATLAB:

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles
            module load Matlab/9.7
            module load conn/19.b
            matlab -desktop -r "addpath('/u/project/CCN/apps/conn/conn19b'); addpath('/u/project/CCN/apps/spm12'); conn"

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load conn/22.a
            matlab -desktop -r "conn"

5. Close CONN and MATLAB, then type ``exit`` to end the Slurm shell.

**Notes**

Both versions passed startup, version, template PNG and Slurm child-job
checks. Version 22.a passed a bounded DCV Viewer check of the Tools menu,
example anatomy display and close. Project typing and save/reopen were
not repeated in that check. Version 19.b has only a basic DCV display
check, not a full GUI workflow. A real lab comparison with SGE was not tested.
