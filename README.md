# SWBProcess-providers
Vagrant and docker files to easily deploy SWBProcess

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
