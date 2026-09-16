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
