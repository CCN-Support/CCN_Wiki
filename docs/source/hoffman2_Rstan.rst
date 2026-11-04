.. _hoffman2_Rstan:

Rstan
=====

To use Rstan, we need to load R version/4.1.2

.. code-block:: python

  module load R/4.1.2
  module load gcc/5.3.0
  export R_LIBS='/u/project/CCN/apps/R_libs/rh7/4.1.2'

Enter R prompt and test Rstan

.. code-block:: python

  R
  >require(rstan)
  > example(stan_model, package = "rstan", run.dontrun = TRUE)


Use RStan on Slurm
------------------

The old 4.1.2 label refers to R, not RStan. Do not use the EL7 package
library above on Slurm.

Load the module
~~~~~~~~~~~~~~~

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Both choices provide RStan 2.32.7. The module loads the matching R version.
For the native EL9 rebuild of CCN R 4.1.2:

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles
         module load R/4.1.2
         module load gcc/5.3.0
         export R_LIBS='/u/project/CCN/apps/R_libs/rh7/4.1.2'

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module purge
         module use /u/project/CCN/apps/modulefiles_rl9
         module load rstan/2.32.7-R4.1.2

For Hoffman2 site ``R/4.4.1``:

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # The old RStan route used R 4.1.2.
         module use /u/project/CCN/apps/modulefiles
         module load R/4.1.2
         module load gcc/5.3.0
         export R_LIBS='/u/project/CCN/apps/R_libs/rh7/4.1.2'

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module purge
         module use /u/project/CCN/apps/modulefiles_rl9
         module load rstan/2.32.7

Batch job
~~~~~~~~~

Put ``model.stan`` and its R data list, ``data.rds``, in a new writable
folder. Save this as ``rstan.sbatch`` there. Submit with ``sbatch rstan.sbatch``.
This example uses site R 4.4.1. Adjust resources for your model.
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
         #$ -l h_rt=01:00:00,h_data=2G
         #$ -pe shared 4

         . /u/local/Modules/default/init/modules.sh
         set -euo pipefail
         module use /u/project/CCN/apps/modulefiles
         module load R/4.1.2
         module load gcc/5.3.0
         export R_LIBS='/u/project/CCN/apps/R_libs/rh7/4.1.2'
         export OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 MKL_NUM_THREADS=1 TBB_NUM_THREADS=1
         export RSTAN_CORES="$NSLOTS"
         Rscript --vanilla - <<'RS'
         library(rstan)
         cores <- as.integer(Sys.getenv("RSTAN_CORES"))
         fit <- stan(file="model.stan", data=readRDS("data.rds"),
                     chains=cores, cores=cores, iter=4000, warmup=1000, seed=20261015)
         saveRDS(fit, "fit.rds")
         RS

      Submit the saved script:

      .. code-block:: bash

         qsub rstan.sh

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=rstan
         #SBATCH --time=01:00:00
         #SBATCH --mem=8G
         #SBATCH --cpus-per-task=4
         #SBATCH --output=rstan-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         set -euo pipefail
         module purge
         module use /u/project/CCN/apps/modulefiles_rl9
         module load rstan/2.32.7
         empty_lib="$(mktemp -d /tmp/rstan-user.XXXXXXXX)"
         trap 'rmdir "$empty_lib"' EXIT
         export R_LIBS_USER="$empty_lib"
         export R_MAKEVARS_USER=/dev/null
         export OMP_NUM_THREADS=1 OPENBLAS_NUM_THREADS=1 MKL_NUM_THREADS=1 TBB_NUM_THREADS=1
         export RSTAN_CORES="$SLURM_CPUS_PER_TASK"
         Rscript --vanilla - <<'RS'
         library(rstan)
         cores <- as.integer(Sys.getenv("RSTAN_CORES"))
         fit <- stan(file="model.stan", data=readRDS("data.rds"),
                     chains=cores, cores=cores, iter=4000, warmup=1000, seed=20261015)
         saveRDS(fit, "fit.rds")
         RS
         module unload rstan/2.32.7

Notes
~~~~~

* Both R routes compiled and sampled two small models with known answers.
  Four chains used four CPUs. Module unload restored environment settings.
* The site-R batch recipe saved a fit that could be read back. Its mean and
  chain agreement passed the checks. This does not validate other models.
* The empty personal library prevents personal packages from replacing
  the shared set. Reinstall personal EL7-built packages from source under
  the new R. Keep them separate from the shared RStan packages.
* Real lab model comparisons and access by another intended user were not
  tested. RStudio and GUI use were not tested.
