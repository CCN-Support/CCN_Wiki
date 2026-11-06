.. _hoffman2_freesurfer:

FreeSurfer
==========

1. Use FreeSurfer Apptainer images on Slurm

FreeSurfer's Apptainer images are under

.. code-block:: python

  /u/project/CCN/apps/freesurfer/

.. code-block:: python

  #!/bin/bash
  #SBATCH --job-name=reconall-sub123
  #SBATCH --time=5:00:00
  #SBATCH --mem=48G
  #SBATCH --output=/u/home/b/bruin/jobs/slurm_job.%j.out
  #SBATCH -A pi_ccnadm   ##change this to your own pi_account

  ## load apptainer
  module load apptainer
  
  ## export path for bc
  export APPTAINERENV_APPEND_PATH="/u/project/CCN/apps/bc/1.08.2/bin"

  ##base directory for the data
  BASEDIR="/u/project/mylab/bids"
  
  ## Specify the folder for temporary files FreeSurfer generates. 
  ## Create it if not existing
  WORKDIR="/u/scratch/b/bruin/work"
  if [[ ! -d "$WORKDIR" ]]; then
    mkdir -p $WORKDIR/$USER/$SLURM_JOB_ID
  fi
  export TMPDIR=$WORKDIR

  apptainer exec \
    -B $BASEDIR/sub-123/:/input \
    -B $BASEDIR/derivatives/freesurfer:/output \
    -B /u/project/CCN/apps/freesurfer/rh7/8.0.0-1/.license:/usr/local/freesurfer/8.0.0-1/.license \
    /u/project/CCN/apps/freesurfer/freesurfer_8.0.0.sif \
    recon-all -i /input/anat/sub-123_T1w.nii.gz -s sub-123 -all -sd /output

  ## Optional, just to prevent the job ends less than 5 minutes when error happens
  sleep 300

2. Run Freeview

Freeview currently is only working with Freesurfer module, version 8.2.0. The Apptainer container images have missing libaries and we are still working on it.

.. code-block:: python

  module load freesurfer/8.2.0
  freeview
