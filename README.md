hakuto [![Build Status](https://magnum.travis-ci.com/tork-a/hakuto.svg?token=CnBWT8crLoonzXSDK29D&branch=master)](https://magnum.travis-ci.com/tork-a/hakuto)
======

ROS package suite for robots at Hakuto, a Google XPRIZE competitor.

.. contents:: Table of Contents
   :depth: 2

Prerequisite
==================

 * Ubuntu 14.04 64bit, ROS Indigo Igloo.
 * Internet connection (only for the installation and the 1st time run)

hakuto package Installation
==========================================

Install via apt (RECOMMENDED)
-------------------------------------------------------------------------

(TBA)

Install via source
-----------------------------------------------------------------------------------------

(will be non-recommended once apt installation becomes available)

1. Download `hakuto` ROS package.

 ```
$ mkdir -p ~/ros/catkinws/src && cd ~/ros/catkinws/src && catkin_init_workspace
$ git clone https://github.com/tork-a/hakuto.git
```

2. Also download other necessary sources.

 ```
$ cd ~/ros/catkinws
$ wstool init -j8 src
$ wstool merge https://raw.githubusercontent.com/tork-a/hakuto/master/.rosinstall?token=ABwVEQx8x-9V2eVzDfCO25Rm2hp83Vohks5UuK2xwA%3D%3D -t src
$ wstool update -t src
```

3. Install dependencies.

 ```
$ cd ~/ros/catkinws
$ rosdep install --from-paths src --ignore-src --rosdistro indigo -r -y 
```

4. Now ready to build sources.

 ```
$ catkin_make install && source install/setup.bash
```

Run on Gazebo, desktop simulator
==========================================

Set up Gazebo (do this only once)
-----------------------------------------------

[Desktop simulator version of Gazebo](http://gazebosim.org/) should be already installed by the previous steps (`rosdep`, in particular). We still need some customization.

1. Link model files directory.

```
$ cd /usr/share/gazebo-%VERSION_NUMBER%
$ cd /usr/share/gazebo-2.2               (Example)

$ sudo ln -fs %YOUR_CATKIN_WORKSPACE%/src/osrf/gazebo_models models
$ sudo ln -fs ~/catkinws/src/osrf/gazebo_models models               (Example following the directory used in above instruction)
```

Run simulation on Gazebo
------------------------------

```
$ GAZEBO_MODEL_PATH=~/ros/catkinws/src/osrf/gazebo_models roslaunch tetris_launch demo.launch 
```

![Screenshot](https://cloud.githubusercontent.com/assets/1840401/5726189/57f0fb2c-9b0e-11e4-8ef4-c32f945d893c.png)

 * NOTE-1: 1st time run on a computer, internet access is required to download model files for Gazebo.
 * NOTE-2: `GAZEBO_MODEL_PATH` takes absolute path.

Run on web, by gzweb (Gazebo on web server)
============================================

Install, setup gzweb (Web application of Gazebo)
----------------------------------------------------------------------

1. Follow the official installation steps. Stop before `./start_gzweb.sh`.
http://wiki.gazebosim.org/wiki/Gzweb/install

2. Additionally, go through another installation steps page. http://wiki.gazebosim.org/wiki/Gzweb/build

3. Run the following commands.

```
$ cd %HOME_GZWEB%/http/client/assets       (this is where gzweb source is downloaded in the following step)
$ ln -fs `rospack find tetris_description`/models/tetris/ .
$ ln -fs /usr/share/gazebo-2.2/models/apollo15_landing_site_1000x1000 .
```

