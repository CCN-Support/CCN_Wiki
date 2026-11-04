.. _hoffman2_OpenSmile:

OpenSmile
=========

This module needs to run in CentOS 7. To use it,

.. code-block:: python

  module load gcc/7.5.0
  module load mplayer/1.4
  module load opensmile


Use openSMILE on Slurm
----------------------

Use this route on Slurm. The CentOS 7 instructions above are for the old
environment.

Load the module
~~~~~~~~~~~~~~~

Available version: 3.0.0.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load gcc/7.5.0
         module load mplayer/1.4
         module load opensmile/3.0.0

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load opensmile/3.0.0

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
~~~~~~~~~

Save this as ``opensmile.sbatch`` in a new writable folder.
Submit it with ``sbatch opensmile.sbatch``. It uses the shipped audio and
eGeMAPS configuration and writes ``features.csv``.
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
         #$ -l h_rt=00:20:00,h_data=2G
         #$ -pe shared 1

         . /u/local/Modules/default/init/modules.sh
         set -eo pipefail
         module use /u/project/CCN/apps/modulefiles
         module load gcc/7.5.0
         module load mplayer/1.4
         module load opensmile/3.0.0
         SMILExtract -C /u/project/CCN/apps/opensmile/3.0.0/opensmile/config/egemaps/v01b/eGeMAPSv01b.conf \
           -I /u/project/CCN/apps/opensmile/3.0.0/opensmile/example-audio/opensmile.wav \
           -csvoutput "$PWD/features.csv" -appendcsv 0 -timestampcsv 0 -instname pilot

      Submit the saved script:

      .. code-block:: bash

         qsub opensmile.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=opensmile
         #SBATCH --time=00:20:00
         #SBATCH --mem=2G
         #SBATCH --cpus-per-task=1
         #SBATCH --output=opensmile-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         set -eo pipefail
         source /u/local/Modules/5.6.1/gcc-11.5.0/init/bash
         set -u
         module purge
         module use /u/project/CCN/apps/modulefiles_rl9
         module load opensmile/3.0.0
         SMILExtract -C "$OPENSMILE_ROOT/config/egemaps/v01b/eGeMAPSv01b.conf" \
           -I "$OPENSMILE_ROOT/example-audio/opensmile.wav" \
           -csvoutput "$PWD/features.csv" -appendcsv 0 -timestampcsv 0 -instname pilot

Notes
~~~~~

* Two extractions produced one row of 88 finite features with the same
  names and values. This checked output shape and repeatability, not
  scientific correctness.
* The shipped configuration reported an ``lldconcat`` full-buffer warning.
  A larger-buffer comparison gave the same 88 values for this audio only.
  Keep the shipped configuration unchanged. Effects on other audio,
  configurations and low-level output were not tested.
* Representative lab workflows, SGE comparisons and GUI use were not tested.
  Use ``SMILExtract`` as a command-line tool.
* Access by other intended users was not tested.
