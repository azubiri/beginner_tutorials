# Beginner Tutorials of ROS

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

This is a package that follows the official ROS tutorial, specifically the beginner level.
In the next link you can find the website where there is the tutorial: [ROS_TUTORIALS][ros_tuto]
Here we will see how we use a ROS package exporting from github to our local terminal.

# Settings
This section will show the settings from the laptop where this package was created, built, installed and tested.
   - OS System: Ubuntu 18.04
   - ROS version: Melodic

# Build this ROS package
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
The error is below:
```sh
ssh user@xxx.yyy.zz.kk 'cd Documents;ls -l;'
Base path: /home/alberto/catkin_ws
Source space: /home/alberto/catkin_ws/src
Build space: /home/alberto/catkin_ws/build
Devel space: /home/alberto/catkin_ws/devel
Install space: /home/alberto/catkin_ws/install
####
#### Running command: "cmake /home/alberto/catkin_ws/src -DCATKIN_DEVEL_PREFIX=/home/alberto/catkin_ws/devel -DCMAKE_INSTALL_PREFIX=/home/alberto/catkin_ws/install -G Unix Makefiles" in "/home/alberto/catkin_ws/build"
####
-- Using CATKIN_DEVEL_PREFIX: /home/alberto/catkin_ws/devel
-- Using CMAKE_PREFIX_PATH: /home/alberto/catkin_ws/devel;/opt/ros/melodic
-- This workspace overlays: /home/alberto/catkin_ws/devel;/opt/ros/melodic
-- Found PythonInterp: /usr/bin/python2 (found suitable version "2.7.15", minimum required is "2") 
-- Using PYTHON_EXECUTABLE: /usr/bin/python2
-- Using Debian Python package layout
-- Using empy: /usr/bin/empy
-- Using CATKIN_ENABLE_TESTING: ON
-- Call enable_testing()
-- Using CATKIN_TEST_RESULTS_DIR: /home/alberto/catkin_ws/build/test_results
-- Found gmock sources under '/usr/src/googletest': gmock will be built
-- Found PythonInterp: /usr/bin/python2 (found version "2.7.15") 
-- Found gtest sources under '/usr/src/googletest': gtests will be built
-- Using Python nosetests: /usr/bin/nosetests-2.7
-- catkin 0.7.17
-- BUILD_SHARED_LIBS is on
-- BUILD_SHARED_LIBS is on
-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
-- ~~  traversing 1 packages in topological order:
-- ~~  - beginner_tutorials
-- ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
-- +++ processing catkin package: 'beginner_tutorials'
-- ==> add_subdirectory(beginner_tutorials)
-- Using these message generators: gencpp;geneus;genlisp;gennodejs;genpy
-- beginner_tutorials: 1 messages, 1 services
CMake Warning at /opt/ros/melodic/share/catkin/cmake/catkin_package.cmake:166 (message):
  catkin_package() DEPENDS on 'system_lib' but neither
  'system_lib_INCLUDE_DIRS' nor 'system_lib_LIBRARIES' is defined.
Call Stack (most recent call first):
  /opt/ros/melodic/share/catkin/cmake/catkin_package.cmake:102 (_catkin_package)
  beginner_tutorials/CMakeLists.txt:104 (catkin_package)


CMake Error at /opt/ros/melodic/share/catkin/cmake/catkin_package.cmake:304 (message):
  catkin_package() include dir 'include' does not exist relative to
  '/home/alberto/catkin_ws/src/beginner_tutorials'
Call Stack (most recent call first):
  /opt/ros/melodic/share/catkin/cmake/catkin_package.cmake:102 (_catkin_package)
  beginner_tutorials/CMakeLists.txt:104 (catkin_package)


-- Configuring incomplete, errors occurred!
See also "/home/alberto/catkin_ws/build/CMakeFiles/CMakeOutput.log".
See also "/home/alberto/catkin_ws/build/CMakeFiles/CMakeError.log".
Invoking "cmake" failed
```
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

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [ros_tuto]: <http://wiki.ros.org/ROS/Tutorials>
