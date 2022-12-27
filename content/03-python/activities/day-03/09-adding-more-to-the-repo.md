+++
title = "09. Git 👩‍🎓👨‍🎓"
weight = 9
tags = ["python"] 
+++

* You only added files using the GitHub website, which works well enough when just dealing with one or two files. What happens when we need to quickly add multiple files?

  * The command line comes to the rescue!

* Creating a repo and adding files with Terminal/Git Bash.

  * First, create a new repo.

  * From the repo page, click the green box in the top-right labeled "Clone or download", select "Use SSH", and copy the link to the clipboard, as captured in the following GIF:

  ![clone repo](../images/GitClone.gif)

  * Open Terminal (or Git Bash for Windows users), and navigate to the home folder using `cd ~`.

  * Type `git clone <repository link>` in the terminal to clone the repo to the current directory. Once this code has run, everyone should find a folder with the same name as the repo, as captured in the following image:

    ![terminal clone](../images/GitClone_command.png)

  * Open the folder in VS Code, and create two python script files, named `script01.py` and `script02.py`.

  * Then, open Terminal/Git Bash, and navigate to the repo folder. Run the following lines, explaining each line as you go.

  ```bash
  # Displays that status of files in the folder
  git status

  # Adds all the files into a staging area
  git add .

  # Check that the files were added correctly
  git status

  # Commits all the files to your repo and adds a message
  git commit -m <add commit message here>

  # Pushes the changes up to GitHub
  git push origin main
  ```

  * Finally, navigate to the repo on [Github.com](https://github.com/) to confirm that the changes have been pushed up.

* Make sure every student was able to successfully clone a repo, add files to the repo, commit the changes, and then push the changes to GitHub, all from the command line.




In this activity, you will create a new repository, clone it, and add files via command line

## Instructions

* Using the repo that we just created, make or add the following changes:


* Add new lines of code to one of the Python files.
* Create a new folder.
* Add a file to the newly created folder.
* Add, commit, and push the changes.
* Delete the new folder.
* Add, commit, and push the changes again.