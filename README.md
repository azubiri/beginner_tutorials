# Beginner Tutorials of ROS

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)


## Table of Contents
1. [Introduction](#intro)
2. [Settings](#set)
3. [Building a ROS package](#build)
4. [Installation](#installation)

<a name="intro"></a>
## Introduction
This is a package that follows the official ROS tutorial, specifically the beginner level.
In the next link you can find the website where there is the tutorial: [ROS_TUTORIALS][ros_tuto]
Here we will see how we use a ROS package exporting from github to our local terminal.

<a name="set"></a>
## Settings
This section will show the settings from the laptop where this package was created, built, installed and tested.
   - OS System: Ubuntu 18.04
   - ROS version: Melodic

<a name="build"></a>
## Build this ROS package
Here, we will see which are the steps for building this ROS package, and their considerations.

Create your ROS environment:
```sh
$ mkdir -p ~/catkin_ws/src
$ cd catkin_ws
$ catkin_make
```
You will see three folders:
```sh
$ ls
build   devel   src
```
Make sure you source your setup:
```sh
$ source devel/setup.bash
$ echo $ROS_PACKAGE_PATH
/home/youruser/catkin_ws/src:/opt/ros/kinetic/share
```
Clone this repository to your terminal:
```sh
$ cd src
$ git clone https://github.com/azubiri/beginner_tutorials
```
Now we have the ROS package in our local workspace:
```sh
$ ls
$ beginner_tutorials    CMakeLists.txt
```
In principle we could build it, but in my case an error appeared typing:
```sh
$ cd ~/catkin_ws/
$ catkin_make
```
You can check the error inside error file.

That means the compiler doesn't find an include folder inside the ROS package.
The solution is just creating this folder:
```sh
$ cd src/beginner_tutorials/
$ mkdir -p include/beginner_tutorials
```
Now, it should compile well:
```sh
$ cd ~/catkin_ws/
$ catkin_make
```

<a name="installation"></a>
## Installation
For installing this package in your workspace:
```sh
$ cd ~/catkin_ws/
$ catkin_make_install
```

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [ros_tuto]: <http://wiki.ros.org/ROS/Tutorials>
