---
layout: post
title: A Guide to the Linux Firewall
tags: linux how-to
---

When you are trying to set up a new Linux server, dealing with firewalls can get quite overwhelming. Here’s a beginner’s guide to firewalls on Linux.

Traffic into or out of a computer is filtered through "ports," which are relatively arbitrary designations appended to traffic packets destined for use by a particular application.

By convention, some ports are routinely used for particular types of applications. For example, port 80 is generally used for insecure web browsing and port 443 is used for secure web browsing.

Traffic to particular applications can be allowed or blocked by "opening" or "closing" (i.e. filtering) the ports designated for a particular type of traffic. If port 80 is "closed," for example, no (insecure) web browsing will be possible. 

The default firewall configuration tool for Ubuntu is `ufw`. It stands for uncomplicated firewall. Developed to ease iptables firewall configuration, `ufw` provides a user-friendly way to create an IPv4 or IPv6 host-based firewall. By default `ufw` is disabled.

By default, `ufw` will block all of the incoming connections and allow all outbound connections. This means that anyone trying to access your server will not be able to connect unless you specifically open the port, while all applications and services running on your server will be able to access the outside world.

Install Uncomplicated Firewall:

```bash
sudo apt install ufw
```

Allow SSH before enabling the firewall, otherwise you will lock yourself out. 

```bash
sudo ufw allow ssh
```

If SSH is running on a different port than the default 22, use 

```bash
sudo ufw allow 23/tcp
```

Enable Firewall: 

```bash
sudo ufw enable
```

Check status:

```bash
sudo ufw status verbose
```

e.g. If everything worked so far, you will get the following output

```bash
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
22/tcp (v6)                ALLOW IN    Anywhere (v6)
```

Open a specific application protocol on the default port:

```shell
sudo ufw allow http
```

Open a specific port:

```bash
sudo ufw allow 80/tcp
```

Allow connections for an application profile, such as NGINX:

```shell
sudo ufw allow 'Nginx'
```

To check which application profiles are installed, 

```shell
sudo ufw app list
```

Only allow connection from certain IP address:

```shell
sudo ufw allow from 1.2.3.4 (to any port 80)
```

Deny all connections from certain IP address:

```shell
sudo ufw deny from 1.2.3.4 (to any port 80)
```

Delete firewall rules:

```shell
sudo ufw deny 80/tcp
```

or, first get a numbered list of all rules and then delete it:

```shell
sudo ufw status numbered 
sudo ufw delete 3
```

Source: [UFW documentation](https://help.ubuntu.com/community/UFW) 