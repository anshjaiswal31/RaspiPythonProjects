
### Git Basics

Here's a tutorial on the very basics of git. These are provided in a logical sequence and do not intend to cover all the options git provides. 

##### Account Creation 
  - Head off to http://github.com and create an account there if you haven't already created one.
  - Once you've setup your account and credentials at http://github.com you are now good to create your own repository
  - A git repository is where you will store all your code, create new code and do all your development activity. So head over to the "Repository" section and create your new repo (repository) by clicking on "New". You will need to specify the name of the new repo along with some other options i.e. private, public, etc. 
  - If you are keen on having others from the community collaborate with you and leverage what you've aldready built you would need to create a public repo. Either ways I would always encourage you to keep your repo public.
  - You will now use this repo to create any new code and upload code from the various machines where you perform your development tasks.

#### Clients For Using Git
  - There are various clients for using git. Clients exists for various operating systems i.e. windows, linux, mac, etc. 
  - If you are using the Raspberry Pi you should already have the git client installed. Try issuing the command `bash# git` and see what you come up with. If it says command not found you'll need to head off and install the git client on your RaspberryPi.
  - Install git on the Raspberry Pi using the following commands. This should get you all the git binaries you need to get up and running.
    > `bash# apt-get install git-svn`
  - Personally i do not have access to a Mac so i can't really comment on the clients for git. But since the Mac is based on the BSD style unix operating system i would be surprised if there weren't packages available for the Mac.
  - On windows you might consider downloading some of the free or commercial git clients available. See the following link for options - https://git-scm.com/download/gui/windows
  - Use of the windows based client is out of scope on this tutorial. Personally i can't stand the windows gui or the windows client for purposes of "development". It's way too inefficient when it comes to writing or managing code. You can look at youtube or google and am sure you'll find tutorials that others might have created for the Windows git client. 

#### Cloning An Existing Repo (An easy way to get started) 
  - Once you've created your new repo at github.com you are now ready to clone the repo locally on your RaspberryPi, Desktop, Laptop, etc. Cloning (download) is required if you intend to work on the repo remotely, make changes and have them synced up with the main repo.
  - Head over to the new repo directory within your github account. Click on the "Clone or Download" option. This will provide you with a link which will end with a .git. Note down this URL, we'll need it for the next step. 
  - As an example head over to my repo at http://github.com/tangowhisky37/RaspiPythonProjects/
  - Click on the "Clone or Download" option and you'll see the following URL, "https://github.com/tangowhisky37/RaspiPythonProjects.git"
  - If you were to clone this repo you would need to copy this URL to the machine where you wanted to clone (Download) the repo.
  - Open up a prompt on the target host and issue the following commands. Use the URL you've obtained above.
  > `bash# git clone <URL>` 

#### Git local configuration 
  - Before you can use git you have to setup a few local variables on your machines
  - The following commands setup your local user name and user email for git to reference. 
  - You can refer to the documentation for additional configuration options. 
  > `bash# git config --global user.name "John Doe"`

  > `bash# git config --global user.email "john.doe@doe.com"` 

  > `bash# git config --system core.editor vim`

  > `bash# git config --global credential.helper "cache --timeout=3600"`

#### Adding Newly Created Files To A Repo
  - So you'll now perform all your development inside the new folder.
  - You are free to copy content from other folders you might have locally which you want to sync up into the repo.
  - To add a new file to a repo issue the following commands - 
    > `bash# git add filename.txt`
  - You can also add whole folders, subfolders and files by issuing the following command - 
    > `bash# git add *`

#### Checking Status of Code 
  - When developing code on your machine you might need to check the status of existing or previous commits to understand what's gone into the repo and what might have not already been committed to the repo. 
  - To check status just issue the following command while still in the folder which includes the changes you've just made -
    > `bash# git status`
  - The above command will tell you what files have changed, which of the changed files you've added (using git add) and which ones have been left out.

#### Performing A Commit
  - By issuing the commit you are finalizing the changes and providing comments on what they consist of
  > `bash# git commit -m "These updates include fixes the way the files are copied onto AWS S3"`

