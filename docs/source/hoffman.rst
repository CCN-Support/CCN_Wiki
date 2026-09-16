Hoffman2 Computing Cluster
==========================

Getting Started
---------------

1.1 Introduction
~~~~~~~~~~~~~~~~

What is Hoffman?
^^^^^^^^^^^^^^^^
The Hoffman2 Cluster is a campus computing resource at UCLA and is named for Paul Hoffman (1947-2003). It is maintained by the `IDRE <https://idre.ucla.edu/>`_ at UCLA and the main official webage is `here <https://www.hoffman2.idre.ucla.edu/>`_. With many high end processor, data storage, and backup technologies, it is a useful tool for executing research computations especially when working with large datasets. More than 1000 users are currently registered and the cluster sees tremendous usage. Click here [will link to Getting an Account] to find out how to join. In September 2014 alone, there were more than 5.5 million compute hours logged. See more usage statistics `here <https://www.hoffman2.idre.ucla.edu/status/>`_.

Anatomy of the Computing Cluster
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

What does Hoffman2 consist of?

- Login Nodes
- Computing Nodes
- Storage Space
- Univa Grid Engine

.. image :: images/Hoffman_anatomy.jpg

**Login Nodes**

There are four login nodes which allow you to access and interact with the Hoffman2 Cluster. These are essentially four dedicated computers that you can SSH into and use to look at and edit your files or submit computing jobs to the queue (more on what the queue is in a bit). It is important to remember that these are four computers being shared by ALL the Hoffman2 users. Doing ANY type of heavy computing on these nodes is frowned upon. If you are:

- moving lots of files
- calculating the inverse solution to an EEG signal, or
- running a bunch of python scripts to extract tractography of a brain

You should NOT be doing this on a login node. If the sysadmins at ATS find any process that is taking up too many resources on the login nodes, they reserve the right to terminate the process immediately.

**Computing Nodes**

As of April 2014, Hoffman2 is made up of more than 12,000 processors across three data centers and this number continues to grow as the cluster is expanded. The individual cores of the processors are where your programs gets executed when you submit a job to the cluster. There are ways to request different amount of resources, such as how much RAM or CPU cores your program/job needs.

There is also a GPU cluster that has more than 300 nodes, but access to this must be requested separately from a normal Hoffman2 account.

The reason the number of computing cores continues to grow is because more resource groups (like individual research labs) join Hoffman2 and buy nodes to be integrated into the cluster. Nodes contributed by a resource group are guaranteed to that resource group and can be used to run longer jobs (up to 14 days). As of June 2013, the Cohen and Bookheimer groups on Hoffman2 have 96 cores:

6 nodes (installed pre 2010) each with
  - 8 cores
  - 8GB RAM
3 nodes (installed Fall 2012) each with
  - 16 cores
  - 48GB RAM

Use the command ``mygroup`` to see what resources you have available.

1.2 Getting an Account
~~~~~~~~~~~~~~~~~~~~~~

**Requesting Hoffman2 Account**

What You Need: A UCLA Logon ID, available for free to any UCLA staff, student, or faculty member. If you do not have a UCLA Logon ID, head to the `UCLA Logon services page <https://accounts.iam.ucla.edu/#/>`_. Click on "Create UCLA Logon ID".

**Applying for the Account**

ATTENTION: If you are a PI interested in Hoffman2, please see the section **Becoming a Faculty Sponsor** below.

