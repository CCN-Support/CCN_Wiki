.. _hoffman2_DSIStudio:

DSI Studio
==========

Log in via NoMachine

GUI

.. code-block:: python

  module load apptainer
  singularity exec /u/project/CCN/apps/dsistudio/dsistudio_latest.sif dsi_studio


CLI

.. code-block:: python

  singularity exec dsistudio_latest.sif dsi_studio --action=rec --source=my.src.gz # call DSI Studio command line interface in the singularity container
