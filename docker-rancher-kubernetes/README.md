# Docker, Rancher, Kubernetes... Minecraft? (Setup and Install Tutorial)

[![Docker, Rancher, Kubernetes... Minecraft? (Setup and Install Tutorial)](http://img.youtube.com/vi/oILc0ywDVTk/0.jpg)](https://www.youtube.com/watch?v=oILc0ywDVTk "Docker, Rancher, Kubernetes... Minecraft? (Setup and Install Tutorial)")


If you want to set up Kubernetes at home using Rancher to run Docker containers, this is the guide for you. This is a step by step tutorial of how to install and configure Rancher, Docker, and Kubernetes for your homelab.  In this video we set up and configure a Minecraft server in just a matter of minutes with some enterprise like features.  You can use this same process to spin up other Docker containers at home on your server or desktop.


## Install Docker

Get the current Rancher provided Docker instal CURL command from:

   https://rancher.com/docs/rancher/v2.x/en/installation/requirements/installing-docker/
   
If you would like to use Docker as a non-root user, you should now consider adding your user to the "docker" group with something like:

  `sudo usermod -aG docker USER_NAME`

Remember that you will have to log out and back in for this to take effect!

WARNING: Adding a user to the "docker" group will grant the ability to run
         containers which can be used to obtain root privileges on the
         docker host.
         Refer to https://docs.docker.com/engine/security/security/#docker-daemon-attack-surface
         for more information.


## Install Rancher
You'll want to use a command similar to this so that there aren't any port conflicts with other services or kubernetes itself.

Also, you may want to consider pinning your docker tag to a version other than `latest` to make backing up and upgrading easier. See [here](https://hub.docker.com/r/rancher/rancher/tags) for the latest version.

`docker run -d --restart=unless-stopped -p 9090:80 -p 9091:443 --privileged -v /opt/rancher:/var/lib/rancher --name=rancher_docker_server rancher/rancher:latest`

Example alternate tag: (You probably want to use the above link to ensure the latest version)

`docker run -d --restart=unless-stopped -p 9090:80 -p 9091:443 --privileged -v /opt/rancher:/var/lib/rancher --name=rancher_docker_server rancher/rancher:v2.5-f240f4b0a471af8cacf07470f27cdbf609ee8212-linux-amd64`

You can access Rancher using port 9091:

Example: `https:192.168.0.221:9091`

## Troubleshooting

* Make sure you have a static IP on your Rancher host
* Be sure to use the ports above if you want to add SSL later and use commands in future videos
