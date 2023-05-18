# Rails Challenges
This repository holds the Rails pair programming challenges for the 2023 Charlie cohort.  
***NOTE: Rails applications will not be pushed to this repo. The work from the challenges will be saved as markdown files that include the the team members' names.***

### Process Notes
- Anything wrapped in < > is an indication that this will be named uniquely, the < > are NOT included in the command
- $ is an indication of a command line prompt, the $ is not included
- Anything in ( ) is informational and not included in the command
- The term local/locally your personal computer
- The term remote means GitHub
### Naming Conventions
Branches and file names should be in all lowercase letters with no spaces:
- Branch name is in kebob-case: topic-initials1-initials2 (ex. intro-cb-nmr)
- File name is in snake_case: topic_name1_name2.md (ex. intro_charlean_nicole.md)
### Informational Commands
Use this informational command to tell you what files have been modified and what phase of the git process you are on:  
- $ `git status`  
Use this informational command to see what branch you are currently on:  
- $ `git branch`

### Cloning the Repo
Use this command if you don't have the repository (folder) on your local machine:   
- $ `git clone <repo-url>` (pasted from clipboard on GitHub)


### Create a Branch
Use this command if you need to create a branch that does not exist anywhere:  
- $ `git checkout -b <topic-initials1-initials2>` (ex. intro-cb-nmr)


### Changing to an Existing Local Branch
Use this informational command to see what branches exist on your local machine:  
- $ `git branch`

Use this command to move to a branch that exist on your local machine:  
- $ `git checkout <branch-name>`


### Changing to a Branch that Existing on GitHub
Use these commands if the repo you are working on has a branch but it is NOT on your local machine:  
- $ `git fetch origin <branch-name>`
- $ `git checkout <branch-name>`


### Pushing Local Code to GitHub
Use these commands to add the code you have on your local machine to GitHub:
- $ `pwd` (ensure you are in the repository level)
- $ `git status` (informational command, ensure you are on the correct branch and in the correct directory)
- $ `git add <file-name>`
- $ `git commit -m "message describing the work that was accomplished"`
- $ `git push origin <branch-name>`


### Pulling Remote Code to Local
Use this command if you DO have the repository on your local machine but DON'T have the latest version of the code from GitHub:  
- $ `git pull origin <branch-name>`


### Deleting a Branch on GitHub
Branches exist on your local and on the remote. Always delete your branch in both places.
- Branches in GitHub can be deleted via the GUI


### Deleting a Branch on Local
Branches exist on your local and on the remote. Always delete your branch in both places.
- $ `git checkout main`
- $ `git pull origin main`
- $ `git branch -d <branch-name>`

### Deleting a Rails Application
Because the rails application is stored in your local database, you have to drop the database before removing the application from your local machine.
- Ensure you are on the rails application in the terminal in order to drop its database
- Stop the server if running and drop the database
  - Control + C  
  - $ `rails db:drop`
- To permanently remove the application from your local machine, you have to go back one level
  - $ `cd ..`
  - $ `rm -rf <rails_app_name>` 
