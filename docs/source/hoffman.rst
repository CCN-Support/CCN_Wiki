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



1.3 Accessing the Cluster
~~~~~~~~~~~~~~~~~~~~~~~~~

SSH - Command Line
^^^^^^^^^^^^^^^^^^

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

Remote Desktop [Recommended]
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Currently, Hoffman supports connecting to the cluster via the X2Go client and the NoMachine client.

**NX Client - GUI**

The NX Client program allows you to set up a Virtual Network Computing (VNC)-like session with Hoffman2. This session will keep running even if your Internet connection drops in and out (much like `screen <https://www.ccn.ucla.edu/wiki/index.php/Using_Screen>`_ on the command line).

**X2Go - GUI**

X2Go provides a desktop-like GUI for accessing the Hoffman server. Please see here to find out more about setup details.



Change Passwords
^^^^^^^^^^^^^^^^

Once you've logged on and made sure its works, you can change your password to something more rememberable To change passwords, logon and type:

.. code-block:: python

  passwd

It should ask you for your old password and then new ones.


1.4 Working in a Linux Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Hoffman2: Linux Tutorial**

A tutorial from Hoffman2 support

`Here <https://www.hoffman2.idre.ucla.edu/Using-H2/Command-line/Unix-command-line.html>`_ is a simple tutorial from Hoffman2's support page

**Permissions**

Permissions determine who and to what degree users can access a file.

The key terminology and function of the permission system is found here:

[insert unix permissions page]


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

