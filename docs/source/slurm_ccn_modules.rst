.. _slurm_ccn_modules:

CCN Modules on Slurm
==========

1. Temporarily add this new modulefile for CCN modules on Slurm

   .. code-block:: python

     module use /u/project/CCN/apps/modulefiles_rl9

   Once the migration is completed and no need of modules on SGE, we will change this path back to the current /u/project/CCN/apps/modulefiles

   Although you can see these new installations from the SGE system by "module av", you won't be able to run them on SGE. 
   Similarly, even you see the old modules on Slurm, you can run the Slurm versions only on the Slurm platform.
