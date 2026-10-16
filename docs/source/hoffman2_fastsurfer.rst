.. _hoffman2_fastsurfer:

FastSurfer
==========

`Official Website <https://github.com/Deep-MI/FastSurfer/>`_

This current version requires CentOS 7work nodes and conda environment.

.. code-block:: python

  module load anaconda3/2020.11
  . /u/local/apps/anaconda3/2020.11/etc/profile.d/conda.sh

Use it with GPU node

.. code-block:: python

  conda activate /u/project/CCN/apps/fastsurfer/202102_gpu

Use it with regular CPU only node

.. code-block:: python

  conda activate /u/project/CCN/apps/fastsurfer/202102_cpu

FastSurfer code is under

.. code-block:: python

 cd /u/project/CCN/apps/fastsurfer/202102/FastSurfer

To check the usage

.. code-block:: python

  ./run_fastsurfer.sh -h

Once you finish using it, exit the conda virtual environment by

.. code-block:: python

  conda deactivate
