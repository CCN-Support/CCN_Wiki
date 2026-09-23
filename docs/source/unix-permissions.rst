.. _unix-permissions:

UNIX Permissions
================

Information on this page is heavily based on Perifect's article: `Understanding UNIX and chmod <https://www.perlfect.com/articles/chmod.shtml>`_

There are some differences in the way OSX handles permissions compared to other UNIX's.
However, the following should be accurate for all lab members on the Hoffman2 cluster.

Introduction
------------

There are three levels of ownership and three levels of permission that you
need to know.

.. image:: images/Unix-Permission.gif
   :width: 60%

Ownership
~~~~~~~~~

Every file in UNIX has an owner user and an owner group.

**Only the owner of a file can change its permissions** (unless you are an
administrator).

Owner
^^^^^

**Owner = you, the user.**

UNIX identifies each user by a User ID (UID) and a username (or login), such
as ``nick`` and ``bobby``.

Group
^^^^^

**Groups = your buddies.**

A user may belong to one or more groups of users. The concept of groups
serves the purpose of assigning sets of privileges for a given resource and
sharing them among many users that need to have them. For example, members
of a project working team may all need access to a common set of project
files.

On one system, user ``nick`` and user ``bobby`` might both belong to the
group ``perllab``. This allows them to have shared privileges over the files
for the lab's projects. User ``nick`` needs the files to contribute to the
project, and user ``bobby`` needs them to contribute to nick's work.

To find out what groups you are in, use :ref:`id`.

Other
^^^^^

**Others = the random guys.**

They represent anybody else on the system.

Permissions
~~~~~~~~~~~

Security for your files and directories.

Files
^^^^^

Every file on the system has an associated set of permissions. Permissions
tell UNIX what can be done with that file and by whom.

