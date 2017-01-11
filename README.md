# SWBProcess-providers
Vagrant and docker files to easily deploy SWBProcess 4.5.11.2 using Apache Tomcat 9.0.0.M15 and Oracle JDK 8.

# Docker usage

Build docker image
````sh
cd Docker
docker build -t haxdai/swbprocess .
````

Start new container
````sh
docker run -it -d -p 8080:8080 haxdai/swbprocess
````

Stop container
````sh
docker stop <CONTAINER_ID>
````

Restart container
````sh
docker start <CONTAINER_ID>
````
