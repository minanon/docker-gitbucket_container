#docker-gitbucket_container
This container has Gitbucket package and data directory.

##Introduction
This container is used by a Tomcat container. It has only Gitbucket package and data directory.

##Gitbucket
- [Gitbucket](https://github.com/takezoe/gitbucket)

##Gitbucket Version
3.0

##Maintainer
minanon

##Source Link
- [Dockerfile](https://github.com/minanon/docker-gitbucket_container)
- [Docker registry](https://registry.hub.docker.com/u/minanon/gitbucket_container/)

##Exposed directory

|Package Directory                  |Data Directory|
|---                                |---               |
|/usr/local/tomcat/webapps/gitbucket|/opt/gitbucket    |

##Build

    docker build -t minanon/gitbucket_container .

##Start Container
I recommend to save Data on host.
This container will finish soon because it is the purpose of supply package and retention data.

    docker run -d --name gitbucket_container -v /opt/docker/data/gitbucket:/opt/gitbucket minanon/gitbucket_container

##Usage
Please start Tomcat container with this container.
It will start Gitbucket automatically.

    docker run -p 8080:8080 -td --volumes-from gitbucket_container tomcat

You will be able to access Gitbucket from following URL.
http://localhost:8080/gitbucket
