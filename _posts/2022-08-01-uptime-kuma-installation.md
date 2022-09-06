---
title: How to Install Uptime Kuma
date: 2022-08-01 00:00:02:00 -500
categories: [docker, containers]
tags: [docker, uptime, monitoring, linux]
---

Uptime Kuma is a self-hosted, open-source, fancy uptime monitoring, and alerting system. It can monitor HTTP, HTTP with keywords, TCP, Ping, and even DNS systems.

## Install the Uptime Kuma (Docker)

> You must have Docker installed on the host, a tutorial is available for that [here](https://docs.wzernikow.com/posts/docker-installation/)
{: .prompt-warning }

Create a volume in Docker

```bash
docker volume create uptime-kuma
```

Install the Uptime Kuma container

```bash
docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1
```

Then, browse to
`http://server-ip:3001`

Once you have landed on the Uptime Kuma dashboard, you can start adding your monitors. Below is an example of a 'Ping' (ICMP)-based uptime monitor

![App Templates URL](https://cdn.lansec.net/wzernikow/docs/uptime-kuma-installation/image1.png)

There are many more options to pick from when it comes to choosing how you monitor your services and devices. Another monitor I suggest is the 'TCP Port' monitor. This is especially useful when hosting things such as a Minecraft Server. You can set the TCP Port Monitor to query the server port (25565 by default for Minecraft) and thus monitor the uptime of your Minecraft Server instance.
