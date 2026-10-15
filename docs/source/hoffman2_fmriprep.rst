Hoffman 2 Software Tools: FMRIprep
==================================

FMRIPrep: A Robust Preprocessing Pipeline for fMRI Data

`Official Website <https://fmriprep.org/en/stable/>`_

`FMRIprep Command Line Usage <https://fmriprep.org/en/stable/usage.html>`_

FMRIprep is provided through Apptainer

.. code-block :: python

  module load apptainer
  apptainer run --cleanenv /u/project/CCN/apps/fmriprep/rh7/25.1.3/fmriprep-25.1.3.sif \
  -w PATH/TO/WORKSPACE \
  --output-spaces SPACE_NAME \
  --fs-license-file /u/project/CCN/apps/freesurfer/rh7/7.2.0/.license \
  PATH/TO/DATA/DIR PATH/TO/OUTPUT/DIR \
  participant --participant-label label

*Note: By default, fmriprep uses "MNI152NLin2009cAsym" space if no SPACE_NAME specified with --output-spaces option
