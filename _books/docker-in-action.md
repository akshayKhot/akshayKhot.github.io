---
layout: post
title: Docker in Action
date: 2020-4-22
imglink: docker_in_action.jpg
---

I have started diving deeper and deeper into Docker. Currently, I am reading "Docker in Action" by Jeffrey Nickoloff and Stephen Kuenzli. It's a very well-written book, in an easy to understand language. I highly recommend reading this book if you want to understand Docker and containers. Here is a brief summary of the first chapter, which gives a detailed introduction to Docker and related technology.

<div class="book">
  <a target="_blank" href="{{site.bookshelf}}/{{ page.imglink }}">
    <img src="{{site.bookshelf}}/{{ page.imglink }}" alt="Docker In Action">
  </a>
</div> 

Using software is complex. Before installation, you have to consider the operating system you’re using, the resources the software requires, what other software is already installed, and what other software it depends on. You need to decide where it should be installed. Then you need to know how to install it.

*Docker* is an open source project for building, shipping, and running programs. It is a command-line program, a background process, and a set of remote services that take a logistical approach to solving common software problems and simplifying your experience installing, running, publishing, and removing software. It accomplishes this by using an operating system technology called *containers*.

Docker isn’t a programming language, and it isn’t a framework for building software. Docker is a tool that helps solve common problems such as installing, removing, upgrading, distributing, trusting, and running software.

Any software run with Docker is run inside a container. Docker uses existing container engines to provide consistent containers built according to best practices. With Docker, users get containers at a much lower cost. Docker doesn’t provide container technology; it hides the complexity of working directly with the container software and turns best practices into reasonable defaults.

Running Docker means running two programs in user space. The first is the Docker engine. If installed properly, this process should always be running. The second is the Docker CLI. This is the Docker program that users interact with.

It’s now possible to run the same software—exactly the same software—on any system. That means your desktop, your development environment, your company’s server, and your company’s cloud can all run the same programs. 

**Containers are not VMs.** They take a long time (often minutes) to create and require significant resource overhead because they run a whole operating system in addition to the software you want to use. 

You can think of a Docker container as a physical shipping container. It’s a box where you store and run an application and all of its dependencies (excluding the running operating system kernel). Containers limit the scope of impact that a program can have on other running programs, the data it can access, and system resources.

Like a crane loading a shipping container onto a ship, the process of installing any software with Docker is identical to any other. The shape or size of the thing inside the shipping container may vary, but the way that the crane picks up the container will always be the same. All the tooling is reusable for any shipping container.

Docker image is a bundled snapshot of all the files that should be available to a program running inside a container. You can create as many containers from an image as you want. Images are the shippable units in the Docker ecosystem.