:orphan:

.. _hoffman2_kwave:

k-Wave
======

Use k-Wave on Slurm

k-Wave is a MATLAB toolbox for acoustic simulation.
This page covers CPU use only.

Load the module
---------------

Available versions: ``1.4.1`` and ``1.3``. Load only one version.
The modules use MATLAB R2026a. The example below uses ``1.3``.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # No k-Wave module; add the 1.3 toolbox in MATLAB.
         matlab -r "addpath('/u/project/CCN/apps/kwave/rh7/1.3/k-Wave')"

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load kwave/1.3

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

For version 1.4.1, use ``module load kwave/1.4.1`` instead.

Batch job
---------

Save this as ``kwave.sbatch`` in a writable run folder.
Replace the account. The example runs a small 3D C++ CPU simulation and
saves ``sensor_data`` in ``kwave-result.mat`` in the submission folder.
No ``BinaryPath`` setting is needed with the Slurm module.
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
         #$ -l h_rt=01:00:00,h_data=3G
         #$ -pe shared 4

         . /u/local/Modules/default/init/modules.sh
         module use /u/project/CCN/apps/modulefiles
         # No k-Wave module; use the toolbox and CCN CPU binary.
         export OMP_NUM_THREADS="$NSLOTS"
         matlab -nodisplay -r "addpath('/u/project/CCN/apps/kwave/rh7/1.3/k-Wave'); \
           dx = 1e-4; \
           kgrid = kWaveGrid(64, dx, 64, dx, 64, dx); \
           kgrid.setTime(151, 0.3*dx/1500); \
           medium.sound_speed = 1500; medium.density = 1000; \
           source.p0 = makeBall(64, 64, 64, 32, 32, 32, 2); \
           sensor.mask = zeros(64, 64, 64); sensor.mask(40, 32, 32) = 1; \
           sensor_data = kspaceFirstOrder3DC(kgrid, medium, source, sensor, \
             'BinaryPath', '/u/project/CCN/apps/kwave/1.3/kspaceFirstOrder-OMP/', \
             'PlotSim', false, 'PMLInside', true, 'PMLSize', 10, 'DataCast', 'single'); \
           save('kwave-result.mat', 'sensor_data'); exit"

      Submit with ``qsub kwave.sge`` after saving the script as ``kwave.sge``.
      The old toolbox needs an explicit path to an executable CPU binary.

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=kwave-cpu
         #SBATCH --time=01:00:00
         #SBATCH --mem=12G
         #SBATCH --cpus-per-task=4
         #SBATCH --output=kwave.%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account

         module use /u/project/CCN/apps/modulefiles_rl9
         module load kwave/1.3
         export OMP_NUM_THREADS="$SLURM_CPUS_PER_TASK"
         matlab -batch "dx = 1e-4; \
           kgrid = kWaveGrid(64, dx, 64, dx, 64, dx); \
           kgrid.setTime(151, 0.3*dx/1500); \
           medium.sound_speed = 1500; medium.density = 1000; \
           source.p0 = makeBall(64, 64, 64, 32, 32, 32, 2); \
           sensor.mask = zeros(64, 64, 64); sensor.mask(40, 32, 32) = 1; \
           sensor_data = kspaceFirstOrder3DC(kgrid, medium, source, sensor, \
             'PlotSim', false, 'PMLInside', true, 'PMLSize', 10, 'DataCast', 'single'); \
           save('kwave-result.mat', 'sensor_data');"

Submit with ``sbatch kwave.sbatch``.
For your own MATLAB script, replace the MATLAB command with
``matlab -batch "my_simulation"``. Keep the script in the submission folder.
For a script that saves figures, use
``ccn-xvfb-run matlab -batch "my_simulation"`` to supply a virtual screen.

Notes
-----

- Both versions passed small 2D and 3D MATLAB CPU checks with
  ``kspaceFirstOrder2D`` and ``kspaceFirstOrder3D``.
- Both passed C++ CPU checks with ``kspaceFirstOrder3DC``. Its sensor data
  matched MATLAB within the tested tolerance. Known arrival-time checks
  also passed. These are small checks, not lab workflow validation.
- Version 1.3 saved a checked batch plot. Its Slurm copy has an upstream
  HDF5 text-format fix for use with newer MATLAB releases.
- Version 1.4.1 passed CPU checks, but its combined acceptance check failed.
  Its saved figure also failed the automated label check. It is not fully
  accepted on the strength of the CPU checks alone.
- The separate CUDA binary does not work on the tested GPU. Do not use it
  for this CPU route. The exact cause is not known.
- k-Wave has no GUI of its own. Live plots are MATLAB figures.
  Scientific agreement with lab results was not tested.
