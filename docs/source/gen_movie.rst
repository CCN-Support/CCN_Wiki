.. _gen_movie.py:

gen_movie.py
============

Purpose
-------
To convert a 3D MRI image in nifti format to a movie.

Setup Environment
-----------------
To use this script, you need to load Anaconda module first and use conda environment ccn_py37.

ccn_py37 contains nibabel which is needed to read nifti files. ffmpeg is also required for this script to run.

.. code-block::
   module load anaconda3
   conda activate /u/project/CCN/apps/conda/rh7/ccn_py37
   module load ffmpeg/5.0.1

If you want to run this script on other Linux machines instead of Hoffman2, make sure you have Python3, Nibabel and ffmpeg installed.

Usage/Help
----------
To see the usage of this script, enter:

.. code-block::
  ./gen_movie.py --help usage: gen_movie.py [-h] -i INPUT [-o OUTDIR] [-b BIN] [-w WIN]

optional arguments:

 -h, --help            show this help message and exit
 -i INPUT, --input INPUT
                       Full path to input nii file
 -o OUTDIR, --outdir OUTDIR
                       Output directory for movie file
 -d DIM, --dim DIM     Create movie with specific dimension, i.e. options: 0 or 1 or 2. defaul: 2
                       0: Sag 1: Cor 2: Axial
 -b BIN, --bin BIN     Number of bins used in histogram. i.e. 100
 -w WIN, --win WIN     Window range. i.e. "0.05 0.995"


Example
-------

.. code-block::
  /u/project/CCN/apps/scripts/gen_movie.py -i /path/to/T1w_brain.nii.gz -o /path/to/output/ --win "0.05 0.995" --bin 100 --dim 2

In this example, the script reads the input file from ``/path/to/T1w_brain.nii.gz`` and creates a "movie" folder under ``/path/to/output/``.

Then, it generates a movie file called mri_movie.mp4 using the input file and saves it under the new ``movie/`` folder.

You will find the final output file at ``/path/to/output/movie/mri_movie.mp4``.

Note that the script also applies a histogram with 100 bins on the MRI data. Data values lower than 0.05 or higher than 0.995 are replaced by windowing method. The window range and numbers of bins can be adjusted with ``--win`` and ``--bin`` options.
