.. _hoffman2_profumo:

Profumo
=======

This module is provided with Singularity.

Since Singularity requires CentOS 7, the following command lines should be run on a CentOS 7 node.

.. code-block:: python

  module load singularity
  singularity shell --userns /u/project/CCN/apps/profumo/0.11.3/profumo.sif
  exit. ##to stop container
