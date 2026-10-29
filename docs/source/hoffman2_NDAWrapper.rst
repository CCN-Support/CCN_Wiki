.. _hoffman2_NDAWrapper:

downloadcmd | Wrapper Script
=============================

A wrapper script of NDATools has been developed by our CCN member Dylan Hughes. To use it:

**Downloading brains from ABCD, by Dylan Hughes, 12/05/2022**

This will help you download ABCD images from baseline, year 2, year 4, or all 3 timepoints.

Feel free to reach out with any questions at dylanhughes@mednet.ucla.edu or slack.

1. Go to (the aesthetically pleasing) ABCD dictionary: https://nda.nih.gov/general-query.html?q=query=featured-datasets:Adolescent%20Brain%20Cognitive%20Development%20Study%20(ABCD)
2. On the left side, click on "Query by Global Unique Identifier (GUID)". You'll have to log in if you haven't already
3. Either a) add subject keys (1 per line) to the GUIDs box or b) upload a file with subject keys (1 per line). The subject key should move into the box that says "Subjects with data" or something along those lines.
4. Add to workspace (the button should be towards the bottom of the page). You'll see a little <thing> float to the top right.
5. Then, on the left side, click on Adolescent Brain Cognitive Development Study (ABCD) which is under Featured Datasets.
6. Within "OPTION TWO" (i.e., in the box towards the bottom of the page), click the dropdown for "Release X Minimally Processed Imaging Data - Month Year".
7. In the dropdown, select the data you want (e.g., Release X Minimally Processed Data. All task fMRI (nBack) - Month Year"
8. Add to workspace.
9. You'll see the "filter" move to a little black filter symbol (I think that's what it is?) in the top right corner. If you have followed these steps exactly, there should be a 2 next to it, indicating that you have selected two filters (i.e., some GUIDs and the imaging data). Click on the filter symbol. A window should pop up/slide in on the right side of the page.
10. At the bottom of this box/window, click "Submit to filter cart". You should see in the top right of the screen that the filter cart is loading.
11. Click "Create Data Package/Add Data to Study"
12. On the next page, click on "Create Data Package" (orange button).
13. Name your data package and select "Include associated data files"************ (very important). And then click "Create Data Package".
14. Make a note of the package ID number. You can either find this in the "Data Packages" section on the NDAR website (click on the orange settings wheel near the top right of the page, then click ")
################# Now to the terminal/command prompt
15. ssh into hoffman if you haven't already (or remote in however you do)
16. cd into the directory that houses the script (OPTIONAL)

.. code-block:: python                                             

  module load ccnscripts
                                              
17. Okay, now you can run this:

.. code-block:: python                                             

  bash downloadcommand_wrapper.sh -d /full/path/to/output/directory

*if you chose to ignore step #16 you can run:

.. code-block:: python                                             

  bash /u/project/CCN/apps/scripts/downloadcommand_wrapper.sh -d /full/path/to/output/directory 

18. The script will prompt you to input the package number. This can be found in the NDA download manager and should be in the "My Data Packages" section under "Package "Id" for the specific package of interest. It can also be found on your account page in NDAR - click on the little orange wheel next to your username (top right), then "Data Packages" (right above "Reset Password" button), scroll down to your packages and the ID should be the first column in the table.
19. The script will prompt for your NDAR username (this will be your NDAR username - NOT your login.gov/other two factor auth username)
20. The script will prompt for a timepoint. You can choose baseline, year2, year4, or all. Verbatim plz. DANGER: make sure you have the GBs if you decide to download all the data. Depending on how many subjects you selected, it will likely require a lot of space.
21. This should initiate a conversation with the script. Make sure everything looks right and ENTER "y" if it does and "n" if it doesn't. It will also give you the specific variables it's interpreting from your input download dir: where the ABCD images will be downloaded to package: package ID user: NDAR username
22. If this is your first time running it, the script will prompt for NDAR password (again, for NDAR account, not 2-fac auth). Ideally, your credentials will save somewhere for future runs, but if not you may have to enter your password each time.
23. And there you have it. 22 steps later we've successfully "simplified" the process..

Happy analyzing!


################# PS

Here's some more info about the NDA tools downloadcmd if you're interested:

.. code-block:: python                                             

  /u/project/CCN/apps/nda-tools/0.2.21/bin/downloadcmd -dp <<PackageID>> -d <<download directory>> -u <<username>> --file-regex <<string to look for>>

``<<PackageID>>`` : this follows the -dp argument. the package ID number, which can be found in the download manager on the left side of the window under "My Data Packages". There should be a number followed by the name that you assigned the package in step 13. The number is the package ID. You can also find this number on the Data Packages page online (see step 14).

``<<download directory>>`` : follows the -d argument. This specifies where you want the images to be downloaded.

``<<username>>`` : follows the -u argument. Your NDA username

``<<string to look for>>`` : downloadcmd will only download s3 links that contain the string (in the case of this script it will be baselineYear, 2YearFollowUp, or 4YearFollowUp depending on which timepoint you specify)

There's also a bunch more info about other flags here: https://hpc.nih.gov/apps/nda-tools.html

And the git folder is here: https://github.com/NDAR/nda-tools
