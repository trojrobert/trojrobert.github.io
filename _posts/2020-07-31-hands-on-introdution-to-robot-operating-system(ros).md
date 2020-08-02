---
date: 2020-07-31 04:51:19
layout: post
title: "Hands-On Introduction to Robot Operating System(ROS)"
subtitle:
description: This article describes how to install and explains ROS Packages, ROS Nodes, ROS Topics, ROS Messages, ROS service, ROS Publishers and Subscribers, and Basic ROS GUI tools. The programming language used in this article is Python. 
image: https://res.cloudinary.com/dbzzslryr/image/upload/v1596181676/ros_master_communication_znqheg.png
optimized_image: https://res.cloudinary.com/dbzzslryr/image/upload/v1596181676/ros_master_communication_znqheg.png
category:
tags:
author:
paginate: false
---

Wikipedia defines [Robot](https://en.wikipedia.org/wiki/Robot) as a machine capable of carrying out complex series of actions automatically. The advantages and importance of Robots are contentious, the robotics field is evolving every day and the benefits of robots are becoming inevitable. This article is not meant to discuss the advantages of robots, but to get you started with ROS(Robot Operating System).

This article describes ROS installation, file system, packages, nodes, topics, messages, service, publishers, subscribers, and ROS GUI tools. The programming language used in this article is Python. Refer to this [github](https://github.com/trojrobert/introduction-to-ROS) repo for the codes in this article. 

## [What is Robot Operating System(ROS)](http://wiki.ros.org/ROS/Introduction)

ROS is an open-source meta operating system or a middleware used in programming Robots. It consists of packages, software,  building tools for distributed computing, architecture for distributed communication between machines and applications. It also provides tools and libraries for obtaining, building, writing, and running code across multiple computers. It can be programmed using python, c++, and lisp.  

## ROS vs Framework vs OS(Operating System)
**Operating System(OS)** manages communication between computer software and hardware. In the process of managing this communication, it allocates resources like the central processing unit(CPU), memory, and storage. Examples are windows, Linux, android, mac OS, etc. 

**[Framework](https://en.wikipedia.org/wiki/Software_framework)** in computer programming is an abstraction in which software providing generic functionality can be selectively changed by additional user-written code, thus providing application-specific software. Software frameworks may include support programs, compilers, code libraries, tool sets, and application programming interfaces(APIs) that bring together all the different components to enable the development of a project or system. Examples are Django, Laravel, Tensorflow, Flutter, etc.

**Robot Operating System(ROS)** is not a full fledged operating system, it is a “meta operating system”. It is built on top of a full operating system. It is called an OS because it also provides the services you would expect from an operating system, including hardware abstraction, low-level device control, implementation of commonly-used functionality, message-passing between processes, and package management. It is a series of packages that can be installed on a full operating system like Ubuntu. 

## ROS level of concepts 
**Filesystem level** - these are resources located on the disk. For example, packages, package manifests (package.xml), repositories, messages types, service types, etc.

**Computation level**  - these involve the communications between peer to peer networks of ROS. Examples are nodes, master, parameter server, messages, topics, services, bags.
 
**Community level**  - these involve the exchange of software and knowledge between members of the community. Examples are [distributions]( http://wiki.ros.org/Distributions), [repositories](http://wiki.ros.org/Repositories), [ROS wiki](http://wiki.ros.org/).

## [catkin vs rosbuild](http://wiki.ros.org/catkin/conceptual_overview)
catkin is the new build system (generate executable files from source files) for ROS while rosbuild was the build system used in the past. catkin uses CMake more cleanly and only enhances CMake where it falls short on features, while rosbuild uses CMake but invokes it from Makefiles and builds each package separately and in-source. catkin was designed to be more conventional than rosbuild, allowing for better distribution of packages, better cross-compiling support, and better portability.

## ROS Distributions, Installation and File System 
**[ROS distributions](http://wiki.ros.org/Distributions)** are named alphabetically. For instance, the last 3 distributions are Lunar Loggerhead, Melodic Morenia, and Noetic Ninjemys. ROS can be officially built on Linux distributions but it also supports other operating systems. This article use ROS Melodic distribution on Ubuntu 18 Linux distribution. 

**[Installing ROS](http://wiki.ros.org/Installation)**  

```bash
sudo apt update && sudo apt install ros-melodic-desktop-full
```
You can install other distributions by changing the distribution name. For instance, you can change *melodic* to *noetic* but note *noetic* support Ubuntu Focal Fossa(20.04). This installation install the  full version, you can install smaller versions for instance:

```bash
sudo apt update && sudo apt install ros-melodic-ros-base 
```
This installation does not contain the GUI tools. 

After proper installation, you need to source the ROS setup script. *source* command reads and executes commands from the file specified as its argument in the current shell environment.

```bash
source /opt/ros/melodic/setup.bash 
```
To avoid sourcing the setup file every time a new terminal is opened, you can add the command to the *.bashrc* file. It will automatically run when you open a new terminal.

```bash
echo "/opt/ros/melodic/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

**[Initialize ROS Dependencies](http://wiki.ros.org/rosdep)**

```bash
sudo rosdep init 
rosdep update
```

Check for proper installation 

```bash
rosversion -d
```
This command output your ROS distribution

**File System** 

ROS packages are saved in a catkin "workspace" folder. The package folders are saved in the "src" folder in the catkin "workspace".


![ros_file_system](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/file_structure_vh6wry.png "ROS file system")

```bash
mkdir -p catkin_ws/src
cd catkin_ws/
catkin_make
```
The *[catkin_make](http://wiki.ros.org/catkin/commands/catkin_make)* command build all packages located in “catkin_ws/src” folder. After running *catkin_make* command, two new folders “build” and “devel” will be created. Note, you should always run *catkin_make* command when you are in the “catkin_ws” directory. The “build” folder is where CMake and Make are invoked, while the "devel" folder contains any generated files and targets, including setup.sh files. A "CMackeLists.txt" file is also created in the src folder(I explained more about this file below). 

## [ROS PACKAGES](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)

**Ros Package** - contains libraries, executables, scripts, and other artifacts for a specific ROS program. Packages are used for structuring specific programs. Files in a package also have a specific structure. A ROS package folder could contain:

* **launch folder** - it contains the launch files(launch files are used to run multiple nodes).
* **src folder** - it contains the source files for instance python or c++ files. 
* **package.xml** - also called manifest file, contains package metadata, dependencies, and other metadata related to the package.
* **CMakeLists.txt** -it contains executables, libraries, etc. it is catkin metapackage. 

A ROS package must be in the parent  “catkin_ws/src” folder, its folder, and must contain package.xml and  CmakeList.txt.

### Creating a ros package 
```bash
catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
```

```bash
catkin_create_pkg bio_data_package std_msgs rospy roscpp
```
 
```bash
cd catkin/src 
catkin_make 
source devel/setup.bash
```
![create package](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/create_package_qoqys3.png "Create ROS Package")

This command creates a  package called “bio_data_package” with dependencies std_msgs, rospy,  and roscpp. This command automatically creates a folder named the package name, this package folder contains the "package.xml", "CMakeLists.txt", “include” folder and “src” folder. The “src” folder in the workspace folder is different from the "src" folder created in the package folder.
Build all the packages in "catkin/src" by running *catkin_make*, *source* the "setup.bash" in the "devel" folder to add new environment variables. 

### ROS Package command-line tool - rospack

rospack is used to get information about packages.
Note: Tab completion, press the tab key once to complete a command, and twice to show you suggestions. For instance, you press tab twice after rospack.

![rospack](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rospack_fps0md.png "rospack")

> *rospack list* - list all the ROS packages in your workspace
> *rospack  find bio_data_package* - to output the path of package “bio_data_package” 

## [Understanding the Package.xml file](http://wiki.ros.org/catkin/package.xml)

The package.xml contains tags that describe the package. The required tags are name, version, description, maintainer and license. 

* `<name>` - the name of the package.	
* `<version>` - the version of the package, usually it should be  three integers separated by dots.	
* `<description>` - a description of the package.	
* `<maintainer>` -  information about the maintainer i.e someone you can contact if you need more information about the package.
* `<license>` - the license to the package.	
* `<buildtool_depend>`(build tool dependency) - the build system required to build the package, this is usually catkin or rosbuild.	
* `<build_depend>`(build dependency) - the dependencies of the package, each dependency is enclosed in a build_depend tag.	
* `<build_export_depend>`(build export dependency) - a  dependency that is  included in the headers in public headers in the package.	
* `<exec_depend>`(Execution Dependency) - a dependency that is among the shared libraries.	
* `<test_depend>`(Test Dependency) - a dependency required for unit test.	
* `<doc depend>`(Documentation Tool Dependency) - a dependency required to generate documentation.	

## [ROS Node](http://wiki.ros.org/ROS/Tutorials/UnderstandingNodes)
A ROS node is an executable that uses ROS to communicate with other nodes. The concept of ros node helps in fault tolerance as each node does not depend on another node. 
* **[ROS Master](http://wiki.ros.org/Master)** - provides naming and registration services to the rest of the nodes in the ROS system. Publishers and Subscribers register to the master, then ROS Master tracks ROS topics being published by the publisher and ROS Topics being subscribed to by the subscribers. It also provides the Parameter Server. 
* **[rosout](http://wiki.ros.org/rosout)** - rosout is the name of the console log reporting mechanism in ROS. rosout subscribes to /rosout topic. 
* **[Parameter Server](http://wiki.ros.org/Parameter%20Server)** - is a shared, multi-variate dictionary that is accessible via network APIs. Nodes use this server to store and retrieve parameters at runtime. 
* **[roscore](http://wiki.ros.org/roscore)** - master + rosout + parameter server. It controls the entire ROS system. It must be running to enable ROS nodes to communicate. It is a collection of nodes and programs that are pre-requisites of a ROS-based system.

![roscore](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/roscore_djm9sh.png "rocore")

Once roscore is running, you can open a new terminal to run other ros nodes. 


### ROS node command-line tool - rosnode
![rosnode](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rosnode_h_t61eve.png "rosnode")


## ROS Run
rosrun - this is used to run a node in a package 
```bash
rosrun [package_name] [node_name] 
```

```bash
rosrun  turtlesim turtlesim_node 
```
turtlesim_node display a GUI with a turtle.

![rosrun turtlesim](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/turtlesim_fifpzi.png "turtlesim")

Run the command on a different terminal 
```bash
rosrun turtlesim turtle_teleop_key 
```
The turtle_teleop_key node provides a way to control the turtle with a keyboard. Click on the terminal where you ran `rosrun turtlesim turtle_teleop_key`, then press the arrow keys, the turtle moves in the direction of the arrow key pressed.  

## [ROS Topics](http://wiki.ros.org/Topics)
Ros Topics are the buses used by ROS nodes to exchange messages. Imagine a ROS Topic as a water pipe and ROS Message as the water, the two ends of the pipe are where the nodes are located. Topic transport message between a publisher node and a subscriber node. Ros Topics have anonymous publish/subscribe semantics. Nodes that generate message/ data publish to a specific topic, and nodes that consume or need data subscribed to a specific topic. The relationship between publishers and subscribers is many to many.

In the example above, the turtle_teleop_key node publishes the key pressed to the /turtle/cmd_vel topic and the turtlesim node subscribes to that same topic.  

### ROS topic command-line tool - rostopic
![rostopic](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rostopic_h_azpp5v.png "rostopic")

```bash
rostopic list -v
```
![rostopic list](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rostopic_list_zoucwc.png "rostopic_list")

> rostopic hz [topic] (shows how fast the messages are publishing) 
> rostopic hz /turtle/cmd_vel 

## [ROS message](http://wiki.ros.org/Messages)
Nodes communicate by sending ROS messages to each other using ROS Topic. A message can be of primitive type integer, floating-point, boolean, etc. A publisher and subscriber should communicate using the same topic type. The topic type is determined by the message type.


### Creating a ROS message 

Create a msg folder in your package folder. We created a new package call bio_data_package in the example above. Inside this newly created “msg” folder, create a msg file called name.msg

```bash
mkdir catkin_ws/src/bio_data_package/msg
cd catkin_ws/src/bio_data_package/msg
touch name.msg 
```
#### Step 1 
Copy the following command into the “name.msg” file. You can also check on [github](https://github.com/trojrobert/introduction-to-ROS/blob/master/msg/name.msg)
```txt
 string first_name
 string last_name
```
#### Step 2
**Open the package.xml** for the bio_data_package package in a text editor, then modify the <build_depend> tag and the <exec_depend> tag by adding. You can also check on [github](https://github.com/trojrobert/introduction-to-ROS/blob/master/sample_package.xml)
```txt
 <build_depend>message_generation</build_depend>
 <exec_depend>message_runtime</exec_depend>
```
Now you should have something like this, please don’t modify other lines.
![package_xml](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/package.xml_byglmo.png "package_xml")

#### Step 3 
**Open the CmakeList.txt file** for the bio_data_package package in a text editor. This is needed for steps 3 to 6. Check a sample file on [github](https://github.com/trojrobert/introduction-to-ROS/blob/master/sample_CMakeLists.txt)

Modify the *find_package* call by adding *message generation* to its components. Now you should have something similar to this.
![find_package](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/find_package_tmh1c4.png "find_package")

#### Step 4
Modify the *catkin_package* by adding *message_runtine*
![catkin_package](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/catkin_package_a0iwdk.png "catkin_package")

#### Step 5
Modify *add_message_files* by adding the *name.msg*, this enable CMake to reconfigure the project with the new msg file. 
![add_message_files](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/add_message_files_jdgrhb.png "add message files")

#### Step 6
Modify *generate_message* by removing the # symbols to uncomment it.
![generate_message](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/generate_message_tj10q6.png "generate_message")

#### Step 7
```bash
cd  catkin_ws
catkin_make
source devel/setup.bash
```
### ROS message command-line tool - rosmsg

![rosmsg](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rosmsg_h_fj7om6.png "rosmsg")

Show the description of the new message created 
```bash
rosmsg show bio_data_package/name
```
![rosmsg show](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rosmsg_show_mwvu9y.png "rosmsg show")

## [ROS Service](http://wiki.ros.org/Services)

ROS service is one to one two way transport, it is suitable for request/reply interactions. A ROS node(server) offers a service, while another ROS node(client) requests for the service.  The server sends a response back to the client. Services are defined using srv files. srv files are just like msg files, except they contain two parts: a request and a response. Services also have types like topics.

### Creating a ROS Service 

Create a srv folder in your package folder. You created a new package call bio_data_package in the example above. Inside this newly created “srv” folder, create a srv file called full_name.srv. A srv file is used to describe a service, srv files are stored in the “srv” folder.

```bash
mkdir catkin_ws/src/bio_data_package/srv
cd catkin_ws/src/bio_data_package/srv
touch full_name.srv
```
 
Copy the following command into the “full_name.srv” file. A sample is on [github](https://github.com/trojrobert/introduction-to-ROS/tree/master/srv)

```txt
string first_name
string last_name
---
string full_name 
```

A srv file has two parts separated by ---, the first part is the request while the second part is the response.

Do the steps required in *creating a ROS message*, but instead of Step 5, do thhe following. Please don’t repeat all the steps if you have done them before. 

#### Step 5(specific for ROS service)
Modify *add_service_files* by adding the "full_name.srv", this enables CMake to reconfigure the project with the new srv file.

![add_service_files](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/add_service_files_i1xqf0.png "Add service files")

### ROS service command-line tool - rossrv
![rossrv h](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rossrv_h_olli4l.png "rossrv_h")

Show the description of the new service created 
```bash
rossrv show bio_data_package/name
```

### ROS Services vs ROS Topic
<table>
  <thead>
    <tr>
      <th>ROS Service</th>
      <th>ROS Topic</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Involves the communication between any two nodes</td>
      <td>Involves the communication between Publishers and  Subscribers</td>
    </tr>
    <tr>
      <td>It is a two way transport</td>
      <td>It is a one way transport </td>
    </tr>
    <tr>
      <td>It is one to one </td>
      <td>It is many to many </td>
    </tr>
    <tr>
      <td>Involves a request/ reply pattern  </td>
      <td>Does not involves a Request/reply pattern </td>
    </tr>
  </tbody>
</table>

### ROS Publisher and Subscriber 
Publisher and subscriber is many to many but one way transport. A node sends out a message by publishing it to a given topic. The topic is a name that is used to identify the content of the message. A node that is interested in a certain kind of data will subscribe to the appropriate topic.


#### Creating a Publisher

A publisher is a node that publishes messages into a topic. Create a scripts folder in your package folder, we created a new package call bio_data_package in the example above, inside this newly created “script” created folder, create a python file called writer_pub.py

```bash
mkdir catkin_ws/src/bio_data_package/scripts
cd catkin_ws/src/bio_data_package/scripts
touch writer_pub.py 
chmod +x writer_pub.py
```

Copy the following code into the “writer_pub.py” file. Sample is on [github](https://github.com/trojrobert/introduction-to-ROS/blob/master/scripts/writer_pub.py)

```python
#!/usr/bin/env python

import rospy # This module is used to write ROS node in python
from std_msgs.msg import String # This module is responsible for the message type

def writer():
	"""Create a Publisher and send message through a topic"""
    
	# initiate a publisher node called "writer_node"
	# anonymous=True ensure every node is unique by adding random numbers to end
	rospy.init_node('writer_node', anonymous=True)

	# ensures  the publisher publish to topic "/print_topic" with message type "String"
	# queue_size is the limit to the number of messages in queued messages
	pub = rospy.Publisher('/print_topic', String, queue_size=10)

	# looping at a desired rate, the number of times per second to go through the while loop
	rate = rospy.Rate(1)
 
	# ensure the rospy is running until the program is shutdown
	while not rospy.is_shutdown():
   
    	     writer_str = "Hello world, this is the message published   %s" % rospy.get_time()
   	 
                 # Print message to screen, write message to node log file
                 # write message to rosout
    	     rospy.loginfo(writer_str)

                 # publish "writer_str" to topic "/print_topic"
    	     pub.publish(writer_str)

    	    # ensures the loop sleep for some seconds just like time.sleep
    	    rate.sleep()

if __name__ == '__main__':
	try:
    	     writer()
	except rospy.ROSInterruptException:
    	     pass
```

### Creating a Subscriber

A subscriber is a node that gets messages from a topic. Create a python file called reader_sub.py in the "scripts" folder.

```bash
touch reader_sub.py 
chmod +x reader_sub.py 
```

Copy the following code into the “reader_sub.py” file. A sample is on [github](https://github.com/trojrobert/introduction-to-ROS/blob/master/scripts/reader_sub.py)

```python
#!/usr/bin/env python

import rospy  #This module is used to write ROS node in python
from std_msgs.msg import String # This module is responsible for the message type

def callback(message):

    """Print message received from the subscriber
    
    args:
        message(str): The message received by the subscriber        
    """
    # Print message to screen, write message to node log file
    # write message to rosout
    rospy.loginfo("Caller - "+ rospy.get_caller_id() + " I received - %s", message.data)
  
def reader():
    """Create a subscriber and receive message from a topic"""

    # initiate a subscriber node called "reader_node"
    # anonymous=True ensure every node is unique by adding random numbers to end
    rospy.init_node('reader_node', anonymous=True)

    # ensures  the subscriber subscribes to topic "/print_topic" with message type "String"
    # the subscriber subscribe to topic "/print_topic" which is same as the topic that 
    # the Publisher publish to, with the same message type “string”, then call the callback function
    rospy.Subscriber('/print_topic', String, callback)

    # ensure the python program does not exit, that is it keeps it in execution mode
    rospy.spin()
    
if __name__ == '__main__':
    reader()
```

Modify the *caktin_install_python()* call in CMameLists.txt

```txt
catkin_install_python(PROGRAMS 
    scripts/writer_pub.py
    scripts/reader_sub.py
  DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)
```

Build the created publisher and subscriber 

```bash
cd  catkin_ws
catkin_make
source devel/setup.bash
```

Test the Publisher and Subscriber 

**Terminal 1**
`roscore` 

**Terminal 2** 
`rosrun bio_data_package writer_pub.py`

**Terminal 3** 
`rosrun bio_data_package reader_sub.py`

**Terminal 4** 
`rosnode list -a`

![publisher subscriber](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181676/publisher_subscriber_wd9a2t.png "publisher subscriber")

## ROS Tools

### [Roswtf](http://wiki.ros.org/roswtf)
roswtf is a tool for diagnosing issues with a running ROS file system. It evaluates ROS setup
like environment variables, packages , stacks, launch files and configuration issues. 
```bash
cd catkin_ws/src/bio_data_package
roswtf
```
![roswtf](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/roswtf_t0yihy.png "roswtf")

### [rqt_console](http://wiki.ros.org/rqt_console)

rqt_console is a tool that displays  messages being published to rosout. These messages have different level of severity like debug, info, warn, error, fatal.

**Terminal 1** 
`roscore` 

**Terminal 2** 
`rosrun  turtlesim turtlesim_node`

**Terminal 3**
`rosrun turtlesim turtle`

**Terminal 4**
`rqt_console` 

Now move the turtle to the wall 

![rqt_console](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/rqt_console_n5aqfq.png "rqt_console")

### rqt _graph
This shows nodes and the topics the nodes are communicating on. 

![rqt_graph](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/rqt_graph_fxiaqi.png "rqt_graph")

### rqt _plot
Display the scrolling time plot of data published on a topic 

![rqt_plot](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/rqt_plot_pgesyu.png "rqt_plot")


### rqt 
rqt contain most ROS GUI tools, you can select the on you want in the *Plugib* tab.
![rqt](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181674/rqt_k3nix8.png "rqt")

## Other  ROS concepts 

**[ROS Launch](http://wiki.ros.org/roslaunch)** - is used for starting and  stopping multiple ros nodes. It is used to execute a ros program which is a .launch file.

**ROS Stack** - this contain several packages.

**[rosbag](http://wiki.ros.org/ROS/Tutorials/Recording%20and%20playing%20back%20data)** - published  topics are saved as .bag file, rosbag command line tool is used to work with bag files. 

**[rviz](http://wiki.ros.org/rviz)** - 3D visualization tool for ROS 

```bash 
rosrun rviz rviz
```
![rviz](https://res.cloudinary.com/dbzzslryr/image/upload/v1596181675/rviz_yemdpw.png "rviz")