1. Navigate to the `Requesting an account page <https://www.hoffman2.idre.ucla.edu/Accounts/Requesting-an-account.html>`_.
2. Read over the application summary.
3. Click "New User Registration".
4. Log in using your UCLA Logon ID and password.
5. Fill out the form with appropriate information. For Hoffman2, your Faculty Sponsor should be Mark Cohen, Alison Burggren (for Susan Bookheimer's lab), or your respective PI if they are a Faculty Sponsor on Hoffman.

**Proposed Username**
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



1.3 Accessing the Cluster
~~~~~~~~~~~~~~~~~~~~~~~~~

SSH - Command Line
^^^^^^^^^^^^^^^^^^

SSH stands for Secure Shell and is a method of remotely logging into a computer using an encrypted connection. It is a command-line tool and is available on most *nix-based operating systems with ports available for Windows.

**Mac/Linux/Unix**

*Simple SSH*

Use the ssh command from a terminal:

.. code-block:: python

  ssh login_id@hoffman2.idre.ucla.edu

where login_id is replaced by your cluster user name.

*GUI-Enabled SSH*

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

Remote Desktop [Recommended]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Currently, Hoffman supports connecting to the cluster via the X2Go client and the NoMachine client.

**NX Client - GUI**

The NX Client program allows you to set up a Virtual Network Computing (VNC)-like session with Hoffman2. This session will keep running even if your Internet connection drops in and out (much like `screen <https://www.ccn.ucla.edu/wiki/index.php/Using_Screen>`_ on the command line).

**X2Go - GUI**

X2Go provides a desktop-like GUI for accessing the Hoffman server. Please see here [insert X2Go section] to find out more about setup details.



Change Passwords
^^^^^^^^^^^^^^^^

Once you've logged on and made sure its works, you can change your password to something more rememberable To change passwords, logon and type:

.. code-block:: python

  passwd

It should ask you for your old password and then new ones.


1.4 Working in a Linux Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A tutorial from Hoffman2 support
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Here <https://www.hoffman2.idre.ucla.edu/Using-H2/Command-line/Unix-command-line.html>`_ is a simple tutorial from Hoffman2's support page

Permissions
^^^^^^^^^^^

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
^^^^^^^^^^^^^^^^^^^^^^

The following series of tutorials provide a very basic introduction to file system navigation on unix like systems without any assumptions of prior knowledge on the topics.

- Listing files & directories, making directories, changing directories, the . and .. directories, pathnames, the "home" directories

    - `Tutorial One <http://www.ee.surrey.ac.uk/Teaching/Unix/unix1.html>`_

- Copying files, moving files, removing files and directories, displaying the contents of a file, searching the contents of a file

    - `Tutorial Two <http://www.ee.surrey.ac.uk/Teaching/Unix/unix2.html>`_

**List of Utilities Covered**

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
^^^^^^^^^^^^^^^^^^^^^^^

This is where your career on a UNIX type system can be made or crippled. Sure you know how to move around, list files, find out where you are, and display the contents of files. But now you have to do something with those files. And let's face it, there are a whole lot of files.

It is **highly recommended** that the reader look over `Tutorial Four <http://www.ee.surrey.ac.uk/Teaching/Unix/unix4.html>`_ on how to use wildcards for matching before preceding with this section.

The good news is, using the above utilities we just learned about we can accomplish almost anything we want to do using a very handy utility called find.

As the name might imply, find, well, finds things. What it finds is up to you. find has many, many options. All laid out in its man page. However, for most purposes only a few are needed. We'll cover those here.

A basic find command looks like

.. code-block:: python

  $ find /path/to/directory -name 'filename.txt'

This command looks at all files in /path/to/directory and in all directories therein for a file named 'filename.txt'.

**Common Options**

:option:`-type`
    Specifies the type of file we're looking for. e.g. text file, directory, link, etc.
:option:`-name`
    Specifies the name of the file. Case Sensitive
:option:`-iname`
    Specifies the name of the file. Case Insensitive
:option:`-or`
    Joins the precedeing and following terms by the boolean OR
:option:`-and`
    Joins the preceding and following terms by the boolean AND
:option:`-not`
    negates the next term. e.g. -not -empty means "is not empty"
:option:`-exec`
    excutes a shell command for each file found. The only 'trick' is to replace the actual file name with {} and end the command with a \;. This should become clear when reviewing the examples below.
:option:`-empty`
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
^^^^^^^^^^^^^^^^^^^^^

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

The man pages (for "manual") are the be all end all reference on UNIX systems.

A `Beginners' Guide to man Pages <http://www.tfug.org/helpdesk/general/man.html>`_ is an excellent introduction into how to move around a man page easily and understand what it's telling you.



1.5 Quotas
~~~~~~~~~~
1.6 Modules
~~~~~~~~~~~
1.7 Changing Passwords
~~~~~~~~~~~~~~~~~~~~~~
1.8 Password-less ssh Login
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Computing
---------
2.1 Software Tools
~~~~~~~~~~~~~~~~~~
2.2 Run Your Jobs
~~~~~~~~~~~~~~~~~
2.2.1 Interactive Sessions
^^^^^^^^^^^^^^^^^^^^^^^^^^
2.2.2 Batch Mode
^^^^^^^^^^^^^^^^
2.2.3 Job Array
^^^^^^^^^^^^^^^
2.3 Monitoring Jobs
~~~~~~~~~~~~~~~~~~~

Software
--------
3.1 MATLAB
~~~~~~~~~~
3.2 R
~~~~~
3.3 WEKA
~~~~~~~~
3.4 FSL
~~~~~~~
3.5 Python
~~~~~~~~~~
3.6 Jupyter Notebook
~~~~~~~~~~~~~~~~~~~~
3.7 Singularity
~~~~~~~~~~~~~~~
3.8 Git
~~~~~~~
3.9 X2Go
~~~~~~~~

Productivity
------------
4.1 Scripts
~~~~~~~~~~~
4.2 Data Transfer
~~~~~~~~~~~~~~~~~
4.3 Sharing Filesystems
~~~~~~~~~~~~~~~~~~~~~~~
4.4 Tools
~~~~~~~~~
4.5 Mailing List
~~~~~~~~~~~~~~~~

^^^

