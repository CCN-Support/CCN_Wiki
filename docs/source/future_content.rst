Future Content
--------------

Hoffman 2 Introduction
======================

1.2 Hoffman2: Getting an Account
~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Requesting Hoffman2 Account**

What You Need: A UCLA Logon ID, available for free to any UCLA staff, student, or faculty member. If you do not have a UCLA Logon ID, head to the `UCLA Logon services page <https://accounts.iam.ucla.edu/#/>`_. Click on "Create UCLA Logon ID".

**Applying for the Account**

ATTENTION: If you are a PI interested in Hoffman2, please see the section **Becoming a Faculty Sponsor** below.

1. Navigate to the `Requesting an account page <https://www.hoffman2.idre.ucla.edu/Accounts/Requesting-an-account.html>`_.
2. Read over the application summary.
3. Click "New User Registration".
4. Log in using your UCLA Logon ID and password.
5. Fill out the form with appropriate information. For Hoffman2, your Faculty Sponsor should be Mark Cohen, Alison Burggren (for Susan Bookheimer's lab), or your respective PI if they are a Faculty Sponsor on Hoffman.

**Proposed UserName**
  This will be the username you use to sign into the cluster with.

**Select a Resource**

For the Mark Cohen/Susan Bookheimer labs, choose "Hoffman2". However, you can request access to any cluster that is a member of the Grid Portal.

Click Submit. You will receive an email with a link to a temporary password. **PLEASE WRITE IT DOWN.** The link expires after 72 hours. If you missed the link or it expired, go back to the `Application Page <https://www.hoffman2.idre.ucla.edu/Accounts/Users-managing-your-account.html#password-processes>`_ and click Forgot Your Cluster Password? It will take about a day for the cluster to resend you a new password.

You can change your password once you've logged in by using passwd.

**Becoming A Faculty Sponsor**

If you are a PI or Lab Manager interested in the Hoffman2 Cluster, you will want to create a Faculty Sponsor account first. Also, if you are a member of another lab collaborating with the Cohen or Bookheimer labs, you may want to forward this information to your PI or Lab Manager. Faculty Sponsors can approve (or deny) applications for membership to their group. They also receive a group folder and a unique group id so their users can work and share data easily with each other.

1. Navigate to the `register as a sponsor page <https://www.hoffman2.idre.ucla.edu/Accounts/Requesting-an-account.html#register-as-a-sponsor>`_.
2. Click "New Sponsor Registration" (on the bottom of the page).
3. Log in using your UCLA Logon ID and password.
4. Fill out the form with appropriate information.

Under 'Reason', any reason is appropriate for faculty members. For example: "To perform fMRI analysis."

**Hoffman2:Accessing the Cluster**

SSH - Command Line

SSH stands for Secure Shell and is a method of remotely logging into a computer using an encrypted connection. It is a command-line tool and is available on most *nix-based operating systems with ports available for Windows.

**Mac/Linux/Unix**

Simple SSH

Use the ssh command from a terminal:

.. code-block:: python

  ssh login_id@hoffman2.idre.ucla.edu

where login_id is replaced by your cluster user name.

**GUI-Enabled SSH**

Macs (post - Snow Leopard 10.6.x) no longer come with an X Window System Server pre-installed.

Before doing the following steps, please install `XQuartz <http://xquartz.macosforge.org/>`_ and restart your computer. Note: From Xquartz 2.7.9, indirect GLX is disabled by default, so you'll need to run this command followed by a reboot

.. code-block:: python

  ssh login_id@hoffman2.idre.ucla.edu

For M-series Macs use the following instead with XQuartz 2.8.2:

.. code-block:: python

  defaults write org.xquartz.X11 enable_iglx -bool true

1. Open up your Terminal. It's under Applications > Utilities on Macs.
2. Type the command,

.. code-block:: python

  $ ssh -Y login_id@hoffman2.idre.ucla.edu

replacing login_id with your Hoffman2 username.
The -Y is for X11 Forwarding so that any graphics that are rendered on Hoffman2 get forwarded to the screen of your computer.

3. Press enter and type in your password when it asks for it. No characters or asterisks will show up while you type.
4. Provided your typing was good, you will be greeted by the Hoffman2 login message and have successfully SSH into a login node.

**Windows**

1. Go `here <https://www.hoffman2.idre.ucla.edu/Using-H2/Connecting/Connecting.html>`_ and follow the instructions under Windows. We recommend PuTTY or Cgywin.
2. If you use putty, please install `xming <http://sourceforge.net/projects/xming/>`_ for GUI access.
Once you have that setup, the process is the same as if you were on a Mac or Linux/Unix machine

**Remote Desktop [Recommended]**

Currently, Hoffman supports connecting to the cluster via the X2Go client and the NoMachine client.

**NX Client - GUI**

The NX Client program allows you to set up a Virtual Network Computing (VNC)-like session with Hoffman2. This session will keep running even if your Internet connection drops in and out (much like `screen <https://www.ccn.ucla.edu/wiki/index.php/Using_Screen>`_ on the command line).

**X2Go - GUI**

X2Go provides a desktop-like GUI for accessing the Hoffman server. Please see here to find out more about setup details.



Change Passwords
Once you've logged on and made sure its works, you can change your password to something more rememberable To change passwords, logon and type:

.. code-block:: python

  passwd

It should ask you for your old password and then new ones.

1.4 Working in a Linux Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Hoffman2: Linux Tutorial**

A tutorial from Hoffman2 support

`Here <https://www.hoffman2.idre.ucla.edu/Using-H2/Command-line/Unix-command-line.html>`_ is a simple tutorial from Hoffman2's support page

**Permissions**

Permissions determine who and to what degree users can access a file.

The key terminology and function of the permission system is found here:

[insert unix permissions page]

**List of Utilities Covered**

- ls
- chmod (man chmod)
- Exhaustive tutorial including min-quizzes CatCode Tutorial
- chgrp
- umask
- newgrp

File System Navigation
~~~~~~~~~~~~~~~~~~~~~~

The following series of tutorials provide a very basic introduction to file system navigation on unix like systems without any assumptions of prior knowledge on the topics.

- Listing files & directories, making directories, changing directories, the . and .. directories, pathnames, the "home" directories
    - `Tutorial One <http://www.ee.surrey.ac.uk/Teaching/Unix/unix1.html>`_

-Copying files, moving files, removing files and directories, displaying the contents of a file, searching the contents of a file
    - `Tutorial Two <http://www.ee.surrey.ac.uk/Teaching/Unix/unix2.html>`_

List of Utilities Covered
~~~~~~~~~~~~~~~~~~~~~~~~~

- ls
- mkdir
- cd
- pwd
- cp
- mv
- rm
- cat
- less
- head & tail
- grep

File & Shell Management
~~~~~~~~~~~~~~~~~~~~~~~

This is where your career on a UNIX type system can be made or crippled. Sure you know how to move around, list files, find out where you are, and display the contents of files. But now you have to do something with those files. And let's face it, there are a whole lot of files.

It is **highly recommended** that the reader look over `Tutorial Four <http://www.ee.surrey.ac.uk/Teaching/Unix/unix4.html>`_ on how to use wildcards for matching before preceding with this section.

The good news is, using the above utilities we just learned about we can accomplish almost anything we want to do using a very handy utility called find.

As the name might imply, find, well, finds things. What it finds is up to you. find has many, many options. All laid out in its man page. However, for most purposes only a few are needed. We'll cover those here.

A basic find command looks like

.. code-block:: python

  $ find /path/to/directory -name 'filename.txt'

This command looks at all files in /path/to/directory and in all directories therein for a file named 'filename.txt'.

**Common Options**

-type
    Specifies the type of file we're looking for. e.g. text file, directory, link, etc.
-name
    Specifies the name of the file. Case Sensitive
-iname
    Specifies the name of the file. Case Insensitive
-or
    Joins the precedeing and following terms by the boolean OR
-and
    Joins the preceding and following terms by the boolean AND
-not
    negates the next term. e.g. -not -empty means "is not empty"
-exec
    excutes a shell command for each file found. The only 'trick' is to replace the actual file name with {} and end the command with a \;. This should become clear when reviewing the examples below.
-empty
    The file or directory is empty.


We can combine the above options to preform complex searches on the file system and, even better, execute commands on those search terms. For a list of all options and their arguments, please see `Find Man Page <http://unixhelp.ed.ac.uk/CGI/man-cgi?find>`_.

**Examples**

Find all directories named 'tsplot' in the current directory

.. code-block:: python

  $ find . -name tsplot -type d 

Find all empty directories in the directory /u/home9/foo/data

.. code-block:: python

 $ find /u/home9/foo/data -empty 

Find all empty files or directories named 'tsplot' in the current directory

.. code-block:: python

 $ find . -name tsplot -or -type d -empty 

Using commands we've already learned to perform actions on the above.

Find all files named design.fsf and look for a subject named 'foo'

.. code-block:: python

 $ find . -name design.fsf -type f -exec grep "foo" {} \; 

With a little reading of the man page, we find a new option called -user, which finds all files that belong to the specified user

Find all files owned by user 'foo' and change their permissions

.. code-block:: python

 $ find . -type f -user foo -exec chmod -R ug+rwX {} \; 

Environment Variables
~~~~~~~~~~~~~~~~~~~~~

UNIX uses environment variables to pass information to various tools during a session. These variables are named in all capitals by convention. You can see all of the environment variables and their values by using the command

.. code-block:: python

  $ env

To simply see the value of one variable, you can echo its value

.. code-block:: python

  $ echo $VARIABLENAME

There are a few environment variables that you should be familiar with...

**USER**

This has the username of the current user, which should usually be you. See what the value is

.. code-block:: python

  $ echo $USER


**HOME**

This is the path to the home directory of the current user. The tilde symbol (~) is also recognized as shorthand for this home directory.

.. code-block:: python

  $ echo $HOME

**PATH**

This is a list of directories, separated by colons, in which the operating system should check for commands that you type. For instance, when you were using the ls, grep, or find commands in previous tutorials, the operating system started looking through the directories in your PATH variable to find the first command that matched that name and tried executing it. See the directories that the operating system will check for you by typing

.. code-block:: python
  $ echo $PATH

Making additions to this variable can be important. Let's say you have a personal set of scripts you have created and you store them in a directory ~/scripts. Every time you want to use one of those scripts, you have to type out the full path to it

.. code-block:: python
 
  $ ~/scripts/my-first-script.sh

or

.. code-block:: python

  $ $HOME/scripts/my-first-script.sh

This can get tiring. If you added your scripts directory to your path, you wouldn't have to type that extra bit every time. The best way to do this would be to edit your Bash Profile with a text editor. e.g.

.. code-block:: python
  
  $ vim ~/.bash_profile

and add the line

.. code-block:: python

  export PATH=$PATH:~/scripts

to the end of the file and saved it. This will "export" the variable named PATH to the environment and set its value equal to whatever was already in PATH plus the directory ~/scripts. The next time you login, you can do

.. code-block:: python

  $ echo $PATH

and see that at the end of the list of directories to search, your directory ~/scripts has been added. Now you can be anywhere in the filesystem and call the command

.. code-block:: python

  $ my-first-script.sh

to run that same script from before.

**Collisions on the PATH**

If you get in the habit of naming your scripts the same thing (e.g. my-script.sh) and placing them in different directories, you may run into a collision on your PATH. This is a case where you think you are running one script, but the operating system is actually running another. Let's look at an example.

Continuing from the previous example where we have the script ~/scripts/my-first-script.sh, let's say that we make another directory called analyze and we are working with some data there and make a processing script coincidentally called my-first-script.sh. So we have the files

.. code-block:: python

  ~/scripts/my-first-script.sh
  ~/analyze/my-first-script.sh
  ~/analyze/data-file-1
  ~/analyze/data-file-2
  ...

And we have amended our .bash_profile so that ~/scripts is at the end of our PATH environment variable.

If we change to the analyze directory

.. code-block:: python

  $ cd ~/analyze

and wish to run the processing script my-first-script.sh on the data, you may think we can execute

.. code-block:: python

  $ my-first-script.sh

and call it a day. But this will actually run the file ``~/scripts/my-first-script.sh`` because it is the first file the operating system found in the directories of PATH that matched that name. If you wanted to verify this, you can execute

.. code-block:: python

  $ which my-first-script.sh

This command will search your PATH variable for the first instance of my-first-script.sh and return the full path to it, something like this

.. code-block:: python

  ~/scripts/my-first-script.sh

To run the script we had intended, we would need to execute

.. code-block:: python

  $ ./my-first-script.sh

The period and slash specify that the operating system should look in the current directory for this script.

If something seems weird or script isn't working, a good starting point is to check that you are running the script you think you are. Use which to find out

**Man Pages**

The man pages (for manual) are the be all end all reference on UNIX systems.

A `Beginners Guide to man Pages <http://www.tfug.org/helpdesk/general/man.html>`_ is an excellent introduction into how to move around a man page easily and understand what it's telling you.

Computing
---------

2.1 Software Tools
~~~~~~~~~~~~~~~~~~

There is a CCN usergroup on Hoffman2 which is maintained for groups doing Neuroimaging work at UCLA. Tools like FSL, FreeSurfer, AFNI and Nibabel are maintained for this group separate from normal Hoffman2 programs. In order to take advantage of these tools, you need to load the modules into the interactive mode or listed in your batch mode scripts.

.. code-block:: python

  module load appname/version

Below is a list of the available software tools. We will do our best to update it as changes are made.

  - Do not load matlab and freesurfer or matlab and RStudio as it will cause errors.

ANFI
~~~~

`Official Website <http://afni.nimh.nih.gov/afni/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 20.1.00
     - 
     - New
   * - 19.0.15
     - 2019.02.20
     - 
   * - 17.2.07
     - 2017.02.07
     - Default
   * - 16.3.1
     - 2016.11.20
     - 
   * - 2011.12.21.1014
     - 2012.03.19
     - 

**ANTS**

`Official Website <http://stnava.github.io/ANTs/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - ants-2.3.1
     - 
     - New
   * - ants-2.2.0
     - 2019.03.25
     - 
   * - ants-2.1.0-redhat
     - 2015.01.23
     - Default

**ASHS**

`Official Website <https://www.nitrc.org/projects/ashs%7C>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 20180720
     - 2018.07.20
     - New
   * - 2017-02
     - 2017.06.08
     - 
   * - Rev-103
     - 2016.02.24
     - Default

**Brainsuite**

`Official Website <http://brainsuite.org/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 20180720
     - 2018.07.20
     - New
   * - 2017-02
     - 2017.06.08
     - 
   * - Rev-103
     - 2016.02.24
     - Default

**BrainAgeR**

`Official Website <https://github.com/james-cole/brainageR>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 19a
     - 2019.02.19
     - Default
   * - 18a
     - 
     - 
   * - 17a
     - 
     - 
   * - 15c
     - 
     - No longer supported

**brms**

R Library `Official Website <http://https//mc-stan.org/users/interfaces/brms>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 2.17.0
     - 2022.06.10
     - Default

**Caret**

`Official Website <http://brainvis.wustl.edu/wiki/index.php/Caret:About>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 5.65 (2012.01.27)
     - 2013.07.15
     - Default, not folded into the main profile

**ccn_py37**

Conda virtual environment with nibabel, nilearn, pydicom, pandas, scikit-learn, scipy

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 1.0
     - 2021.05.24
     - CentOS 7 with Conda

**Chronux**

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 2.1
     - 2013.02.26
     - Current

**CONN**

`Official Website <https://web.conn-toolbox.org/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 19.b
     - 2013.02.26
     - New
   * - 18.b
     - 
     - 
   * - 17.f
     - 
     - Default

**dcm2nii**

`Official Website <http://www.mccauslandcenter.sc.edu/mricro/mricron/dcm2nii.html>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 2013.06.06
     - 2014.03.06
     - 
   * - 2011.11.11
     - circa 2011
     - Current

**dmctk**

`Official Website <https://dicom.offis.de/dcmtk.php.en>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 3.6.0
     - 2017.05.17
     - Current
   * - 3.6.6
     - 2021.02.16
     - 

**DTIprep**

`Official Website <https://www.nitrc.org/projects/dtiprep/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 1.2.4
     - 2017.12.21
     - 
   * - 1.2.9
     - 2018.03.20
     - Current

**DSI Studio**

`Official Website <https://dsi-studio.labsolver.org/>`_

**Please note DSI studio only works with NoMachine**

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - "Chen" Release
     - 2023.07.06
     - Current

**dmriprep**

`Official Website: <https://github.com/nipreps/dmriprep>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 0.4.0
     - 2020.12.10
     - Current

**EEGLAB**

`Official Website <http://sccn.ucsd.edu/eeglab/>`_

`Release Notes <http://sccn.ucsd.edu/wiki/EEGLAB_revision_history>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 13.1.1b
     - 2014.01.29
     - 
   * - 12.0.2.5b
     - 2013.11.14
     - 
   * - 11.0.5.4b
     - 2013.11.14
     - 
   * - 12.0.0.0b
     - 2012.12.10
     - 
   * - 11.0.0.0b
     - 2012.02.21
     - 
   * - 10.2.5.8b
     - 2012.02.21
     - 

**ENIGMA**

`Official Website <https://www.nitrc.org/projects/dtiprep/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 20210422
     - 2021.04.22
     - Current

**ENIGMA HALFpipe**

`Official Website <https://github.com/HALFpipe/HALFpipe>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 1.1.1
     - 2021.08.27
     - Current

**FastSurfer**

`Official Website <https://github.com/Deep-MI/FastSurfer/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 202102
     - 2021.03.01
     - Current

**FIT**

`Official Website <https://trendscenter.org/software/fit/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - FITv2.0d
     - 2021.03.01
     - 
   * - FITv2.0e
     - 2021.01.13
     - 

**FIX**

`Official Website <https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/FIX/UserGuide>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 1.06.15
     - 2021.12.01
     - 

**FMRIprep**

`Official Website <https://fmriprep.readthedocs.io/en/stable/usage.html>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 25.1.3
     - 2025.07.27
     - In Apptainer
   * - 24.1.1
     - 2024.11.01
     - In Apptainer 
   * - 23.2.0
     - 2024.03.12
     - In Apptainer 
   * - 23.1.3
     - 2023.08.22
     - Use Apptainer module
   * - 20.2.1
     - 2021.05.13
     - In Singularity
   * - 20.2.0rc0
     - 
     -  
   * - 20.1.1
     - 
     - * known Issue
   * - 1.4.0
     - 2019.01.11
     - Default * known Issue
   * - 1.3.2
     - 2019.01.11
     - * known Issue

**Free Surfer**

`Official Website <http://surfer.nmr.mgh.harvard.edu/>`_

`Release Notes <http://freesurfer.net/fswiki/ReleaseNotes>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 7.2.0
     - 2021.11.29
     - 
   * - 7.1.1
     - 2021.02.26
     -  
   * - 6.0.0
     - 2017.01.18
     - CentOS 6 only

**FSL**

`Official Website <http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/>`_

`Revision History <http://fsl.fmrib.ox.ac.uk/fsl/fslwiki/WhatsNew>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 6.0.4
     - 2021.01.25
     - new
   * - 6.0.3
     - 2021.09.30
     - 
   * - 6.0.1
     - 2019.03.01
     - 
   * - 6.0.0
     - 2018.10.23
     - 
   * - 5.0.11
     - 2018.03.19
     - 
   * - 5.0.10
     - 2017.04.24
     -  * Known Issue
   * - 5.0.9
     - 2015.10.02
     - Default
   * - 5.0.8
     - 2014.12.03
     - 
   * - 5.0.7
     - 2013.10.17
     - 
   * - 5.0.6
     - 2013.12.18
     - (2013.12.18-2014.10.10)
   * - 4.1.9
     - 2011.12.01
     - 
   * - 4.0.4
     - circa 2008
     - 

Known issue: 5.0.10 fsleyes crash on x2go

**FSL_MRS**

`Official Website <https://open.win.ox.ac.uk/pages/fsl/fsl_mrs/index.html#>`_

`Revision History <https://open.win.ox.ac.uk/pages/fsl/fsl_mrs/changelog.html>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 2.1.12
     - 2023.08.22
     - new

**ggseg**

`Official Website <https://github.com/ggseg/ggseg>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - v1.6.5.9000
     - 2023.03.1
     - 

*Note: ggsegExtra and ggseg3d are also available under these libraries

**gift**

`Official Website <https://trendscenter.org/software/gift/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - GroupICATv4.0b
     - 2017.11.14
     -  
   * - GroupICATv4.0c
     - 2021.01.04
     - 

**gradunwarp**

`Official Website <https://github.com/Washington-University/gradunwarp>`_

.. list-table::
   :header-rows: 1

  *  - Version
     - Install Date
     - Notes
   * - 1.1.0
     - 2019.06.04
     -  

**HCP Benchwork**

`Official Website <https://www.humanconnectome.org/software/connectome-workbench>`_

- Note: module name: hcp

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 1.3.2
     - 2019.05.22
     - New
   * - 1.2.3
     - 2018.02.13
     - 
   * - 1.1.1
     - 2016.02.18
     - Default
   * - 1.0
     - 
     - 
   * - 0.84
     - 
     - 

**ICA-AROMA**

- Note: Python 2.7 available for v0.4.5, module name: ica-aroma_py27

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 0.4.5
     - 
     - New
   * - 0.4.1-beta
     - 
     - Default

**ITK Gray**

`Official Website <http://vistalab.stanford.edu/newlm/index.php/ItkGray>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 080803
     - 2009.11.19
     - Default
   * - 080128
     - 2009.11.13
     - 

**ITKSnap**

`Official Website <http://www.itksnap.org/pmwiki/pmwiki.php>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 3.4.0.QT4
     - 2016.02.24
     - Default
   * - 3.6.0.QT4
     - 2021.03.02
     - 
   * - 3.8.0.QT4
     - 2021.03.02
     - Default

**kwave**

`Official Website <http://www.k-wave.org/doxygen/index.html>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 1.3
     - 2020.07.20
     - Current

**MANGO**

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 20190905
     - 
     - Current

**MRIQC**

`Official Website <https://mriqc.readthedocs.io/en/latest/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 0.16.1
     - 2021.03.08
     - Current

**NDATools**

`Official Website <https://github.com/NDAR/nda-tools>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 0.2.3
     - 2021.03.04
     - Current

**OpenSmile**

`Official Website <https://www.audeering.com/opensmile/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 3.0.0
     - 2021.03.23
     - Current

**Osprey**

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 2.9.6
     - 2025.03.13
     - Current

**Profumo**

`Official Website <https://git.fmrib.ox.ac.uk/samh/profumo>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 0.11.3
     - 2021.06.22
     - Current

**RATS**

`Official Website <https://www.iibi.uiowa.edu/rats-rodent-brain-mri/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 060419
     - 2019.06.04
     - Current

**Simnibs**

`Official Website <https://simnibs.github.io/simnibs/build/html/installation/simnibs_installer.html/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 060419
     - 2019.06.04
     - Current

**RStan**

`Official Website <https://mc-stan.org/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 4.1.2
     - 2022.04.11
     - Current

**SPM**

`Official Website <http://www.fil.ion.ucl.ac.uk/spm/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Last Patch Applied
     - Last Checked Date
     - Notes
   * - SPM12-standalone
     - 
     -
     - Current
   * - SPM12
     - 
     -
     - 
   * - SPM8
     - 5236
     - 2014.01
     - 
   * - SPM5
     - Unknown
     - N/A
     - No longer supported

**TrackVis/Diffusion Toolkit**

`Official Website 1 <http://trackvis.org/>`_
`Official Website 2 <http://trackvis.org/dtk/>`_

.. list-table::
   :header-rows: 1

   * - Tool
     - Version Number
     - Last Checked Date
     - Notes
   * - TrackVis
     - 0.5.2.2
     - 2014.03.06
     - 
   * - Diffusion Toolkit
     - 0.6.2.2
     - 204.03.06
     - 

**WEKA**

`Official Website <http://www.cs.waikato.ac.nz/ml/weka/>`_

.. list-table::
   :header-rows: 1

   * - Version
     - Install Date
     - Notes
   * - 3.8.1
     - 
     - 
   * - 3.7.10
     - 2014.03.03
     - 
   * - 3.6.5
     - circa 2011.08
     - 

2.2 Run Your Jobs
-----------------

**2.2.1 Hoffman 2: Interactive Sessions**
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Interactive sessions on Hoffman2 let you have access to a computing node for up to 24 hours. This is ideal for:

- running a intensive program like MATLAB (in fact that's how it works), WEKA, R or FSLView
- debugging a script you will be submitting to the queue later
- moving/tar'ing/untar'ing lots of files
- any other computing or graphics intensive operations since you aren't supposed to use the login nodes for such heavy lifting.

**Basic Command**

To get one, just use the ``qrsh`` command.

For example:

.. code-block:: python

  $ qrsh 

will try to get you an interactive node with 1 core 1 GB memory, for two hours.

If you successfully get a node, your prompt will change from something like

.. code-block:: python

  [joebruin@login4 ~] $

to something like

.. code-block:: python

  [joebruin@n1234 ~] $

indicating you are on node 1234.

**Longer Time**

If you wanted to specify a a time limit for your interactive session (anything less than 24 hours), use the resource flag again and specify time in the HH:MM:SS format.

For example:

.. code-block:: python

  $ qrsh -l h_rt=4:00:00

will try securing an interactive node for four hours with the default amount of RAM, but if they are all taken you will be kindly told you are out of luck.

**Use highp for 24+ hours job**

If you need to run a very long job over 24 hours, and you are a CCN member, you can use "highp" flag to choose CCN dedicated nodes.

.. code-block:: python

  $ qrsh -l h_rt=48:00:00,highp

will reserve an interactive job for 48 hours in CCN's dedicated nodes (without "highp", the job will never start). Since CCN has limited nodes (12 for now), the waiting time for getting the resource might take some time when the nodes are all busy. It may take less time to start a job which requires less than 24 hour in the regular Hoffman pool. So please use highp for jobs longer than 24 hours only.

**More memory**

Doing something memory intensive? Like working with a lot of visualizations or multiple datasets? Use the resource flag again and specify a data request.

For example

.. code-block:: python

  $ qrsh -l h_rt=4:00:00,h_data=4G

will try securing an interactive node for four hours with four gigabytes of RAM, but if no such node is available the cluster will deny your request.

.. code-block:: python

  $ qrsh -l h_rt=48:00:00,highp,h_data=4G

specify memory usage with highp

**More computing power**

You can add more processor cores to power up your computing intensive jobs

.. code-block:: python

  $ qrsh -l h_rt=4:00:00,h_data=4G -pe shared 2

This will reserve 2 processor cores for the interactive mode session. Be aware that the memory reserved here will be 2 x 4G = 8G.

**Request node with specific processor architect**

You can choose processor architect, for example request a work node with intel chip only

.. code-block:: python

  $ qrsh -l arch=intel*,h_rt=4:00:00,h_data=8G 

**Tips**

Sometimes inactivity on your computer will result in Hoffman2 connection break [ Broken Pipe ] (even while computing).

To prevent this from happening: For Macs - in your /etc/ssh/ssh_config -add this line to the bottom

.. code-block:: python

  ServerAliveInterval 180

This will tell your ssh to ping the server every 180 seconds to prevent it from timing out.

**2.2.2 Hoffman2: Batch Mode**
^^^^^^^^^^^^^^^^^^^^^^^^

Here we show how you can submit your job with batch mode.

To use a batch job, you need to create a batch file with bash or tcsh. This file should have three parts:

- Part 1: List all the resources you want to reserve for your job
- Part 2: Load your modules, export the Linux environment that is needed for your script to run
- Part 3: Call your job script

Once you have your batch file, you can submit it using the qsub command. For example (if your batch file is named as myjob.sh)

.. code-block:: python

  qsub myjob.sh

**Job Submission Templates**

Here are some batch file templates you can start with: Job Submission Templates [insert link]

**Part 1: Request Computing Resource**

This example is based on code from the Submit Job template.

The first part of the batch script file should let the Hoffman job scheduler know what resources you want to reserve for your job:

.. code-block:: python

  #!/bin/bash
  #$ -cwd
  #$ -o joblog.$JOB_ID
  #$ -j y
  #$ -pe shared 2
  #$ -l h_rt=8:00:00,h_data=4G
  #$ -M $USER@mail
  #$ -m bea

Here's the meaning of each line:

.. code-block:: python

  #$ -cwd

Use the current directory for the job

.. code-block:: python

  #$ -o joblog.$JOB_ID

Write standard output to file joblog.$JOB_ID. $JOB_ID will be replaced by your job ID which is assigned once you submit your job.

.. code-block:: python

  #$ -j y

Merge error log with standard output (in file joblog.$JOB_ID)

.. code-block:: python

  #$ -pe shared 2

Request 2 processor cores

.. code-block:: python

  #$ -l h_rt=8:00:00,h_data=4G

Use -l option to specify job running time length and reserve memory
``h_rt=8:00:00 :`` reserve 8 hours for your job running time
``h_data=4G:`` reserve 4G per-core (since -pe 2 is used above, it will reserve 2 core x 4G memory = 8G total memory)

.. code-block:: python

  #$ -M $USER@mail

Send notification to your user email address

.. code-block:: python

   #$ -m bea

Specify the timing of the notification email to be sent out:

- b - when the job begins
- e - when the job ends
- a - when the job is aborted (ends in an error state)

**Part 2: Setup the Environment**

In the second part of the batch script, you should setup your Unix environment for your code to run, which includes loading modules and export paths for libraries.

To use any module provided by Hoffman and CCN, you'll need the following two lines

.. code-block:: python

  # load the job environment:
  . /u/local/Modules/default/init/modules.sh
  module use /u/project/CCN/apps/modulefiles

For example, load FSL

.. code-block:: python

  # Load the FSL module
  module load fsl

Another example, export a FSL variable

.. code-block:: python
  
  # This is optional
  # More info here: https://www.ccn.ucla.edu/wiki/index.php/Hoffman2:FSL 
  export NO_FSL_JOBS=true

Or export an additional PATH for a custom installed library under your .local/ directory

.. code-block:: python

  export PATH=$HOME/.local/bin:$PATH

**Part 3: Call your job script**

The third part of the batch script should call commands or other scrip for analysis.

For example, if you run feat

.. code-block:: python

  feat /my/path/to/design.fsf

Or if you have a script named as mycode.sh containing all the commands for your analysis,

Make sure your job script has executive privileges by using chmod command

.. code-block:: python

  chmod ug+x mycode.sh

call your script at the last part of your batch script

For example:

.. code-block:: python

  /bin/bash mycode.sh

Once the batch script is ready, you can submit it with qsub

.. code-block:: python

   qsub myjob.sh

To confirm the status of the submitted job, use command "myjob"

.. code-block:: python

   myjob

This will show the status of your jobs.

**Other methods**

Use an interactive way to create your batch job file in Hoffman, read more about job.q
Use qsub in one line command: examples

**2.2.3 Job Array**

Job array is a type of batch mode. It makes it possible to process different subjects using the same script on multiple Hoffman2 working nodes at the same time.

Here, we use the this template code to show how it can be done:

.. code-block:: python

  #!/bin/bash
  #$ -cwd
  # error = Merged with joblog
  #$ -o joblog.$JOB_ID.$TASK_ID
  #$ -j y
  #$ -pe shared 2
  #$ -l h_rt=8:00:00,h_data=4G
  # Email address to notify
  #$ -M $USER@mail
  # Notify when
  #$ -m a
  #  Job array indexes
  #$ -t 1-5:1

The only differences comparing with the single subject version are:

.. code-block:: python

  #$ -o joblog.$JOB_ID.$TASK_ID
  #$ -t 1-5:1

``-o joblog.$JOB_ID.$TASK_ID`` is for splitting logs into separate files for each subject with file name ``joblog.$JOB_ID.$TASK_ID.``
``-t 1-5:1`` is giving numbers [1 2 3 4 5] to step through.
This ``-t`` option should be followed by a lower number and a higher number range together with the step interval in the following format:

.. code-block:: python

  -t lower-upper:interval

where 

``lower`` is replaced with the starting number

``upper`` is replaced with the ending number

``interval`` is replaced with the step interval

So adding the argument

``-t 10-100:5``

will step through the numbers 10, 15, 20, 25, ..., 100 submitting a job for each one.

There will be an environment variable called ``SGE_TASK_ID`` whose value will be incremented over the range you specified. Hoffman2 job scheduler will submit one job for each SGE_TASK_ID, so your work will be parallelized.

**When to use it?**

Let's see how job array can replace a loop which is limited to run only in one computing node.

.. code-block:: python

  #!/bin/bash
  # myFuncSlowWrapper.sh
  for i in {1..100};
  do
      myFunc.sh $i;
  done

With job arrays, the work load will be split among many processors and can finish much faster. Here's how you rewrite it using job array in myFuncFastWrapper.sh as

.. code-block:: python

  #!/bin/bash
  # myFuncFastWrapper.sh
  echo $SGE_TASK_ID
  myFunc.sh $SGE_TASK_ID

**Example**

In this sample code, each SGE_TASK_ID is the index of the array of subjects, so each job in different node knows which subject it should process.

.. code-block:: python

  #!/bin/bash
  #$ -cwd
  # error = Merged with joblog
  ...
  ...
  # Set up the subjects list
  declare -a subjects

  subjects[1]="su3v3hkaykw2"
  subjects[2]="wxg5mk5u5xbz"
  subjects[3]="6q2bgkqu5grp"
  subjects[4]="whjue68jmwyh"
  subjects[5]="pfx3ju9wz8rr"

  echo "This is sub-job $SGE_TASK_ID"
  echo "This is subject ${subjects[$SGE_TASK_ID]}"

At the end, call your script to process the subject

.. code-block:: python

  # Your script content goes here...
  myFunc.sh  ${subjects[$SGE_TASK_ID]}

Software
--------

**3.4 FSL**

FSL is a comprehensive library of analysis tools for FMRI, MRI and DTI brain imaging data. FSL is written mainly by members of the Analysis Group, FMRIB, Oxford, UK.


Multiple versions are maintained on the Hoffman2 cluster to allow researchers to be consistent in using the same version for data analysis within a single study. You can either:

- do nothing, and always use the "current" version of FSL on the cluster
- actively choose which version of FSL you would like to run

We recommend the latter for data integrity and reproducibility.

**FSL GUI**

Make sure you source the FMRI Path in your Profile before doing anything, or else you won't be able to access FSL.

To run FSL using a GUI on hoffman2, use the following command:

.. code-block:: python

  $ fsl &

If you received this message while opening FSL

.. code-block:: python

   DISPLAY is not set. Please set your DISPLAY environment variable!

It means you did not open X11 along with your ssh connection. See here for more information. [insert link]

**FSL Tools**

A complete list of tools can be found `here <http://www.fmrib.ox.ac.uk/fsl/fsl/list.html>`_

Functional MRI (command line only)

.. list-table::
   :header-rows: 1

   * - Tool
     - Explanation
   * - `feat <http://www.fmrib.ox.ac.uk/fsl/feat5/index.html>`_
     - Model-based FMRI analysis: data preprocessing (including MCFLIRT motion correction); first-level FILM GLM timeseries analysis; higher-level FLAME Bayesian mixed effects analysis.
   * - `melodic <http://www.fmrib.ox.ac.uk/fsl/melodic/index.html>`_
     - Model-free FMRI analysis using Probabilistic Independent Component Analysis (PICA). MELODIC automatically estimates the number of interesting noise and signal sources in the data and because of the associated "noise model", is able to assign significance ("p-values") to the output spatial maps. MELODIC can also analyse multiple subjects or sessions simultaneously using Tensor-ICA.
   * - `fabber <http://www.fmrib.ox.ac.uk/fsl/fabber/index.html>`_
     - Fast ASL & BOLD Bayesian Estimation Routine. Efficient nonlinear modelling and estimation of BOLD and CBF from dual-echo ASL data, using Variational Bayes.

Structural MRI (command line only)

.. list-table::
   :header-rows: 1

   * - Tool
     - Explanation
   * - `bet <http://www.fmrib.ox.ac.uk/fsl/bet2/index.html>`_
     - Brain Extraction Tool - segments brain from non-brain in structural and functional data, and models skull and scalp surfaces.
   * - `fast <http://www.fmrib.ox.ac.uk/fsl/fast4/index.html>`_
     - FMRIB's Automated Segmentation Tool - brain segmentation (into different tissue types) and bias field correction.
   * - `first <http://www.fmrib.ox.ac.uk/fsl/first/index.html>`_
     - first	FMRIB's Integrated Registration and Segmentation Tool. FIRST uses mesh models trained with a large amount of rich hand-segmented training data to segment subcortical brain structures.

GUI Commands/Tools [Make sure to have X11 forwarding on]

.. list-table::
   :header-rows: 1

   * - Tool
     - Explanation
   * - fsl
     - Bring you to the FSL menu where you can choose what type of analysis.
   * - `fdt <http://www.fmrib.ox.ac.uk/fsl/fdt/index.html>`_
     - FMRIB's Diffusion Toolbox - tools for low-level diffusion parameter reconstruction and probabilistic tractography, including crossing-fibre modelling.
   * - `flirt <http://www.fmrib.ox.ac.uk/fsl/flirt/index.html>`_
     - FMRIB's Linear Image Registration Tool - linear inter- and intra-modal registration.
   * - `feat <http://www.fmrib.ox.ac.uk/fsl/feat5/index.html>`_
     - Model-based FMRI analysis: data preprocessing (including MCFLIRT motion correction); first-level FILM GLM timeseries analysis; higher-level FLAME Bayesian mixed effects analysis.
   * - `featquery <http://www.fmrib.ox.ac.uk/fsl/feat5/featquery.html>`_
     - A program which allows you to interrogate FEAT results by defining a mask or set of co-ordinates (in standard-space, highres-space or loweres-space) and get mean stats values and time-series.
   * - Glm
     - A GUI for setting up just the design matrix and contrasts, in the same way as in FEAT, for use with other modelling/inference programs such as randomise.
   * - `Melodic <http://www.fmrib.ox.ac.uk/fsl/melodic/index.html>`_
     - Model-free FMRI analysis using Probabilistic Independent Component Analysis (PICA). MELODIC automatically estimates the number of interesting noise and signal sources in the data and because of the associated "noise model", is able to assign significance ("p-values") to the output spatial maps. MELODIC can also analyse multiple subjects or sessions simultaneously using Tensor-ICA.
   * - `Possum <http://www.fmrib.ox.ac.uk/fsl/possum/index.html>`_
     - Physics-Oriented Simulated Scanner for Understanding MRI. An FMRI data simulator that produces realistic simulated images and FMRI time series given a gradient echo pulse sequence, a segmented object with known tissue parameters, and a motion sequence.
   * - Renderhighres
     - Transforms all thresholded stats images in a FEAT directory into high resolution or standard space and overlays these onto the high resolution or standard space images. This then produces PNG format pictures of the overlays and, by default, deletes the 3D AVW colour overlay images.
   * - `Renderstats <http://www.fmrib.ox.ac.uk/fsl/miscvis/index.html>`_
     - This tool allows you to combine a background image (raw FMRI or high resolution MRI) image with one or two statistics images. The statistics image(s) must be in registration with the background image.
   * - `Susan <http://www.fmrib.ox.ac.uk/fsl/susan/index.html>`_
     - Nonlinear noise reduction.
   * - `fslview <http://www.fmrib.ox.ac.uk/fsl/fslview/index.html>`_
     - Interactive display tool for 3D and 4D data.





