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

created a docker file with all instructions 

run docker file using  docker build . command

to check image is build or not use docker images ls command.

Now docker run command

application will run inside container we can access this inside container but with localhost it will give error because we haven't yet expose port to outside world to access our application lets do this

 docker run -p 3000:3000 941e8c1a53a1    # this is how we bind 3000 port to outside world or we can say we expose 3000 port to outside world. so that everyone can access our application.

 to run container in detach mode 
 docker run -d -p 3000:3000 941e8c1a53a1  

to create multiple containers from single image we have to use different ports
docker run -d -p 3001:3000 941e8c1a53a1  
docker run -d -p 3002:3000 941e8c1a53a1 

if we use the same port then 3000:3000 we will get an error



so when we create multiple containers we have to manually shutdown stoped containers so what if
when we stop container it should automatically gets removed. cool 
so that we use this command

docker run -d --rm -p 3002:3000 941e8c1a53a1 

To create custom name container 
docker run -d --rm --name "mywebapp" -p 3002:3000 941e8c1a53a1 

to stop container 

docker stop "container_name"

to tag a name to image we use 
docker build -t mywebapp:02 .

to delete docker image 

when we update our application we create new container and exicute the command this will reflect
all the new changes in our application. This is used to maintain the versions of your application
docker run -d --rm --name "mywebapp" -p 3002:3000 mywebapp:03


'predefined images':
python image ---->  docker pull python
nginx image -----> docker pull nginx   #default port 80

'interactive mode with terminal'

here docker run 'image id' will fail so we have to use 
docker run -it 'image id' 
with this command user can interact enter 1st no and 2nd num to get total.

'Sharing images Dockerhub'

login using any id on dockerhub 
in free tier you are allowed to create only 1 public and private repository 
click on create repository
enter name of image give one short description
then you will see repo and command like : docker pull coolboynitor/docker-project:02
then go to vs code terminal and run this command 
but in vs code we don't have our image name as docker assign random names 

1. so change the name of the image with this command:
docker tag mywebapp:03 coolboynitor/docker-project:02

2. or build new image with :
docker build -t coolboynitor/docker-project:02

'Using our image remotely pull images':
docker pull coolboynitor/docker-project:02
we can pull our image and run it on any system this is the beauty of docker.
eg. tester can test the application

'understand docker volumes':

docker run -it --rm -v myvolumne:/myapp/ image_id
docker volume --help
docker volume inspect myvolume

'What are bind mounts'

lets say we have servers.txt file and we want changes to get reflect while we delete or add server list in servers.txt file. use command

we are doing changes in external file but till after running our application using docker we are able to see those changes
here we are not creating volumen we are just using our external file.

docker run -v 'absolute_path_of_servers.txt' :/myapp/servers.txt --rm 'image_id'

'What is .dockerignore '

we don't want to copy unecessory files.
create .dockerignore file in the same location where Dockerfile is present
and add the files which you dont want to copy eg. Dockerfile, .git, .env  etc

'Communication From/To Containers'

1. container python application depends on -----> website though API service.
2. container python application depends on -----> local database on your machine'
3. container python application depends on -----> container database (container to container connection)

'Working with API'

RUN pip install requests

'Communication container & local DB'


