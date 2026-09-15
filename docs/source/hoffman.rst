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
1.3 Accessing the Cluster
~~~~~~~~~~~~~~~~~~~~~~~~~
1.4 Working in a Linux Environment
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
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

