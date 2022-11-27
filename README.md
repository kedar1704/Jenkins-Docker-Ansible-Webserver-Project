# Jenkins-Docker-Ansible-Project

So basically in this project we have first created 2 servers on EC2 instances. Then we named one of them as mainserver and another one as webserver.

In mainserver we have installed jenkins,ansible,git,docker

And in webserver we have deployed docker

Our aim for the project is to integrate ansible with jenkins and push the image to dockerhub and then pull the image from dockerhub into webserver and run it there.

We have used Ansible plugin to ssh into our webserver.


