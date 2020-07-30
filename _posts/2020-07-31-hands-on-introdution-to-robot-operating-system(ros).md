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
**Filesystem level** - these are resources located on the disk, for example, packages, package manifests (package.xml), repositories, messages types, service types, etc.

**Computation level**  - these involve the communications between peer to peer networks of ROS, examples are nodes, master, parameter server, messages, topics, services, bags.
 
**Community level**  - these involve the exchange of software and knowledge between members of the community. Examples are [distributions]( http://wiki.ros.org/Distributions), [repositories](http://wiki.ros.org/Repositories), [ROS wiki](http://wiki.ros.org/).

## [Catkin vs Rosbuild](http://wiki.ros.org/catkin/conceptual_overview)
Catkin is the new build system(generate executable files from source files) for ROS while rosbuild was the build system used in the past. Catkin uses CMake more cleanly and only enhances CMake where it falls short on features, while rosbuild uses CMake but invokes it from Makefiles and builds each package separately and in-source. Catkin was designed to be more conventional than rosbuild, allowing for better distribution of packages, better cross-compiling support, and better portability.

## ROS Distributions, Installation and Folder Structure 
**[ROS distributions](http://wiki.ros.org/Distributions)** are alphabetical, for instance, the last 3 distributions are Lunar Loggerhead, Melodic Morenia, and Noetic Ninjemys. ROS can be officially built on Linux distributions but it also supports other operating systems. In this article use ROS Melodic distribution on Ubuntu 18 Linux distribution. 

**[Installing ROS](http://wiki.ros.org/Installation)**  

```
sudo apt update && sudo apt install ros-melodic-desktop-full
```
You can install other distributions by changing the distribution name, for instance, you can change melodic to noetic but note noetic support Ubuntu Focal Fossa(20.04). This installation install the  full version, you can install smaller versions for instance

```
sudo apt update && sudo apt install ros-melodic-ros-base 
```
This installation does not contain the GUI tools. 

After proper installation, you need to source the ROS setup script. source command reads and executes commands from the file specified as its argument in the current shell environment.

```
source /opt/ros/melodic/setup.bash 
```
To avoid sourcing the setup file when a new terminal is opened, you can add the command to the .bashrc file. it will automatically run when you open a new terminal.

```
echo "/opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

**[Initialize ROS Dependencies](http://wiki.ros.org/rosdep)**

```
sudo rosdep init 
rosdep update
```

Check for proper installation 

```
rosversion -d
```
This command output your ROS distribution

**Folder structure** 

ROS packages are saved in a catkin workspace folder. The package folders are saved in the src folder in the catkin_workspace.


![file_structure](https://placehold.it/800x400 "Large example image")

```
mkdir -p catkin_ws/src
cd catkin_ws/
catkin_make
```
The [catkin_make](http://wiki.ros.org/catkin/commands/catkin_make) command build all packages located in “catkin_ws/src” folder. After running catkin_make command, two new folders “build” and “devel” will be created. Note, you should run catkin_make command when you are in the “catkin_ws” directory. The “build” folder is where CMake and make are invoked, and the devel folder contains any generated files and targets, plus setup.*sh files so that you can use it like it is installed. A CMackeLists.txt file is also created in the src folder( I will explain the function of this file later). 

[ROS PACKAGES](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)

**Ros Package** - contains libraries, executables, scripts, and other artifacts for a specific ROS program. Packages are used for structuring specific programs, files in a package also have a specific structure. A ROS package folder could contain:

**launch folder** - it contains the launch files(launch files are used to run multiple nodes) 
**src folder** - it contains the source files for instance python or c++ files. 
**package.xml** - also called manifest file, contains package metadata, dependencies, and other metadata related to the package.
**CMakeLists.txt** -it contains executables, libraries, etc. it is catkin metapackage. 

A ROS package must be in the parent  “catkin_ws/src” folder, have its folder, and must contain package.xml and  CmakeList.txt.

### Creating a ros package 
```
catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
```
```
catkin_create_pkg bio_data_package std_msgs rospy roscpp
```
```
cd catkin/src 
catkin_make 
source devel/setup.bash
```
![create package](https://placehold.it/800x400 "Large example image")

This command creates a  package called “bio_data_package” with dependencies std_msgs, rospy,  and roscpp. This command automatically creates a folder named the package name, this folder contains the package.xml, CMakeLists.txt, “include” folder and “src” folder. The “src” folder in the workspace folder is different from the src folder created in the package folder.
Ensure the run catkin_make after creating a new package, then source the devel/setup.bash file,   so you can build the new package which updates the “devel” and “build” folder. 

### ROS Package command-line tool - rospack

rospack provides  get information about packages
Note: Tab completion, press the tab key once to complete a command, and twice to show you suggestions. For instance, you press tab twice after rospack

![rospack](https://placehold.it/800x400 "Large example image")

*rospack list* - list all the ROS packages in your workspace
*rospack  find bio_data_package* - toutput the path of package “bio_data_package” 

## [Understanding the Package.xml file](http://wiki.ros.org/catkin/package.xml)

The package.xml contains tags that describe the package. The required tags are name, version, description, maintainer and license. 
<name> - the name of the package 
<version> - the version of the package, usually it should be  three integers separated by dots.
<description> - a description of the package 
<maintainer> -  information about the maintainer that is someone you can contact if you need more information about the package   
<license> - the license to the package 
<buildtool_depend>(build tool dependency) - the build system required to build the package, this is usually catkin or rosbuild 
<build_depend>(build dependency) - the dependencies of the package, each dependency is enclosed in a build_depend tag.
<build_export_depend>(build export dependency) - a  dependency that is  included in the headers in public headers in the package.  
<exec_depend>(Execution Dependency) - a dependency that is among the shared libraries. 
<test_depend>(Test Dependency) - a dependency required for unit test 
<doc depend>(Documentation Tool Dependency) - a dependency required to generate documentation.



## [ROS Node](http://wiki.ros.org/ROS/Tutorials/UnderstandingNodes)
A ROS node is an executable that uses ROS to communicate with other nodes. The concept of ros node helps in fault tolerance as each node does not depend on another node. 

**[ROS Master](http://wiki.ros.org/Master)** - provides naming and registration services to the rest of the nodes in the ROS system. Publishers and Subscribers register to the master, then ROS Master tracks ROS topics being published by the publisher and ROS Topics being subscribed to by the subscribers. It also provides the Parameter Server.
**[rosout](http://wiki.ros.org/rosout)** - rosout is the name of the console log reporting mechanism in ROS. rosout subscribes to /rosout topic.
**[Parameter Server](http://wiki.ros.org/Parameter%20Server)** - is a shared, multi-variate dictionary that is accessible via network APIs. Nodes use this server to store and retrieve parameters at runtime. 
**[roscore](http://wiki.ros.org/roscore)** - master + rosout + parameter server, it controls all the ROS system, it must be running to enable ROS nodes to communicate. It is a collection of nodes and programs that are pre-requisites of a ROS-based system.


![roscore](https://placehold.it/800x400 "Large example image")

Once the roscore, you can open a new terminal to run other ros nodes. 

### ROS node command line tool - rosnode


![rosnode](https://placehold.it/800x400 "Large example image")


## ROS Run
Rosrun - this is used to run a node in a package 
```
rosrun [package_name] [node_name] 
```
```
rosrun  turtlesim turtlesim_node 
```
turtlesim_node create a GUI with a turtle 
