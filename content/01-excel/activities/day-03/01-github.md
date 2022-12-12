+++
title = "01. Github Playground 👩‍🏫🧑‍🏫"
weight = 1
tags = ["excel"] 
+++

* Guide for `Github`   steps:

  * Visit <https://github.com>, and ask students to log in to their personal accounts.

  * From the main page, create a new repository with an initializing `README.md` file, as detailed in the following screenshots and instructions. Explain that it’s standard in the tech world to include a "README" file that explains what each repository contains.

    ![git repo](../images/GitDemo_1.png)

  * Make the repository public so Graders can always access it for grading.

  * Then, click on the “Add .gitignore” button and type "Python", as in the following image:

    ![create git ignore](../images/Git_ignore_1.png)

  * Click the green “Create repository” box. After clicking “Create repository”, you’ll now be on the homepage of your repository.

    * The purpose of the gitignore file is to ensure that GitHub can ignore certain files that do not need to be tracked.

    * Click the `.gitignore` file in your repository to open the file, as in the following image:

      ![create git ignore](../images/Git_ignore_2.png)

    * In the `.gitignore` file, you’ll find files that won’t be tracked for this repository. Files are organized by extension and distribution packages, as in the following image:

      ![Git ignore file](../images/Git_ignore_3.png)

    * If you don’t want GitHub to track a file, you can edit the `.gitignore` file by adding the file name or file extension.

    * Let's untrack a common file, `.DS_Store`, for this repository. The `.DS_Store` file is created and maintained by the macOS Finder application in every folder; it has functions similar to the file `desktop.ini` in Microsoft Windows.

      * Click on the pencil icon in the `.gitignore` file to edit the file.
      * Once in edit mode, add the following code to the `.gitignore` above the `# Distribution / packaging` section.

      ```python
      # .DS_Store
      .DS_Store
      ```

      * Scroll to the end and enter the commit message, "Updating .gitignore file.", where it says “Commit changes”.
      * Then, click the green “Commit changes” button, as in the following image:

      ![edit git ignore](../images/Git_ignore_4.png)

  * Switch back to the computer's desktop, create a new empty Excel file, and save the file. We’ll use this file to demonstrate how to upload new files.

  * Navigate back to the repository homepage that you created, and click “Upload files,” as in the following image:

    ![upload file](../images/GitDemo_upload.png)

  * Choose your Excel file in the dialog box; instead of the “Upload Files” button, you may also drag files from your desktop to the GitHub repo web page. Add a commit message, and commit the changes.

  * Finally, refresh the web page to show that the new file is now saved to the repository, as captured in the following GIF:

    ![drag file](../images/GitDemo_filedrag.gif)