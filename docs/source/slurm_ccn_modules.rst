.. _slurm_ccn_modules:

CCN Modules on Slurm
==========

1. To use the new CCN module installations for Slurm, temporarily add this new modulefile for CCN modules on Slurm

   .. code-block:: python

     module use /u/project/CCN/apps/modulefiles_rl9

   Once the migration is completed and no need of modules on SGE, we will change this path back to the current /u/project/CCN/apps/modulefiles

   Although you can see these new installations from the SGE system by "module av", you won't be able to run them on SGE. 
   Similarly, even you see the old modules on Slurm, you can run the Slurm versions only on the Slurm platform.

2. Modules ready for Slurm:

   1. FSL

   2. FreeSurfer: 

      How to use FreeSurfer's Apptainer images: :ref:`hoffman2_freesurfer`

   3. AFNI

      Version 26.1.05 (Apptainer image)

   4. ASHS

      version 2.5.4, 2.6.5 (module)