There are three things you can (or can't) do with a given file:

* **read** it: gain access to look into the file
* **write** (modify) it: change things in the file
* **execute** it: run it as a program

UNIX permissions specify which of the above operations can be performed for
each ownership relation with respect to the file. In simpler terms, what can
the owner do, what can the owner group do, and what can everybody else do
with the file?

For any given ownership relation, we need three bits to specify access
permissions:

* the first denotes read (``r``) access
* the second denotes write (``w``) access
* the third denotes execute (``x``) access

We have three ownership relations: **owner**, **group**, and **all**. This
gives us nine permission bits.

Each bit can be set or clear. A set bit is represented by its corresponding
operation letter (``r``, ``w``, or ``x``), and a clear bit is represented by
a dash (``-``).

For example:

.. code-block:: text

   rwxr-xr-x

This means that the owner can do anything with the file, while the group
owner and everyone else can only read or execute it.

Usually in UNIX there is also another bit that precedes this 9-bit pattern.
You do not need to know about it for now.

Directories
^^^^^^^^^^^

Directories also have permissions, but permissions have a different meaning
for directories.

* **read** determines whether a user can view the directory's contents,
  i.e. run ``ls`` in it.
* **write** determines whether a user can create new files or delete files
  in the directory. Note that a user with write access to a directory can
  delete files in the directory even if they do not have write permissions
  for those files.
* **execute** determines whether the user can ``cd`` into the directory.

To find out the permissions, use :ref:`ls`.

Tools
-----

These UNIX tools will help you when you want to modify permissions.

ls
~~

If you run ``ls -l`` at the command prompt, you will get something like the
following:

.. code-block:: console

   [nick@thekla src]$ ls -l
   -rwxr-xr-x   1 nick     users          382 Jan 19 11:49 bscoped.pl
   drwxr-xr-x   3 nick     users         1024 Jan 19 11:19 lib/
   -rwxr-xr-x   1 nick     users         1874 Jan 19 10:23 socktest.pl

The first column shows the permission bit pattern for each file. The third
column shows the owner, and the fourth column shows the owner group. The
information provided by ``ls -l`` should be enough for you to determine what
each user of the system can do with any of the files in the directory.

.. image:: images/Unix-Permission.png
   :width: 80%

chmod
~~~~~

To set or modify a file's permissions, use the ``chmod`` program. Only the
owner of a file may use ``chmod`` to alter its permissions.

The syntax is:

.. code-block:: text

   chmod [options] mode file(s)

The ``mode`` part specifies the new permissions for the file(s) that follow
as arguments.

A mode specifies which users' permissions should be changed and which access
types should be changed.

For example:

.. code-block:: console

   $ chmod a-x socktest.pl

This means that the execute bit should be cleared (``-``) for all users:
the owner, the group, and everyone else.

The permissions start with a letter specifying which users should be affected:

* ``u`` — the owner user
* ``g`` — the owner group
* ``o`` — others (neither ``u`` nor ``g``)
* ``a`` — all users (``u``, ``g``, and ``o``)

This is followed by a change instruction consisting of ``+`` (set bit) or
``-`` (clear bit), followed by the letter corresponding to the bit that
should be changed.

Examples
^^^^^^^^

Start by looking at the existing permissions:

.. code-block:: console

   $ ls -l socktest.pl
   -rwxr-xr-x   1 nick     users         1874 Jan 19 10:23 socktest.pl*

Now remove the executable bit for all users:

.. code-block:: console

   $ chmod a-x socktest.pl
   $ ls -l socktest.pl
   -rw-r--r--   1 nick     users         1874 Jan 19 10:23 socktest.pl

Then set the write bit for the owner group:

.. code-block:: console

   $ chmod g+w socktest.pl
   $ ls -l socktest.pl
   -rw-rw-r--   1 nick     users         1874 Jan 19 10:23 socktest.pl

Add executable permission for both the user owner and the group owner:

.. code-block:: console

   $ chmod ug+x socktest.pl
   $ ls -l socktest.pl
   -rwxrwxr--   1 nick     users         1874 Jan 19 10:23 socktest.pl*

Finally, remove both the write and executable bits for both the user and
group owners:

.. code-block:: console

   $ chmod ug-wx socktest.pl
   $ ls -l socktest.pl
   -r--r--r--   1 nick     users         1874 Jan 19 10:23 socktest.pl

Strange numbers...
^^^^^^^^^^^^^^^^^^

You may have encountered commands such as:

.. code-block:: console

   chmod 755 somefile

You can change the entire permission pattern of a file in one go using a
numeric mode.

Each of the three digits corresponds to one of the three permission
triplets:

* user (``u``)
* group (``g``)
* others (``o``)

Each permission bit in a triplet has a value:

* ``4`` for read (``r``)
* ``2`` for write (``w``)
* ``1`` for execute (``x``)

If a permission bit is set, add its value to the number for that triplet.
If it is clear, add nothing.

For example, if a file has ``rwxr-xr-x`` permissions:

.. code-block:: text

   Triplet for u: rwx => 4 + 2 + 1 = 7
   Triplet for g: r-x => 4 + 0 + 1 = 5
   Triplet for o: r-x => 4 + 0 + 1 = 5

This gives:

.. code-block:: text

   755

Thus, ``755`` is a concise way to say:

   I don't mind if other people read or run this file, but only I should be
   able to modify it.

Similarly, ``777`` means everyone has full access to the file.

chgrp
~~~~~

As the name implies, the ``chgrp`` utility changes the group of a file or
directory.

A user may only change a file's group to a group for which they are a member.

The syntax is:

.. code-block:: console

   chgrp <groupname> <file or directory name>

For example, suppose Suzie is a member of both the ``perllab`` and
``rubylab`` groups. She is collaborating with Que, who is a member of
``rubylab``. Unfortunately, the files she wishes to share have
``perllab`` as their group owner, so Que cannot read them.

Since Suzie is also a member of ``rubylab``, she can change the group:

.. code-block:: console

   $ chgrp rubylab project_directory

She might also need to change the directory's permissions to ensure that the
group owner can use the files:

.. code-block:: console

   $ chmod g+rwX project_directory

If Suzie wanted to ensure that all files contained in ``project_directory``
had the appropriate group and permissions, she could execute the following
recursive commands:

.. code-block:: console

   $ chgrp -R rubylab project_directory
   $ chmod -R g+rwX project_directory

umask
~~~~~

Each user has a default set of permissions that applies to files created by
that user, unless the software explicitly sets something else. This is often
called the **umask**, after the command used to change it.

The umask is either inherited from the login process, set in the
``.bash_profile`` file that configures an individual account, or run
manually.

On the Hoffman2 server, the default is to allow read/write permissions to
the user, while the group and others are given permission to read but not
write to new files.

If you wish to use more permissive defaults, you must change your umask in
``.bash_profile`` or manually each time you wish to change it.

Setting the umask is not immediately intuitive. As the name implies, the
argument to ``umask`` specifies the bits you do *not* want set.

For example:

* To make all new files give all permissions to the owner, read permission
  to the group, and no permissions to others:

  .. code-block:: console

     $ umask 027

We have not masked any bits by passing ``0`` in the first slot. We have
masked (removed) write permission for all group members by passing ``2`` in
the second slot, and we have masked all possible bits for others by passing
``7`` in the third slot.

Here are two more examples covering common cases:

* To allow the user and the group to read, write, or execute new files:

  .. code-block:: console

     $ umask 007

* To allow only the user to read, write, or execute new files (highest
  privacy):

  .. code-block:: console

     $ umask 077

newgrp
~~~~~~

There is also a handy utility called ``newgrp`` that can ease permission
problems.

The ``newgrp`` utility changes the default group ownership for new files.

For example:

.. code-block:: console

   $ id foo
   uid=8122(foo) gid=4004(staff) groups=4004(staff),1901(webadmin)

The user ``foo`` is a member of both the ``webadmin`` and ``staff`` groups.
Her current GID is ``staff``. This means that any new file she creates will
belong to the ``staff`` group.

When ``foo`` wishes to work with web files, it is easier for other members
of the ``webadmin`` group if the files she creates have ``webadmin`` as their
group ownership.

Instead of running ``chgrp`` for every file, she can use ``newgrp``:

.. code-block:: console

   $ newgrp webadmin

After running this command, newly created files will be owned by the
``webadmin`` group.

She may also wish to retain the more restrictive permissions of read-only
group access by default, but when doing collaborative work she can change to
group read/write permissions. Combining ``newgrp`` with ``umask`` makes this
easy:

.. code-block:: console

   $ umask 007

This needs to be executed **after** ``newgrp`` to take effect. Running
``newgrp`` resets the environment to its defaults.

id
~~

You can find the full list of groups that a user belongs to with:

.. code-block:: console

   $ id bobby

Replace ``bobby`` with the name of the user you are interested in.

It is common to check which groups two users belong to so that you can assign
a shared group to a file and allow both users to read, write, or edit the
file.

Further Reading
---------------

* `Understanding UNIX and chmod <https://www.perlfect.com/articles/chmod.shtml>`_
* For additional information, see the ``chmod`` manual page by running
  ``man chmod``. It contains additional options and types of permissions that
  are beyond the scope of this introduction.
* `An exhaustively complete tutorial for the chmod utility
  <https://www.catcode.com/teachmod/>`_
* `ONLamp chmod tutorial <https://www.onlamp.com/>`_
