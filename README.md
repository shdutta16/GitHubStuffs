# GitHub Stuffs

## Uploading a repo from existing code-setup
1. First create empty repo in git
2. From the root directory of the code-setup initialize git: `git init`
3. Create a `README.md` file and then add that: `git add README.md`
4. Commit the changes: `git commit -m "Added README"`
5. Add remote: `git remote add <remote-name-in-local (remote-name)> <actual-remote-location (url)>`
   For example: `git remote add MonoHiggsToGG git@github.com:shdutta16/MonoHiggsToGG.git`
7. Check remote: `git remote -v`
8. Check status: `git status`
9. Push the changes: `git push <remote-name> <branch-name>`
   For example: `git push MonoHiggsToGG main`
10. Check the repo whether the `README.md` file shows up or not. If it's there then you are all set. If not then you are doomed with google search and stuffs. 
11. Add the files to the repo: `git add <file/directory>`
12. Commit the changes: `git commit -m "<comments>"`
13. Push the changes : `git push <remote-name> <branch-name>`

`<remote-name> = <remote-name>`

Whenever you make changes to the README file or any other file in remote through the browser, do a `git pull <remote-name> <branch-name>` in the local repo area to sync those changes with the local repo. Also, you are encouraged to git pull first, before making any local changes and pushing them. 


## ERROR 1
```
error: src refspec main does not match any.
error: failed to push some refs to 'git@github.com:shdutta16/MonoHiggsToGG.git'
```

This error means that the remote branch doesn't exist (at least this is the reason because of which I faced this error). The solution was to `checkout` to the proper branch and then `push` the changes. For more details go to [link](https://www.freecodecamp.org/news/error-src-refspec-master-does-not-match-any-how-to-fix-in-git/). Another common reason to face this error is when no ```git commit``` is done before pushing the changes. 


## How to's
1. How to check which branch I am on? -> `git branch`
2. How to switch to another branch? -> `git checkout <branch-name>`
3. How to create new branch and switch to it? -> `git checkout -b <branch-name>`
4. How to check remote? `git remote -v`
5. How to delete a file in remote but not locally? 
   ```
   git rm --cached <name of file in remote>
   git commit -m "<comments>"
   git push <remote-name> <branch-name>
   ```
6. How to push contents of local branch to remote branch having different names?
   
   Normally when push is done like `git push origin master`, it means push from the local branch named `master` to the remote
   branch named `master`. To push to a remote branch with a different
   name than the local branch, separate the local and remote names with a `:` like `git push origin <local-branch-name>:<remote-branch-name>`
   
7. How to remove branch both locally and remotely?
   ```
   git branch -d <branch-name>                # to delete branch locally
   git push -d <remote-name> <branch-name>    # to delete branch remotely 
   ```
8. How to add existing remote?
   ```
   git init
   git remote add <remote-name-in-local (remote-name)> <actual-remote-location (url with git@github.com)>
   git remote -v   # Check the remote name
   git status      # Check the status
   git init
   git pull <remote-name> <branch-name>
   ```

9. How to make available .ssh or ssh authentication within singularity for github?
   Inside host do the following:
   ```
   eval "$(ssh-agent -s)"   # Check if ssh agent is active
   ssh-add ~/.ssh/id_ed25519  # Use the key used to clone the main repo
   ```
   While starting container bind the authentication, for example:
   ```
   sudo singularity shell -B $geant_dir:/simulation -B /tmp:/tmp -B $SSH_AUTH_SOCK:$SSH_AUTH_SOCK --env SSH_AUTH_SOCK=$SSH_AUTH_SOCK --containall $container
   ```
   Inside container check the ssh access:
   ```
   ssh-add -l
   ```

10. How to pull a branch along with all the submodules (that appear as links under the branch)?
    ```
    git pull <remote-name> <branch-name> --recurse-submodules
    ```
    
11. How to pull the updated submodule folders, after you have pulled the parent branch?
    ```
    git submodule update --init --recursive
    ```
    
   
      
