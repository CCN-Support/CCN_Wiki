.. _slurm_issue:

Known issues on Slurm
======================

1. Matlab
   ^^^^^^^^^^^^^^^^

   Error occurs when starting an interactive mode on DCV, then use "module load matlab" to load matlab module and use "matlab" to start matlab GUI interface. 
   
   Solution:

   At the matlab prompt, input command "restoredefaultpath" 

   Then type in 
     
   .. code-block:: python

     savepath /PATH/TO/pathdef.m
   
