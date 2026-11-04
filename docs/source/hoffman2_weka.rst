:orphan:

.. _hoffman2_weka:

WEKA
====

Use WEKA on Slurm

Load the module
---------------

The ``weka/3.8`` module provides versions 3.8.1, 3.8.5 and 3.8.7.
Run programs in a Slurm job, not on a login node.

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # See the Grid Engine version table in section 2.1

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         module use /u/project/CCN/apps/modulefiles_rl9
         module load weka/3.8

Each pair shows the old Grid Engine (SGE) way first and the new Slurm way second.

Use ``weka-3.8.1``, ``weka-3.8.5`` or ``weka-3.8.7`` to select a version.

Batch job
---------

Save this script as ``weka.sbatch`` in a writable work folder.
Submit with ``sbatch weka.sbatch``. This example uses the supplied iris data.
Checked on Slurm: this script ran as shown (only the PI account changed).

.. grid:: 1 1 2 2
   :gutter: 1

   .. grid-item-card:: Grid Engine (old)
      :class-card: sge-slurm-card

      .. code-block:: bash

         # See the Grid Engine version table in section 2.1

   .. grid-item-card:: Slurm (new)
      :class-card: sge-slurm-card

      .. code-block:: bash

         #!/bin/bash
         #SBATCH --job-name=weka
         #SBATCH --time=00:15:00
         #SBATCH --mem=2G
         #SBATCH --cpus-per-task=1
         #SBATCH --output=weka-%j.out
         #SBATCH -A pi_ccnadm   ## change this to your own pi account
         module use /u/project/CCN/apps/modulefiles_rl9
         module load weka/3.8
         WEKA_JAVA_HEAP=512m _JAVA_OPTIONS=-Djava.awt.headless=true \
           weka-3.8.7 weka.classifiers.trees.J48 \
             -t /u/project/CCN/apps/runtime-deps/el9-x86_64/weka/3.8.7/data/iris.arff \
             -x 10 -s 1

Request more job memory than the Java heap. Change both the launcher and
input path when you use another version or dataset.

GUI
---

1. Connect to the DCV desktop at ``dcv1.hoffman2.oarc.ucla.edu``.
2. Open a terminal.
3. Request a Slurm shell. Replace ``<your pi account>`` with your account.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # From a NoMachine desktop terminal:
            qrsh -X -l h_rt=2:00:00,h_data=4G -pe shared 2

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            srun --x11 -A <your pi account> -c 2 --mem=8G -t 2:00:00 --pty bash

4. Load the module and open Explorer.

   .. grid:: 1 1 2 2
      :gutter: 1

      .. grid-item-card:: Grid Engine (old)
         :class-card: sge-slurm-card

         .. code-block:: bash

            # See the Grid Engine version table in section 2.1

      .. grid-item-card:: Slurm (new)
         :class-card: sge-slurm-card

         .. code-block:: bash

            module use /u/project/CCN/apps/modulefiles_rl9
            module load weka/3.8
            weka-3.8.7 weka.gui.explorer.Explorer

Checked on Slurm through DCV: these commands ran as shown (only the PI account changed), and the Explorer loaded the iris data.

Notes
-----

All three versions passed a headless J48 check with 10-fold cross-validation
on iris. Each reported 96% correct. Other classifiers, packages and lab
workflows were not tested.

All three versions opened Explorer, displayed iris and closed on DCV.
Input was sent on the desktop display, not through a connected DCV Viewer.
Connected Viewer input and other GUI routes were not tested.
Versions 3.7.10 and 3.6.5 are retired and have no Slurm module.
Access by users outside the tested shared application group was not tested.
