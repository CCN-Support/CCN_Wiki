
Testing Area
============

**Before scanning**

#. Load protocol
#. Verify coil selection
#. Check shim volume

**After scanning**

#. Review images
#. Export DICOMs
#. Archive data

Heading
-------

Short intro paragraph.

.. important::

   One key takeaway.

Procedure Test
--------------

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
~~~~~~~~~~~~~

+------------+------------+
| Column 1   | Column 2   |
+============+============+
| Item A     | Value A    |
+------------+------------+
| Item B     | Value B    |
+------------+------------+

2. Simple Table
~~~~~~~~~~~~~

========== ==========
Column 1   Column 2
========== ==========
Item A     Value A
Item B     Value B
========== ==========

3. Code Block
~~~~~~~~~~~~~

.. code-block:: python

   def hello():
       print("Code block text!")

4. Image
~~~~~~~~

.. image:: images/example.png
   :width: 300px
   :align: center
   :alt: Example image

5. Figure
~~~~~~~~~

.. figure:: images/example.png
   :width: 50%
   :align: center

   Figure 1. This is an example figure caption.

6. Topic
~~~~~~~~

.. topic:: Background

   This is a topic box used to provide background information.

7. Rubric
~~~~~~~~~

.. rubric:: Before You Begin

This paragraph follows a rubric.

8. Horizontal Rule
~~~~~~~~~~~~~~~~~~

This text appears above the rule.

----

This text appears below the rule.

9. Sidebar
~~~~~~~~~~

.. sidebar:: Tip

   This content appears in a sidebar (if supported by your theme).

Continue reading the main text here.

10. Definition List
~~~~~~~~~~~~~~~~~~~

API
    Application Programming Interface.

SDK
    Software Development Kit.

CLI
    Command Line Interface.

11. Field List
~~~~~~~~~~~~~

:Author: Jane Doe
:Version: 1.0
:Status: Draft

12. Option List
~~~~~~~~~~~~~

-h, --help
    Show the help message.

-v, --verbose
    Enable verbose output.

-o FILE
    Write output to FILE.

13. Block Quote
~~~~~~~~~~~~~

This is a normal paragraph introducing the quote.

    This is a block quote.

    It can contain multiple paragraphs.

This is back to normal text.

14. Line Block
~~~~~~~~~~~~~

| Dr. Jane Smith
|   Department of Computer Science
|   University of Example
|   jane@example.edu
| Allows newlines without having to hit Return twice in the code to inject the line break

15. Epigraph
~~~~~~~~~~~~~
.. epigraph::

   Documentation is a love letter that you write to your future self.

   -- Damian Conway

16. Cards (sphinx-design feature)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. card:: My Card

   This is one card.

.. grid:: 3
   :gutter: 3

   .. grid-item-card:: 📘 Guides

      Tutorials and walkthroughs.

   .. grid-item-card:: 🛠 Tools

      Configuration and utilities.

   .. grid-item-card:: 📚 Reference

      Detailed documentation.

17. Dropdown (sphinx-design feature)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. dropdown:: More information

   Hidden content goes here.

18. Badges (sphinx-design feature)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. dropdown:: Documentation Status Examples

   This page contains several types of status indicators:

   :bdg-success:`Complete` The installation guide has been reviewed and tested.

   :bdg-info:`Info` This section contains additional background information.

   :bdg-warning:`Warning` This configuration option may change in future releases.

   :bdg-danger:`Deprecated` This method should no longer be used.

   :bdg-primary:`New` This feature was added in version 2.0.

   :bdg-secondary:`Optional` This step is not required for most users.

Using badges in inline text:

The API is :bdg-success:`stable` and the old endpoint is
:bdg-danger:`deprecated`.

Using badges as compact labels in a list:

* :bdg-success:`PASS` Unit tests completed successfully
* :bdg-warning:`CHECK` Review required before merging
* :bdg-danger:`FAIL` Build failed
* :bdg-info:`NOTE` Additional information available

19. Flowchart (Mermaid feature)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

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
   :caption: Figure 3. Using dark theme (see conf.py) and rounded pill shapes for yes/no nodes

   %%{init: {
       "theme": "dark",
       "themeVariables": {
           "fontSize": "18px"
       }
   }}%%

   flowchart TD
       A([User visits website]) --> B{Logged in?}

       B --> Y1([YES])
       B --> N1([NO])

       Y1 --> C[Show dashboard]
       N1 --> D[Show login page]

       D --> E[User enters credentials]
       E --> F{Credentials valid?}

       F --> Y2([YES])
       F --> N2([NO])

       Y2 --> C
       N2 --> G[Display error message]
       G --> D

       classDef start fill:#1e8449,stroke:#82e0aa,color:#fff,font-size:18px;
       classDef decision fill:#b7950b,stroke:#f7dc6f,color:#000,font-size:18px;
       classDef action fill:#2874a6,stroke:#85c1e9,color:#fff,font-size:18px;
       classDef answer fill:#5d6d7e,stroke:#d5d8dc,color:#fff,font-size:18px;

       class A start;
       class B,F decision;
       class C,D,E,G action;
       class Y1,N1,Y2,N2 answer;
