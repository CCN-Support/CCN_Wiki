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