#### Checking  Files & Folders Into The Repo3
  - Finally check the files into the repo using the following command -
    > `bash# git push --set-upstream origin master`
  - You will be asked for your github account details. Once you've provided them the code will by pushed into the main repo.
  
#### Pulling updates from your github repo into local repo
  - There will be times where someone else might make changes that have synced up with your repo
  - Or you might have made changes using the web interface and now want to pull the updates down to your local machine. 
  - Issue the following commands in the folder where you had cloned the repo earlier - 
    > `bash# git pull`

#### Creating A New Repo (Remotely) & Pushing Content to Github
  - I have intentionally kept this at the end to keep things simple for you. The easiest way to get started is as mentiond at the start of the tutorial i.e. create a repo online at github.com and then clone the repository to your local development environment wherever it might be located. 
  - In this section we'll look at creating a repo remotely (assumng you do not have a repo with the same name at github.com) and then setting up the repo such that it syncs up as a new repo at github.com.
  - Create a new directory and change paths into that directory
  - Issue the following command there, 
    > `bash# git init`
  - Go about the development activity you need to perform, create your new files and folders here. If you have content from other projects you wanted to copy over do that. 
  - Once you are ready to commit your files issue the following commands - 
      > `bash# add filename.txt` 
    - Or if you want to add entire folders issue the following command, 
      > `bash# git add *`
    - Issue the following command to commit your code -
      > `bash# git commit -m "what changes are you commiting in this release"`
  - Now that you've done all of the above it's time to create a new repository at Github. Refer to the, "Account Creation" steps above.
  - Once you've created a new github.com repository it's time to configure this new repo on your remote machine where you are currently performing your development tasks. 
  - Issue the command provided below to confiugure the repo to push the code to. With your new repo now configured at the remote development location you are now ready to push the comitted code to github.com.
    > `bash# git remote add origin https://github.com/username/you_new_repo`
  - Issue the following command to push the code out,
    > `bash# git push -u origin master`.
  - Now head over to github.com and check your new repo to see if the code you've just committed shows up there. 

#### Remove Files That You've Just Added (for a commit)
  - We all make mistakes, who doesn't. So if you've just added a file or files using "git add" you can undo that with the following command.
    > `bash# git reset <filename>`
  - If you want to delete all of the files you've just added use the following command.
    > `bash# git reset`
  - To check whether all the files are no longer being considered by git for commit using the status command as follows.
    > `bash# git status`

### Deleting Files and Folders from your Repository
  - There are times when you'll move folders around and then need to delete the older content from your repo. Git doesn't automatically delete the older content even though you've renamed the files.
  - You might also want to delete a file for a particular reason. Deleting it from disk is simple. Just issue your normal linux command as follows - 
    > `bash# rm -fr ./<foldername>` 
  - Or the following command if you are just deleting a file on linux - 
    > `bash# rm <filename>`
  - On the first command PLEASE make sure you have no space between the ./ and <foldername> else you'll delete all the contents of your folder and everything inside it. Don't tell me I didn't warn you.
  - Once you've done the above the files are now deleted from your file system. However if you run the status command (see below) you'll notice that the deleted files or/and folders show up in red and not green (means marked as part of the commit). 
    > `bash# git status`
  - To get rid of the deleted files and/or folders from your git repo issue the following command - 
    > `bash# git add -u .`
  - To see if the files are now marked for deletion issue the following status command - 
    > `bash# git status`
  - The result of the above command should depict all the files you've just deleted as marked in "green" for deletion. Once you issue the commit and push commands git will make the changes on your master repo.

#### Additional Reading
  - For additional reading please visit - 
    - kbroman.org/github_tutorial/
    - www.atlassian.com/git/tutorials/ 
    - www.tutorialspoint.com/git/index.htm
    - codeacademy/com/learn/learn-git

Would highly recommend that you take one of the online git tutorials to dig into the details of git. This tutorial was put together to help out a few folk get started. It might or might not be what you are looking for. 


