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
