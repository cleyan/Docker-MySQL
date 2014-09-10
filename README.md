Created by Kaushal Kishore <br>
Email : kaushal.rahuljaiswal@gmail.com<br>
Website : http://www.kaushalkishore.com<br>

<h2>Dockerfile for creating docker image for MySQL-5.5</h2>

<h4>Steps for creating image from the Docker-MySQL:</h4>

<b>Step 1 :</b> Clone the Docker-MySQL.git
<pre>
<b>Command: </b>
git clone https://github.com/kaushalkishorejaiswal/Docker-MySQL.git
</pre>

<b>Step 2 :</b> Change the directory to the clone folder
<pre>
<b>Command:</b>
cd Docker-MySQL
</pre>

<b>Step 3 :</b> Create the Docker Image
<pre>
<b>Command: </b>
sudo docker build -t ##NAME_OF_YOUR_DOCKER_IMAGE## .
</pre>

<pre>
<b>Note : </b>
  a). This command will be fired where the DockerFile will be placed
  b). ##NAME_OF_YOUR_DOCKER_IMAGE## : Replace it with your image name
  c). . : (.) Symbols shows that your Dockerfile is available on the same directory where you are running the command.
</pre>

<b>Step 4 :</b> Create an MySQL Installed Container from the image
<pre>
<b>Command Syntax: </b>
sudo docker run --name [container name] -p [port to access (New Port):port exposed(original port)] -i -t [image name]
</pre>
<pre>
<b>Command:</b>
sudo docker run --name ##NAME_OF_YOUR_DOCKER_CONTAINER## -d -p 3311:3306 ##NAME_OF_YOUR_DOCKER_IMAGE##
</pre>
<pre>
<b>Example:</b>
sudo docker run --name MySQL5.5_Container -d -p 3311:3306 kaushal_mysql
<b>Here</b>
<ul>
  <li>MySQL5.5_Container : Is the name of my container, which will be displayed on running of docker ps -a</li>
  <li>3311 : Is the port where the docker container is running on host machine</li>
  <li>3306 : Is the exposed port</li>
  <li>kaushal_mysql : Is the name of our docker image</li>
</ul>
</pre>


<b>Step 5 :</b> Now you can access your MySQL container from your CLI.
<pre>
<b>Command:</b>
mysql -uroot -proot -h172.17.42.1 -P3311
</pre>

<h4>Some other important commands:</h4>
<ul>
<li><b>docker images :</b> To list all the images of your docker</li>
<li><b>docker ps :</b> To list all the runing containers</li>
<li><b>docker kill ##CONTAINER_NAME## :</b> To kill the runing container</li>
<li><b>docker rm ##CONTAINER_NAME## :</b> To delete the container from the system.</li>
<li><b>docker inspect ##CONTAINER_NAME## :</b> To get all the information about the container.</li>
<li><b>docker logs ##CONTAINER_NAME## :</b> To get the logs of the container.</li>
<li><b>docker ps -a:</b> To get the listing of all the containers.</li>
</ul>

<h4>Additional Notes:</h4>
<ul>
  <li>You can run multiple container using single image, but you will have to define a free port and the name for it.</li>
  <li>You can get the Gateway IP and other information of the docker container using the command docker inspect  ##CONTAINER_NAME##</li>
  <li> You can get the container name using the command docker ps -a</li>
  <li>You can use any of the mysql client command inside the docker</li>
</ul>
