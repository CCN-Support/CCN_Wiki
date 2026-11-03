.. _slurm_ccn_modules:

CCN Modules on Slurm
==========

1. Temporarily add this new modulefile for CCN modules on Slurm

   .. code-block:: python

     module use /u/project/CCN/apps/modulefiles_rl9

Once the migration is completed and no need of modules on SGE, we will change this path back to the current /u/project/CCN/apps/modulefiles

Even you can see these new installations from the SGE system, you won't be able to run them on SGE. Similarly, even you see the old modules from SGE on Slurm by "module av" command, you can run only the Slurm version on the Slurm platform.
