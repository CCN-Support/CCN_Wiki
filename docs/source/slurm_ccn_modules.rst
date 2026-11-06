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

      Version 6.0.7.23, 6.0.7.15, 6.0.7.4, 6.0.7.1, 6.0.4, 6.0.3, 6.0.1, 6.0.0, 5.0.11 (module); 5.0.9 command line only

      How to use: :ref:`hoffman2_fsl`

   2. FreeSurfer: 

      Version: 8.2.0 (module and image), 8.0.0, 7.4.1, 7.3.2, 6.0.0, 5.3.0 (image)

      How to use FreeSurfer's Apptainer images: :ref:`hoffman2_freesurfer`

   3. AFNI

      Version 26.1.05 (Apptainer image)

   4. ANTs

      Version 2.6.5, 2.5.4 (module)

   5. ASHS

      version 2.5.4, 2.6.5 (module)

   6. CONN

      Version 22.a, 19.b (module; runs in MATLAB R2026a with SPM12 r6906)

      How to use: :ref:`hoffman2_CONN`

   7. FSL_MRS

      Version 2.1.12 (module)

      How to use: :ref:`hoffman2_fslmrs`

   8. GIFT

      Version 4.0c, 4.0b (module)

      How to use: :ref:`hoffman2_gift`

   9. gradunwarp

      Version 1.1.0 (module)

      How to use: :ref:`hoffman2_gradunwarp`

   10. HCP Workbench

      Version 2.2.1, 2.0.1, 1.5.0, 1.3.2, 1.2.3, 1.1.1, 1.0 (module ``hcp``)

      How to use: :ref:`hoffman2_HCPBench`

   11. ICA-AROMA

       Version 0.4.5, 0.4.1-beta (module ``ica-aroma``)

       How to use: :ref:`hoffman2_ica-aroma_py27`

   12. k-Wave

       Version 1.4.1, 1.3 (module ``kwave``; CPU only, the GPU binary does not work yet)

       How to use: :ref:`hoffman2_kwave`

   13. MANGO

       Version 4.1 (module)

       How to use: :ref:`hoffman2_mango`

   14. MRIQC

       Version 24.0.2, 22.0.1, 0.16.1 (module; 22.0.1 tested on human data only)

       How to use: :ref:`hoffman2_mriqc`

   15. openSMILE

       Version 3.0.0 (module)

       How to use: :ref:`hoffman2_OpenSmile`

   16. Osprey

       Version 2.9.6 (module)

       How to use: :ref:`hoffman2_osprey`

   17. RStan

       Version 2.32.7: module ``rstan/2.32.7-R4.1.2`` (with CCN R 4.1.2) or ``rstan/2.32.7`` (with the Hoffman2 R 4.4.1 module)

       How to use: :ref:`hoffman2_Rstan`

   18. SimNIBS

       Version 4.6.0 (module, Apptainer image inside)

       How to use: :ref:`hoffman2_Simnibs`

   19. SPM

       Standalone (no MATLAB license needed): ``spm-standalone/26.10.01`` (default), ``spm-standalone/25.01.02``

       In MATLAB R2026a: ``spm/26.10.01``, ``spm/12-r6906``

       How to use: :ref:`hoffman2_spm`

   20. WEKA

       Version 3.8.1, 3.8.5, 3.8.7 (module ``weka/3.8``; run ``weka-3.8.1``, ``weka-3.8.5`` or ``weka-3.8.7``)

       How to use: :ref:`hoffman2_weka`

    
