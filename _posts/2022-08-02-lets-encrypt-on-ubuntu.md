---
title: How to Get Let's Encrypt SSL on Ubuntu
date: 2022-08-02 00:00:00:00 -500
categories: [website, security]
tags: [security, ssl, lets-encrypt, ubuntu, certificate, https, linux]
---

SSL/TLS encryption is an integral part of the network infrastructure. Any web and mail server allows you to enable data encryption. In this article, we will look at the process of obtaining a free SSL certificate Let's Encrypt.

As initial conditions, you must have a domain name. It's DNS A-record must contain the public address of your server. If the firewall is enabled, open access for HTTP and HTTPS traffic.

```bash
sudo ufw allow 80
sudo ufw allow 443
```

## Installing the "Let's Encrypt" package

The process of installing the "Let's Encrypt" package with all its dependencies is extremely simple. To do this, enter the command:

```bash
sudo apt install letsencrypt
```

Along with the "Let's Encrypt" package, this command also installs the "certbot.timer" utility for automatic certificate renewal. It checks the validity of SSL certificates in the system twice a day and extends those that expire in the next 30 days. To make sure that it is running, enter:

```bash
sudo systemctl status certbot.timer
```

There are different configurations and conditions for obtaining a certificate. Let's look at some of them.

## Standalone server for getting the "Let's Encrypt" SSL certificate

The easiest way to get an ssl certificate is to use a standalone option in Certbot. Replace domain-name.com with your domain name, run the command, and follow the instructions:

```bash
sudo certbot certonly --standalone --agree-tos --preferred-challenges http -d domain-name.com
```

The certonly option means that the certificate will only be obtained without installation on any web server, standalone allows you to start your own web server for authentication, agree-tos means acceptance of the ACME server subscription agreement, which is a prerequisite, and preferred-challenges http means performing authorization using HTTP.

## Automatic installation of the SSL certificate on nginx and Apache web servers

Certbot can automatically install the certificate on nginx and Apache web servers. To do this, you need to install an additional package and choose the appropriate one for your web server.

```bash
sudo apt install python3-certbot-nginx
sudo apt install python3-certbot-apache
```

Run this command for nginx:

```bash
sudo certbot --nginx --agree-tos --preferred-challenges http -d domain-name.com
```

Or this for Apache:

```bash
sudo certbot --apache --agree-tos --preferred-challenges http -d domain-name.com
```

Follow the instructions and Certbot will install an SSL certificate for you.

## "Let's Encrypt" Wildcard SSL certificate

To create a wildcard certificate, the only possible challenge method is DNS. In the d parameter, you must specify both the bare domain and wildcard.

```bash
sudo certbot certonly --manual --agree-tos --preferred-challenges dns -d domain-name.com -d *.domain-name.com
```

After that, place the specified TXT record on your DNS server and click continue.

If everything is well, you will see the path where your new wildcard certificate is stored and some other information.

---

#### Information from serverspace.io
