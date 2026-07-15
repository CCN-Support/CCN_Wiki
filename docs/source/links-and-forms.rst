Commonly Used Links and Forms
=============================

Links & Sites
-------------

- `Scanner schedule: <https://www.sistat.ucla.edu/CCNSAS/login.asp/>`_ You do not need to log in to SISTAT to view the calendar. This is also bookmarked on the control room iMac.
- `SIStat system login: <https://www.sistat.ucla.edu/CCNSAS/ShowCalendar.asp#/>`_ This is your gateway to all activities regarding scan scheduling: booking scans, adding lab personnel, checking certification status, linking funds, uploading IRBs, and so on.
-  `BruinLearn: <https://bruinlearn.ucla.edu/>`_ This platform hosts the materials and exams required for safety certification.
- `CCN Website: <https://www.staglincenterforcogneuro.semel.ucla.edu/>`_ CCN's main, public-facing site. Since it points visitors to currently-active labs and projects, please update us with any changes to your `lab information <https://forms.gle/FKzH4nXrX2x8RKtM6>`_ or `active projects <https://forms.gle/yBmxgFYyQshUJW9TA>`_.
- `CCN YouTube channel: <https://www.youtube.com/@uclastaglincenterforcognit4262/videos/>`_ The channel contains very useful videos demonstrating common procedures at CCN--how to prepare a participant for a scan, navigating the XA30 upgraded software, placing voxels for spectroscopy, and so on.


Forms
-----

- `Metal Screening Form: <https://drive.google.com/file/d/1aUwmgXoij_czd8YktXmo0yDLjpqbuUpm/view?usp=sharing/>`_ REQUIRED for any person entering the scanner. Review carefully and submit documentation regarding any concerns `as a ticket <https://docs.google.com/document/d/13g-DVRauCgZAkScw0D5j03cCPeCiu2Fi/edit#heading=h.rgb25in7p2nc>`_.
- `Illness Screening Form: <https://drive.google.com/file/d/1kXsq_b25apk08NTTJ82GWX4adjsyz_iq/view?usp=sharing/>`_ Must be administered the evening before or morning of the participant's scan appointment. Reschedule your participant if they show signs of illness.
- `Pre-Scan Form: <https://uclahs.az1.qualtrics.com/jfe/form/SV_6tI8o3SvorTot9k/>`_ Fll out this form at the beginning of every scan. Bookmarked on the iMac and very brief.
- `Post-Scan Form: <https://uclahs.az1.qualtrics.com/jfe/form/SV_3BQesXgv9K8kgPc/>`_ Fill out this form after each scan. Bookmarked on the iMac and very brief.
- `Scan Cancellation Form: <https://forms.gle/E9uzNYDZheAqihce7/>`_ Fill out this form if you need to cancel a scan within 72 hours. You must also formally cancel your scan on SIStat.
- `Pilot Application Form: <https://drive.google.com/file/d/1rhfezXO3QP4pV5yjUnNmI8LNkjw7EqS9/view?usp=drive_link/>`_ Fill out this form if you would like to apply for scan hours toward a pilot project. Send the completed form to alenarto@g.ucla.edu and make sure to tell us the outcome of the pilot--if it helps you successfully secure funding, this information is crucial to keeping the pilot program going!


Manuals
-------

- `CCN Safety Manual: <https://drive.google.com/file/d/13xyaDkLcjBykdLvge3fMe-t_9HoukyMR/view>`_ Includes important information about emergency devices and procedures.
- `CCN Operations Manual: <https://drive.google.com/file/d/13xyaDkLcjBykdLvge3fMe-t_9HoukyMR/view>`_ Includes important information about handling reboots, save logs, and incidental findings.
- `Best Practices for Appointment Management: <https://drive.google.com/file/d/1yLR77cLHod_-bwauu4AtoAq51bbiNUgv/view?usp=sharing>`_ A list of recommendations for minimizing late cancellations.

Testing Area
------------
**Before scanning**

#. Load protocol
#. Verify coil selection
#. Check shim volume

**After scanning**

#. Review images
#. Export DICOMs
#. Archive data

Heading
~~~~~~~

Short intro paragraph.

.. important::

   One key takeaway.

Procedure
~~~~~~~~~

Numbered steps.

.. warning::

   Common failure mode.

.. rubric:: Troubleshooting

Bullet list.

.. seealso::

   Link to related section.

.. admonition:: XA30 Only

   This feature is only available on XA30.

Sample text. Does the box wrap around?

.. sidebar:: Quick Reference

   * MB factor: 3
   * TR: 800 ms
   * TE: 37 ms

More text. Where does the box end up? Does it stay on the left of the box? Does it wrap around?

I put this on a new line. Where is it now? Under the box or beside it?

Now I'm trying a table:

