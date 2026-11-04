:orphan:

.. _hoffman2_mriqc:

MRIQC
=====

Use MRIQC on Slurm

Load the module
---------------

Available versions: 24.0.2, 22.0.1 and 0.16.1. Select one version:

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load python/3.7.3 afni/21.0.10 ants/2.2.0 fsl/5.0.9
         module load mriqc/0.16.1
         # Legacy native environment; the SGE comparison failed.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load mriqc/0.16.1

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

For the old ``v0.16.1`` name, use ``mriqc/0.16.1``. There is no separate alias.
The Slurm modules use containers, not the old native environment.

Batch job
---------

Save this as ``mriqc.sbatch``. Set absolute input and output paths.
Use a new output folder for each run. Adjust resources for your data.
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
         #$ -l h_rt=03:00:00,h_data=4G
         #$ -pe shared 4

         . /u/local/Modules/default/init/modules.sh
         set -euo pipefail
         module use /u/project/CCN/apps/modulefiles
         module load python/3.7.3 afni/21.0.10 ants/2.2.0 fsl/5.0.9
         module load mriqc/0.16.1
         # Legacy native environment; the SGE comparison failed.
         bids=/absolute/path/to/bids
         out=/absolute/path/to/new-output
         if [ "$1" = participant ]; then
             mriqc "$bids" "$out" participant --participant-label "$2" -w "$TMPDIR/work"
         else
             mriqc "$bids" "$out" group
         fi

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=mriqc
         #SBATCH --time=03:00:00
         #SBATCH --mem=16G
         #SBATCH --cpus-per-task=4
         #SBATCH --output=mriqc-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         set -euo pipefail
         module use /u/project/CCN/apps/modulefiles_rl9
         module load mriqc/0.16.1
         bids=/absolute/path/to/bids
         out=/absolute/path/to/new-output
         if [ "$1" = participant ]; then
             mriqc "$bids" "$out" participant --participant-label "$2" -w "$TMPDIR/work"
         else
             mriqc "$bids" "$out" group
         fi

Submit one participant job per subject. Then submit the group job with a
success dependency. Change these subject labels to match your data:

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # Save the Grid Engine script as mriqc.sh.
         # Run sequentially; stop if a participant fails.
         qsub -sync y mriqc.sh participant 01 &&
         qsub -sync y mriqc.sh participant 02 &&
         qsub mriqc.sh group

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         p1=$(sbatch --parsable mriqc.sbatch participant 01)
         p2=$(sbatch --parsable mriqc.sbatch participant 02)
         sbatch --dependency=afterok:"$p1":"$p2" mriqc.sbatch group

Notes
-----

* All three versions passed participant and group checks for two human
  participants with T1w and BOLD data. Other datasets and modalities were
  not tested.
* Version 22.0.1 is for human data only. Rat templates are not installed;
  this module rejects rat data.
* The official 24.0.2 image reports
  ``24.1.0.dev0+gd5b13cb5.d20240826``. This is the accepted image identity.
* The module sets CPU and memory options from the Slurm allocation.
  It adds ``--no-sub`` to stop automatic metric submission.
* **Do not press "Post to WebAPI" in HTML reports.** That button sends a
  rating to an outside service. ``--no-sub`` does not block that button.
* Network isolation and isolation from the real home directory were not
  independently tested. Equivalence to SGE results is not established.
* The 0.16.1 image has restricted group access. Runs by other intended users
  were not tested.
