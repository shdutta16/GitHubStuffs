# GitHub Stuffs

## Uploading a repo from existing code-setup
1. First create empty repo in git
2. From the root directory of the code-setup initialize git: `git init`
3. Create a `README.md` file and then add that: `git add README.md`
4. Commit the changes: `git commit -m "Added README"`
5. Add remote: `git remote add <remote-name-in-local (symbolic name)> <actual-remote-location (url)>`
   For example: `git remote add MonoHiggsToGG git@github.com:shdutta16/MonoHiggsToGG.git`
7. Check remote: `git remote -v`
8. Check status: `git status`
9. Push the changes: `git push <symbolic-name> <branch-name>`
   For example: `git push MonoHiggsToGG main`
10. Check the repo whether the `README.md` file shows up or not. If it's there then you are all set. If not then you are doomed with google search and stuffs. 
11. Add the files to the repo: `git add <file/directory>`
12. Commit the changes: `git commit -m "<comments>"`
13. Push the changes : `git push <symbolic-name> <branch-name>`

Whenever you make changes to the README file or any other file in remote through the browser, do a `git pull <symbolic> <branch-name>` in the local repo area to sync those changes with the local repo. Also, you are encouraged to git pull first, before making any local changes and pushing them. 


## ERROR 1
error: src refspec main does not match any.

This error means that the remote branch doesn't exist (at least this is the reason because of which I faced this error). The solution was to `checkout` to the proper branch and then `push` the changes. For more details go to [link](https://www.freecodecamp.org/news/error-src-refspec-master-does-not-match-any-how-to-fix-in-git/)
