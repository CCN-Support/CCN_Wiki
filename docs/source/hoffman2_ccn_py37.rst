.. _hoffman2_ccn_py37:

ccn_py37
========

This is a Conda Virtual environment installed with following modules

.. code-block:: python

  nibabel, nilearn, pydicom, pandas, scikit-learn, scipy

Start a CentOS 7 node

.. code-block:: python

  qrsh –l rh7,h_data=16G,h_rt=4:00:00

Load Anaconda

.. code-block:: python

  module load anaconda3/2020.11                                                         
  source $CONDA_DIR/etc/profile.d/conda.sh

Use ccn_py37

.. code-block:: python

  conda activate /u/project/CCN/apps/conda/rh7/ccn_py37
  
Exit ccn_py37

.. code-block:: python

  conda deactivate
