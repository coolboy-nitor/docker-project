 **docker-project Git commands**

git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/coolboy-nitor/docker-project.git
git push -u origin main


if your SSH key is either not set up, not added to the SSH agent, or not added to your GitHub account.


Use HTTPS Instead of SSH (If You Prefer Simpler Setup)

If you don’t want to set up SSH, you can switch your remote to HTTPS:

git remote set-url origin https://github.com/coolboy-nitor/docker-project.git


Then try:

git push -u origin main
