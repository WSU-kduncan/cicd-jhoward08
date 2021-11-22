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