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

**React & node based testapp is added**

using command:
install node and docker first
app command : 

"npx create-react-app testapp"

testapp folder will be created :
to run app:

cd testapp
"npm start"

node_modules contains all the dependencies required to run our react app
so we do not deploy this instead we delete this and use command :

"node install"

"node start"

so this node_modules will get installed and application will be running.

Now create a Dockerfile in the testapp directory.

install docker extension.

