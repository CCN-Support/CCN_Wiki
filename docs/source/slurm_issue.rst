.. _slurm_issue:

Known issues on Slurm
======================

1. Matlab
   ^^^^^^^^^^^^^^^^

   Error occurs when starting an interactive mode on DCV, then use "module load matlab" to load matlab module and use "matlab" to start matlab GUI interface. 
   
   Solution:

   At the matlab prompt, input command 

   .. code-block:: python

     restoredefaultpath 

   Then type in 
     
   .. code-block:: python

     savepath /PATH/TO/pathdef.m
   
2. Version of Modules provided by IDRE team
   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

   a) Matlab currently has only version R2026a.
      
      We have requested IDRE team for R2020a. Please let us know if your lab needs different Matlab version. 

   b) Python has only version 3.10.20 and 3.12.13. Some old applications use Python2 which can be a problem. We provide Python2 from CCN modules now. To use it,

      .. code-block:: python

        module load python/2.7.18
