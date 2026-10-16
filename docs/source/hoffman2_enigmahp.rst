.. _hoffman2_enigmahp:

ENIGMA HALfpipe
===============

Singularity image for HALfpipe in Hoffman2 is located here:

/u/project/CCN/apps/halfpipe/singularity/

The current version is

.. code-block:: python

  halfpipe_1.1.1.sif

To use it,

.. code-block:: python
  
  module load singularity
  singularity run --no-home --cleanenv --bind /:/ext /u/project/CCN/apps/halfpipe/singularity/halfpipe_1.1.1.sif 

Note: Singularity needs to be run in a work node.

More documents are on its `Github page <https://github.com/HALFpipe/HALFpipe>`_
