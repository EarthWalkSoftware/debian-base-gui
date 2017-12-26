## debian-base-gui
*EarthWalkSoftware/debian-base-gui* builds upon *EarthWalkSoftware/debian-base* to include basic video/gui packages and framework setup.  

A docker image of *EarthWalkSoftware/debian-base-gui* is available from *EarthWalkSoftware* at *Docker Hub*:

  https://hub.docker.com/r/earthwalksoftware/debian-base-gui/

______
### Packages
Among the additional packages are 
- *dbus-x11*
- *dmz-cursor-theme*
- *file*
- *fonts-dejavu*
- *fonts-liberation*
- *hicolor-icon-theme*
- *libdbus-glib-1-2*
- *libglib2.0*
- *libstdc++6*
- *libx11-xcb-dev*
- *libx11-xcb1*
- *libxrender1*
- *libxt6*
- *xauth*
- *xz-utils*

______
### Docker RUN options

#### Environment variables

- *DISPLAY* - Used to set the system display to use. Normally, set to
    -e DISPLAY=unix${DISPLAY}

#### Volumes

- *X11-unix* - maps the *docker container*'s to the *docker host*'s X11 driver. Normally set to  

    -v /tmp/.X11-unix:/tmp/.X11-unix  

- *docker.xauth* - maps the docker container's to the docker host's xauth file.  Normally set to  

    -v /tmp/.docker.xauth:/tmp/.docker.xauth  

- *.Xauthority* - maps the  docker container's .Xauthority file to the docker host's .Xauthority file.  Normally set to  

    -v ${HOME}/.Xauthority:${HOME}/.Xauthority  

- *localtime* - (optional) maps the docker container localtime file to the docker host's localtime file.  Normally set to 

    -v /etc/localtime:/etc/localtime:ro

______
### Creating a container


    docker run -it \
               -e DISPLAY=unix${DISPLAY} \
               -v /tmp/.X11-unix:/tmp/.X11-unix \
               -v /tmp/.docker.xauth:/tmp/.docker.xauth \
               -v ${HOME}/.Xauthority:${HOME}/.Xauthority \
               -v /etc/localtime:/etc/localtime:ro \
               --rm \
               --name=gui \
           debian-base-gui:9.2 /bin/bash  



### locale
The following locale is automatically created in the image:

    locale-gen en_US
    update-locale LANG=C.UTF-8 LC_MESSAGES=POSIX  
  
This setting may be changed in the Dockerfile (using the RUN command) when building a new container from the *EarthWalkSoftware/debian-base* image, 

------
### Licensed by Academic Free License v 3.0

Read the license at https://github.com/EarthWalkSoftware/docker-alpine-htop/wiki/License

Any conflict between the terms of the *Academic Free License v 3.0* and the terms of any license provided by *nimmis/docker-ubuntu*, the terms of the *nimmis/docker-ubuntu* license shall prevail.
