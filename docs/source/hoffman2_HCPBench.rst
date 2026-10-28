.. _hoffman2_HCPBench:

HCP
===

.. code-block:: python

  module load hcp

If you are experiencing crashing trying to load hcp (mesa or other related crashing errors) do the following:

.. code-block:: python

  cd ~
  wget https://www.humanconnectome.org/storage/app/media/workbench/workbench-rh_linux64-v1.5.0.zip
  unzip workbench-rh_linux64-v1.5.0.zip
  cd workbench/exe_rh_linux64/
  ./wb_view