.. list-table::
   :header-rows: 1

   * - Name
     - Type
     - Description
   * - **foo**
     - String
     - Name of the object.
   * - ``count``
     - Integer
       Can it overflow onto the next row?
     - Number of items.
   * - ``flag``
     - Boolean
     - Whether it is enabled.


The following section demonstrates several common reStructuredText elements.

1. Grid Table
-------------

+------------+------------+
| Column 1   | Column 2   |
+============+============+
| Item A     | Value A    |
+------------+------------+
| Item B     | Value B    |
+------------+------------+

2. Simple Table
---------------

========== ==========
Column 1   Column 2
========== ==========
Item A     Value A
Item B     Value B
========== ==========

3. Code Block
-------------

.. code-block:: python

   def hello():
       print("Code block text!")

4. Image
--------

.. image:: images/example.png
   :width: 300px
   :align: center
   :alt: Example image

5. Figure
---------

.. figure:: images/example.png
   :width: 50%
   :align: center

   Figure 1. This is an example figure caption.

6. Topic
--------

.. topic:: Background

   This is a topic box used to provide background information.

7. Rubric
---------

.. rubric:: Before You Begin

This paragraph follows a rubric.

8. Horizontal Rule
------------------

This text appears above the rule.

----

This text appears below the rule.

9. Sidebar
----------

.. sidebar:: Tip

   This content appears in a sidebar (if supported by your theme).

Continue reading the main text here.

10. Definition List
-------------------

API
    Application Programming Interface.

SDK
    Software Development Kit.

CLI
    Command Line Interface.

11. Field List
--------------

:Author: Jane Doe
:Version: 1.0
:Status: Draft

12. Option List
---------------

-h, --help
    Show the help message.

-v, --verbose
    Enable verbose output.

-o FILE
    Write output to FILE.

13. Block Quote
---------------

    This is a block quote.

    It can span multiple paragraphs if desired.

14. Line Block
--------------

| Dr. Jane Smith
|   Department of Computer Science
|   University of Example
|   jane@example.edu
| Allows newlines without having to hit Return twice in the code to inject the line break

15. Card (sphinx-design feature)
--------------------------------

.. card:: My Card

   This is inside a card.

16. Dropdown (sphinx-design feature)
------------------------------------

.. dropdown:: More information

   Hidden content goes here.

17. Flowchart (Mermaid feature)
--------------------------------

.. mermaid::
   :caption: Figure 1. Colored nodes (default is black with white text)

   flowchart TD
       A[User visits website] --> B{Logged in?}
       B -->|Yes| C[Show dashboard]
       B -->|No| D[Show login page]
       D --> E[User enters credentials]
       E --> F{Credentials valid?}
       F -->|Yes| C
       F -->|No| G[Display error message]
       G --> D

       classDef start fill:#d5f5e3,stroke:#27ae60,color:#000;
       classDef decision fill:#fcf3cf,stroke:#f39c12,color:#000;
       classDef action fill:#d6eaf8,stroke:#2980b9,color:#000;

       class A start;
       class B,F decision;
       class C,D,E,G action;

.. mermaid::
   :caption: Figure 2. With darker colors and "YES" and "NO" as nodes to give them more space

   flowchart TD
       A[User visits website] --> B{Logged in?}
       B --> Y1[YES]
       B --> N1[NO]

       Y1 --> C[Show dashboard]
       N1 --> D[Show login page]

       D --> E[User enters credentials]
       E --> F{Credentials valid?}

       F --> Y2[YES]
       F --> N2[NO]

       Y2 --> C
       N2 --> G[Display error message]
       G --> D

       classDef start fill:#a9dfbf,stroke:#239b56,color:#000,font-size:18px;
       classDef decision fill:#f7dc6f,stroke:#d68910,color:#000,font-size:18px;
       classDef action fill:#85c1e9,stroke:#2471a3,color:#000,font-size:18px;
       classDef choice fill:#f2f2f2,stroke:#666,color:#000,font-size:16px;

       class A start;
       class B,F decision;
       class C,D,E,G action;
       class Y1,N1,Y2,N2 choice;


.. mermaid::
   :caption: Figure 3. Using dark theme (see conf.py)

   %%{init: {
       "theme": "dark",
       "themeVariables": {
           "fontSize": "18px",
           "edgeLabelBackground": "#333333"
       }
   }}%%

   flowchart TD
       A[User visits website] --> B{Logged in?}
       B -->|  YES  | C[Show dashboard]
       B -->|  NO  | D[Show login page]
       D --> E[User enters credentials]
       E --> F{Credentials valid?}
       F -->|  YES  | C
       F -->|  NO  | G[Display error message]
       G --> D

       classDef start fill:#1e8449,stroke:#82e0aa,color:#fff,font-size:18px;
       classDef decision fill:#b7950b,stroke:#f7dc6f,color:#000,font-size:18px;
       classDef action fill:#2874a6,stroke:#85c1e9,color:#fff,font-size:18px;

       class A start;
       class B,F decision;
       class C,D,E,G action;
