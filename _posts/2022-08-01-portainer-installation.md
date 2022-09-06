---
title: How to Install Portainer CE
date: 2022-08-01 00:00:01:00 -500
categories: [docker, portainer]
tags: [docker, portainer, containers, linux]
---

Portainer Community Edition is a powerful, open source toolset that allows you to easily build and manage containers in Docker, Docker Swarm, Kubernetes and Azure ACI.

Portainer hides the complexity of managing containers behind an easy-to-use UI. By removing the need to use the CLI, write YAML or understand manifests. Portainer makes deploying apps and troubleshooting problems so easy that anyone can do it.

## Install the Portainer Server (HTTP only)

> You must have Docker installed on the host, a tutorial is available for that [here](https://docs.wzernikow.com/posts/docker-installation/)
{: .prompt-warning }

First, create the volume that Portainer Server will use to store its database:

```bash
docker volume create portainer_data
```

Then, download and install the Portainer Server container:

```bash
docker run -d -p 8000:8000 -p 9000:9000 --name portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    portainer/portainer-ce:latest
```

Now that the installation is complete, you can log into your Portainer Server instance by opening a web browser and going to:

```
http://server-ip:9000
```

## Install the Portainer Server (with HTTPS)

By default, Portainer generates and uses a self-signed SSL certificate to secure port 9443. You can provide your own certificate by using the following install script instead

Again, we will first create the volume that Portainer Server will use to store its database:

```bash
docker volume create portainer_data
```

Then, download and install the Portainer Server container:

```bash
docker run -d -p 9443:9443 -p 8000:8000 \
    --name portainer --restart always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    -v /path/to/your/certs:/certs \
    portainer/portainer-ce:latest \
    --sslcert /certs/portainer.crt \
    --sslkey /certs/portainer.key
```

Now that the installation is complete, you can log into your Portainer Server instance by opening a web browser and going to:

```
https://server-ip:9443
```

## Import my App Templates List

If you would like access to a bunch of templates to install many of the most common apps, then follow the next few steps to import my list to your Portainer Instance.

Log in to your Portainer web-interface and head to the settings. Find the menu shown in the image below...
![App Templates URL](https://cdn.lansec.net/wzernikow/docs/portainer-installation/image1.png)

Paste the following URL into the URL field

```
https://cdn.lansec.net/dist/portainer/templates.json
```

Now if you go to the Templates menu found in the navigation bar, you will be able to install from over one-hundred app templates!
