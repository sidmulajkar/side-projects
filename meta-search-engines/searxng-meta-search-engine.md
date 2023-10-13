 SearXNG is a free internet metasearch engine which aggregates results from various search services and databases. Users are neither tracked nor profiled as we are hosting it.
 
 > This meta search can be hosted on cloud or on raspberrypi or simple VM Instances as well using docker
 
 1. Install docker and docker-compose
 
 > For ubuntu, mint and debian users
 
 ```
 sudo apt update
 sudo apt install docker.io
 sudo apt install docker-compose
 
 or
 
 sudo dnf install docker
 sudo dnf install docker-compose
 ```
 
 > For arch users
 ```
 sudo pacman -Syu
 sudo pacman -S docker
 sudo pacman -S docker-compose
 ```
 
 2. After Installing the docker and docker compose as well
 
 ```
mkdir searchengine
cd searchengine
export PORT=8080
docker pull searxng/searxng
docker run --rm \
             -d -p ${PORT}:8080 \
             -v "${PWD}/searxng:/etc/searxng" \
             -e "BASE_URL=http://localhost:$PORT/" \
             -e "INSTANCE_NAME=my-instance" \
             searxng/searxng
```

3. Open your web browser and visit the URL and modify the settings as required:

> http://localhost:8080

![Searxng Image](https://www.maketecheasier.com/assets/uploads/2022/06/searxng-install-00-featured-image-800x400.jpg.webp)


> Or just want to use Online Searxng Instances hosted by other people: https://searx.space/

I personally don't recommend it.