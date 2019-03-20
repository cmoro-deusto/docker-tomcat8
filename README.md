docker-tomcat
=============


[![](https://images.microbadger.com/badges/version/dordoka/tomcat.svg)](http://microbadger.com/images/dordoka/tomcat "Get your own version badge on microbadger.com")

[![](https://images.microbadger.com/badges/image/dordoka/tomcat.svg)](http://microbadger.com/images/dordoka/tomcat "Get your own image badge on microbadger.com")


[![dockeri.co](http://dockeri.co/image/dordoka/tomcat)](https://registry.hub.docker.com/u/dordoka/tomcat/)

Ubuntu 14.04/16.04, Oracle JDK 8 and Tomcat 8 based docker container.

# Description
You should run this container in the background and mount the volume with your web app inside.

Includes:

 - Oracle JDK 1.8u201
 - Tomcat 8.0.53
 - Git, wget, curl, build-essential
 
The ```latest``` tag is based on Ubuntu 14.04. Should you prefer Ubuntu 16.04, please use the ```xenial``` tag.

There's also a ```tomcat8.5``` tag, which includes:

  - Ubuntu 16.04 Xenial based only
  - Oracle JDK 1.8u201
  - Tomcat 8.5.39
  - Git, wget, curl, build-essential

## Volumes
Exports a volume on `/opt/tomcat/webapps`.
You can mount the volume on run to a local directory containing your war file or exploded war directory.
If you need the management app, remember to have a copy on your hosts volume mount point.

## Ports
Two ports are exposed:

 - 8080: default Tomcat port.
  
 - 8009: default Tomcat debug port.

Remember to map the ports to the docker host on run.


# How to run the container
## Using docker
You need docker v1.3+ installed. To get the container up and running, run:
 
```
sudo docker run -d -p 8080:8080 -p 8009:8009 -v /opt/tomcat/webapps:/opt/tomcat/webapps dordoka/tomcat
```
Remember to change `/opt/tomcat/webapps` to the directory where your app is stored.

If you prefer the Ubuntu 16.04 based image instead of the default 14.04 one, just use the ```xenial``` tag:

```
sudo docker run -d -p 8080:8080 -p 8009:8009 -v /opt/tomcat/webapps:/opt/tomcat/webapps dordoka/tomcat:xenial
```

## Using docker compose
If you have `docker-compose` installed, you can just launch:

```
sudo docker-compose up
```

## A warning regarding admin user for tomcat management console
Please note that the image contains a `tomcat-users.xml` file, including an `admin` user (password `admin`). For the time being, should you wish to change that, fork this repo and modify the xml file accordingly.

