.. _hoffman2_brms:

Hoffman2>Software Tools>brms
============================

Use R library brms in Hoffman

.. code-block:: python

  module load R/4.1.2
  module load gcc/5.3.0
  export R_LIBS='/u/project/CCN/apps/R_libs/rh7/4.1.2'

Start R

.. code-block:: python
  
  R
  >require(rstan)
  >require(brms)

To run a test of brms (load rstan and brms first as above)

.. code-block:: python
  
  >fit1 <- brm(count ~ zAge + zBase * Trt + (1|patient),
  data = epilepsy, family = poisson())
