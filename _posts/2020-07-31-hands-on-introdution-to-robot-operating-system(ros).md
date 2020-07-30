---
date: 2020-07-31 04:51:19
layout: post
title: "Hands-On Introdution to Robot Operating System(ROS)"
subtitle:
description: This article describes how to install and explains ROS Packages, ROS Nodes, ROS Topics, ROS Messages, ROS service, ROS Publishers and Subscribers, and Basic ROS GUI tools. The programming language used in this article is Python. 
image:
optimized_image:
category:
tags:
author:
paginate: false
---

Wikipedia defines [Robot](https://en.wikipedia.org/wiki/Robot) as a machine capable of carrying out a complex series of actions automatically. The advantages and importance of Robots are contentious, the robotics field is evolving every day and the benefits of robots are becoming inevitable. This article is not meant to discuss the advantages of robots, but to get you started with ROS(Robot Operating System).

This article describes how to install and explains ROS Packages, ROS Nodes, ROS Topics, ROS Messages, ROS service, ROS Publishers and Subscribers, and Basic ROS GUI tools. The programming language used in this article is Python. 

## [What is Robot Operating System(ROS)](http://wiki.ros.org/ROS/Introduction)

It is an open-source meta operating system or a middleware used in programming Robots. It consists of packages, software,  building tools for distributed computing, architecture for distributed communication between machines and applications. It also provides tools and libraries for obtaining, building, writing, and running code across multiple computers. It can be programmed using python, c++, and lisp.  

## ROS vs Framework vs OS(Operating System)
Operating System(OS) manages communication between computer software and hardware. In the process of managing this communication, it allocates resources like the central processing unit(CPU), memory, and storage. Examples are windows, Linux, android, mac OS, etc 

[Framework](https://en.wikipedia.org/wiki/Software_framework) in computer programming, a software framework is an abstraction in which software providing generic functionality can be selectively changed by additional user-written code, thus providing application-specific software. Software frameworks may include support programs, compilers, code libraries, tool sets, and application programming interfaces(APIs) that bring together all the different components to enable the development of a project or system. Examples are Django, Laravel, Tensorflow, Flutter, etc 

Robot Operating System(ROS) is not a full flesh operating system, it is a “meta operating system”, it is built on top of a full operating system. It is called an OS because it also provides the services you would expect from an operating system, including hardware abstraction, low-level device control, implementation of commonly-used functionality, message-passing between processes, and package management. It is a series of packages that can be installed on a full operating system like Ubuntu. 

## ROS level of concepts 
<b>Filesystem level</b> - these are resources located on the disk, for example, packages, package manifests (package.xml), repositories, messages types, service types, etc.

<b>Computation level</b>  - these involve the communications between peer to peer networks of ROS, examples are nodes, master, parameter server, messages, topics, services, bags.
 
<b>Community level</b>  - these involve the exchange of software and knowledge between members of the community. Examples are [distributions]( http://wiki.ros.org/Distributions), [repositories](http://wiki.ros.org/Repositories), [ROS wiki](http://wiki.ros.org/).

[Catkin vs Rosbuild](http://wiki.ros.org/catkin/conceptual_overview)
Catkin is the new build system(generate executable files from source files) for ROS while rosbuild was the build system used in the past. Catkin uses CMake more cleanly and only enhances CMake where it falls short on features, while rosbuild uses CMake but invokes it from Makefiles and builds each package separately and in-source. Catkin was designed to be more conventional than rosbuild, allowing for better distribution of packages, better cross-compiling support, and better portability.




