Future Content
--------------

Hoffman 2 Introduction
======================

Hoffman2: Getting an Account
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

