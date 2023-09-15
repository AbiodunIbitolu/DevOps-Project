# GIT PROJECT

## Initializing a Git Repository

Open the terminal and create a working folder / directory called _DevOps_ using the 'mkdir DevOps' command.

Change to the working directory by using the 'cd DevOps' command.

Run the 'git init' command.

![Alt text](<images/Screenshot 2023-09-15 at 07.58.09.png>)

## Making first commit

Inside the working directory, create a file called "index.txt" using the 'touch index.txt' command.

Use the echo command to write a sentence inside the txt file: 'echo "Excited to be making my first commit" > index.txt'

Add changes to git staging area using the 'git add .' command

Run the command 'git commit -m "inintial commit"'

![Alt text](<images/Screenshot 2023-09-15 at 07.58.41.png>)

## Working with Branches

Run the command 'git checkout -b main' to make a new branch called "main"

![Alt text](<images/Screenshot 2023-09-15 at 08.12.36.png>)

List your branches by running the 'git branch' command.

![Alt text](<images/Screenshot 2023-09-15 at 08.14.07.png>)

Change to an old branch called "master" by using this command: 'git checkour master'

![Alt text](<images/Screenshot 2023-09-15 at 08.26.15.png>)

Merging a branch into another one: 

Use the 'git merge' command. change into the receiving branch and run the 'git merge <2nd branch_name>' command.

![Alt text](<images/Screenshot 2023-09-15 at 08.51.11.png>)

## Deleting a git branch

Run the  'git branch -d <branch_name>'

# Collaboration and Remote Repositories

Logged into my exsiting Github account and created a new Repository called "Git-Project"

![Alt text](<images/Screenshot 2023-09-15 at 09.03.52.png>)

To add a remote repository to the local repository use the command: 'git remote add origin <link to your github repo>'

![Alt text](<images/Screenshot 2023-09-15 at 09.09.44.png>)

![Alt text](<images/Screenshot 2023-09-15 at 09.12.39.png>)

After commiting changes in the local repository, you push the content to the remote repository using the command: 'git push origin <branch name>'

![Alt text](<images/Screenshot 2023-09-15 at 09.20.39.png>)

# Cloning a Remote Git Repository

To clone a remote repositoy to our local machine, use the command: git clone '<link to your remote repository>'

![Alt text](<images/Screenshot 2023-09-15 at 09.40.43.png>)

## Branch Managememt and Tagging

Markdown Syntax: some of the most common markdown syntax elements were used in the completion of this documentation.
















