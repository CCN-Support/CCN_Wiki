.. _hoffman2_ica-aroma_py27:

ICA-AROMA
=========
  
Module ica-aroma_py27 is the regular ica-aroma program with Python2.7. This module name is to avoid confusion with ica-aroma module in Hoffman which works with FMRIprep and requires Python 3

To use it, you'll need the following modules

.. code-block:: python

  module load python/2.7.15
  module load ica-aroma_py27/0.4.5
  module load fsl
  export PYTHONPATH=/u/project/CCN/apps/ica-aroma_py27/site-packages

Show its help menu

.. code-block:: python

  ICA_AROMA.py -h


Use ICA-AROMA on Slurm
----------------------

Load the module
~~~~~~~~~~~~~~~

Available versions: ``0.4.5`` and ``0.4.1-beta``.
On Slurm, load ``ica-aroma/<version>``, not ``ica-aroma_py27``.
There is no ``ica-aroma_py27`` alias on Slurm.
The module loads Python 2.7 and FSL 5.0.9.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load python/2.7.15
         module load ica-aroma_py27/0.4.5
         module load fsl
         export PYTHONPATH=/u/project/CCN/apps/ica-aroma_py27/site-packages

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load ica-aroma/0.4.5

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
~~~~~~~~~

Save this as ``aroma.sbatch``. Replace the account and absolute paths.
Supply preprocessed functional data, motion parameters, a functional mask,
and transforms from functional space through anatomy to standard space.
Set ``-tr`` to your data's repetition time in seconds.
Use absolute paths: the program changes to its install folder at startup.
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
         #$ -l h_rt=01:00:00,h_data=4G
         #$ -pe shared 2

         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         module load python/2.7.15
         module load ica-aroma_py27/0.4.5
         module load fsl
         export PYTHONPATH=/u/project/CCN/apps/ica-aroma_py27/site-packages
         export OMP_NUM_THREADS="$NSLOTS"
         export OPENBLAS_NUM_THREADS="$OMP_NUM_THREADS" MKL_NUM_THREADS="$OMP_NUM_THREADS"
         export MPLBACKEND=Agg
         export MPLCONFIGDIR="$(mktemp -d "${TMPDIR:?}/aroma-mpl.XXXXXX")"
         trap 'rm -r -- "$MPLCONFIGDIR"' EXIT
         ICA_AROMA.py -in /absolute/path/prep/func_mcf_s6.nii.gz \
           -out /absolute/path/results/aroma \
           -mc /absolute/path/prep/func_mcf.par \
           -affmat /absolute/path/prep/example_func2highres.mat \
           -warp /absolute/path/prep/highres2standard_warp.nii.gz \
           -m /absolute/path/prep/mask.nii.gz -tr 2 -den both

      Submit with ``qsub aroma.sge`` after saving the script as ``aroma.sge``.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=ica-aroma
         #SBATCH --time=01:00:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=2
         #SBATCH --output=ica-aroma.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load ica-aroma/0.4.5
         export OMP_NUM_THREADS="$SLURM_CPUS_PER_TASK"
         export OPENBLAS_NUM_THREADS="$OMP_NUM_THREADS" MKL_NUM_THREADS="$OMP_NUM_THREADS"
         export MPLBACKEND=Agg
         export MPLCONFIGDIR="$(mktemp -d "${TMPDIR:?}/aroma-mpl.XXXXXX")"
         trap 'rm -r -- "$MPLCONFIGDIR"' EXIT
         ICA_AROMA.py -in /absolute/path/prep/func_mcf_s6.nii.gz \
           -out /absolute/path/results/aroma \
           -mc /absolute/path/prep/func_mcf.par \
           -affmat /absolute/path/prep/example_func2highres.mat \
           -warp /absolute/path/prep/highres2standard_warp.nii.gz \
           -m /absolute/path/prep/mask.nii.gz -tr 2 -den both

Submit with ``sbatch aroma.sbatch``. To use the older version, change the
module line to ``module load ica-aroma/0.4.1-beta``.

Notes
~~~~~

- Both versions completed the full workflow on two public subjects.
  MELODIC, classification and both denoised outputs passed output checks.
- Version 0.4.5 made a PDF plot. Version 0.4.1-beta deletes its native
  thresholded component map by design; its output checks allowed this.
- Earlier small-input checks failed: 0.4.5 can raise a singular-matrix error
  during plotting; 0.4.1-beta can raise a ``len() of unsized object`` error
  when it finds exactly one motion component. These source issues are not
  fixed. Neither occurred in the public-subject pilot.
- Random sampling can change motion-correlation scores between runs.
  Agreement with lab workflows or SGE results was not tested.
- This is a command-line tool. It has no GUI.
