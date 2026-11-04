.. _hoffman2_fslmrs:

FSL_MRS
=======

`Official Website <https://fsl.fmrib.ox.ac.uk/fsl/docs/utilities/fsl_mrs.html>`_

.. code-block:: python

  module load fsl_mrs/2.1.12
  fsl_mrs -h


Use FSL_MRS on Slurm
--------------------

The instructions above describe the older setup.
Use the module folder below for Slurm.

Load the module
~~~~~~~~~~~~~~~

Available version: 2.1.12.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load fsl_mrs/2.1.12

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load fsl_mrs/2.1.12

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Batch job
~~~~~~~~~

Prepare a spectrum, its matching basis set and a water reference.
Replace the input paths below. Use a new output folder.
Save this as ``fsl_mrs_job.sh``, change the PI account, then submit it with
``sbatch fsl_mrs_job.sh``.
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
         #$ -l h_rt=00:10:00,h_data=2G
         #$ -pe shared 1

         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         module load fsl_mrs/2.1.12
         export OPENBLAS_NUM_THREADS=1 OMP_NUM_THREADS=1 MKL_NUM_THREADS=1
         fsl_mrs --data spectrum.txt --basis basis/ --h2o water.txt \
           --output fit_results --algo Newton --report

      Submit the saved script from the terminal:

      .. code-block:: bash

         qsub fsl_mrs_job.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=fsl_mrs_fit
         #SBATCH --time=00:10:00
         #SBATCH --mem=2G
         #SBATCH --cpus-per-task=1
         #SBATCH --output=fsl_mrs_fit.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load fsl_mrs/2.1.12
         export OPENBLAS_NUM_THREADS=1 OMP_NUM_THREADS=1 MKL_NUM_THREADS=1
         fsl_mrs --data spectrum.txt --basis basis/ --h2o water.txt \
           --output fit_results --algo Newton --report

Copy ``fit_results`` to your computer. Open ``report.html`` in a browser.

Notes
~~~~~

Version 2.1.12 passed a single-voxel fit on public challenge data with
22 basis spectra. The CSV output had finite values. The HTML report
opened, and its model plot control worked.
The pilot had no TE or TR values. Its results were relative to total
creatine (Cr+PCr), not absolute concentrations.
Comparison with SGE results, full preprocessing, segmentation, simulation,
MRSI and parallel workers were not tested.
