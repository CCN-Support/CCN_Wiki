Resources and Learning
======================

CCN has compiled a list of useful resources for learning about data analysis, coding, and research science. These resources are provided below in both Table and filterable Directory formats, to allow the user to easily discern which items cover which topics.


Resource List - Table
---------------------

.. raw:: html


   <p>
      Search the table, scroll horizontally through all topics, or click a
      topic heading to show only resources covering that topic.
   </p>

   <iframe
      src="_static/resources_matrix_preview_with_links.html"
      title="Complete 17-topic resource matrix"
      style="width: 100%; height: 600px; border: 1px solid #d9dee7; border-radius: 8px;"
      loading="lazy">
   </iframe>

   <p style="margin-top: 1em;">
      [<a href="_static/Resources%20Table.xlsx" download>
         Click to download this table as an Excel spreadsheet
      </a>]
   </p>


Resource List - Directory 
-------------------------

The directory below allows you to easily see which topics each resource addresses and filter by one or more topics.

If you are on mobile, it will be easier than the table above to navigate.

.. raw:: html

   <iframe
      id="resources-directory"
      src="_static/resources_directory_with_links.html"
      title="Resources Directory"
      style="width: 100%; min-height: 200px; border: 0; overflow: hidden;"
      scrolling="no">
   </iframe>

   <script>
   (function () {
       const frame = document.getElementById('resources-directory');

       window.addEventListener('message', function (event) {
           if (event.origin !== window.location.origin) {
               return;
           }

           if (!event.data || event.data.type !== 'resources-directory-height') {
               return;
           }

           frame.style.height = event.data.height + 'px';
       });
   })();
   </script>

