# Project_06 - CICD
----------------------------------
1. Get the Github repository.
* In Pilot, there is a link to go to. It looks like the one below:
![gitLink](Pictures/gitLink.jpg)
* Once attached to the repo, choose the medium in which the user will complete the website.
  I have chosen to use my first instance from lab_01 since WSL gives errors about docker.io.
2. Clone the NEW repo.
* Below is the screenshot from my repo clone.
![cloneCICD](Pictures/cloneCICD.jpg)
----------------------------------
3. Get Docker
* Now, one thing to do is to login to the instance which is self explanitory by now. Next the
  user will have to install docker and docker.io. Docker is the program and docker.io allows 
  the uplink to the docker repository for the images to download. . . (I THINK?!?).
![updateAndInstall](Pictures/updateAndInstall.jpg)
* It is always best to make sure that any executable or serivce is running after installation.
![dockerRunning](Pictures/dockerRunning.jpg)
----------------------------------
4. Get a webpage or splashpage
* Create a basic HTML file to replace the old "index.html" file that apache2 makes in "/usr/local/apache2/htdocs/"
![simpleHTML](Pictures/simpleHTML.jpg)
----------------------------------
5. Pull an image and build.
* From what I know about building an image, you usually need some type of base to lay the rest
  on. This is usually a OS like Ubuntu or a different flavor, but we are going to use "httpd".
  ![dockerPull](Pictures/dockerPull.jpg)
* Now the DOCKERFILE. . .The dockerfile is basically a list of commands that will build the image
  of whatever you need the container to do. It can look like the one below:
  ![dockerfile](Pictures/dockerfile.jpg)
* In my dockerfile it should copy the index.html into "/usr/local/apache2/htdocs/" folder after installing Apache2.
* Below is the readout:
![dockerBuild](Pictures/dockerBuild.jpg)
----------------------------------
6. Run the container.
* After a successful build, use the "sudo docker image ls" to verify that the image is actually there.
![dockerImageRepo](Pictures/dockerImageRepo.jpg)
* Now that it is verified, we can test to see if the image actually does what we need it to do.
* I had issues trying to run the command below due to login issues with Docker, so I went ahead and 
  logged in using "sudo docker login", input my username and password, then ran the command below.
  Using "sudo docker run -d -p 8080:80 web1:Project6" you should see a hash printout meaning the container 
  is running.
* Now if you curl "localhost:8080, then the spashpage should showup like mine below:
![mySplash](Pictures/mySpash.jpg)
----------------------------------
7. Setup a DockerHub account
* Go to https://hub.docker.com/ and the user should see the page below:
![dockerhub](Pictures/dockerhub.jpg)
* Enter in an id email and password, then verify the users account by going into the email from Docker.
* After creating an account and logging in, you should see the following:
![mydocker](Pictures/mydocker.jpg)
----------------------------------
8. Create a DockerHub Repository
* To create a DockerHub repo, the user needs to click on the "create repository" button located near the top 
  right of the screen.
![createButton](Pictures/createButton.jpg)
* The user will then see the page below:
![createInfo](Pictures/createInfo.jpg)
* Fill in the name, description and keep it public since this is for Project_06 and click "create". The user's 
  page will look like mine below:
![myRepo](Pictures/myRepo.jpg)
----------------------------------
9. Create GitHub secrets for Docker Credentials
* In the user's repository, there is a settings widget that looks like a gear, click it and navigate down to 
  the secrets tab.
![githubSecrets](Pictures/githubSecrets.jpg)
* Click the button "New repository secret".
![newSecret](Pictures/newSecret.jpg)
* Fill in the next pages textboxes with the necessary information. This information will be the user's "DOCKER_USERNAME" 
  for the name and then the user's Docker username, then the user's "DOCKER_PASSWORD" etc.
![secretInfo](Pictures/secretInfo.jpg)
* And click the "Add secret" button. Below is my secrets from the top level:
![mySecret](Pictures/mySecret.jpg)
----------------------------------
10. Configure GitHub Workflow
* Go to https://docs.github.com/en/actions/guides/publishing-docker-images#publishing-images-to-docker-hub to get the 
  template for the workflow.
* The first template has the information required to pull the image "index.html" from the cicd-github repo. It will then
  use the credentials that were made in the github repository's secrets to login to Docker. Things will need to be changed 
  in order to make the workflow do the actions for the user's job.
![githubWorkflow](Pictures/githubWorkflow.jpg)
* The things that will need to be changed are ***********