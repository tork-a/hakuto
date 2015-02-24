hakuto [![Build Status](https://magnum.travis-ci.com/tork-a/hakuto.svg?token=CnBWT8crLoonzXSDK29D&branch=master)](https://magnum.travis-ci.com/tork-a/hakuto)
======

ROS package suite for the lunar rovers at Hakuto project, a Google XPRIZE competitor.

.. contents:: Table of Contents
   :depth: 2

# Overview

With this ROS package, we can realize Hakuto's Tetris robots in a simulated lunar surface on web browser. Document here is the end user's usage and server-side operation for maintanance tasks.

# For Simulator User

## OS and Web Browser tested

The simulator has been seen working on the following environment:

 * Mac OSX 10.10
  * Google Chrome 40.0 
  * Firefox 35.0
 * Android 5.0.1
  * Google Chrome 40.0 
 * Ubuntu Linux (12.04 and 14.04)
  * Google Chromium 37.0 
  * Firefox 35.0

Under following circumstance the simulator limitedly works:

 * MS Windows 7 (64bit)
  * IE11

## How to Use Simulator

### Simulator view

Users can access the simulator thru the following link: http://54.199.141.230:8080/#
You'll see simulator similar to the following image:

![hakuto web simulator](/tetris_launch/doc/gzweb-1.2_tetris_osx_ff.png.jpg)

Assigned keys vary per each OS and web browser. Typically you use `mouse buttons and wheel`, `Shift` key to control `Zoom`, `Tilt` and `Elevation`.

### Keypad for simulator

Then, users can send commands from another web page: http://54.199.141.230/joystick.html
You'll see keys like below:

![hakuto web simulator keypad](http://wiki.ros.org/keyboardteleopjs?action=AttachFile&do=get&target=example.png)

There you can use ***keyboard*** to send commands that are associated with each key. 
NOTE that the images in the web page are NOT buttons; they are there to indicate which keys are associated with what commands.

# For System Admin

## Web server requirement

 * Internet connection
 * Ubuntu Linux. 12.04 or 14.04 64bit.
  * Currently installation of web simulator is only limited to Ubuntu Linux (the limitation comes from `Gzweb`, web frontend of the physics simulator `Gazebo`).
 * [ROS Indigo Igloo](http://wiki.ros.org/indigo)

## hakuto package Installation

### Install via apt (RECOMMENDED)

(TBA)

### Install via source

The directory `~/ros_ws/` will be used as a source directory for this instruction.

1. Download `hakuto` ROS package.

 ```
$ mkdir -p ~/ros_ws/src && cd ~/ros_ws/src && catkin_init_workspace
$ git clone https://github.com/tork-a/hakuto.git
```

2. Install depended libraries.

 ```
$ cd ~/ros_ws
$ rosdep install --from-paths src --ignore-src --rosdistro indigo -r -y 
```

3. Now ready to build sources.

 ```
$ catkin_make install && source install/setup.bash
```

4. Now let's install web frontend of the simulator, `Gzweb`. Follow the [official installation steps](http://gazebosim.org/gzweb#gzweb_installation). Go through until `Clone the repository and build` section (ie. Stop before `Running gzserver, gzweb server, and WebGL client` section). Select `./deploy.sh -m`.

5. Place the necessary 3D model files of lunar surface by running the following commands.

 ```
$ cd %HOME_GZWEB%/http/client/
$ mkdir assets         (create `assets` folder in case it doesn't exist)
$ ln -fs `rospack find tetris_description`/models/tetris/ .
```

 `%HOME_GZWEB%` is where you intalled `Gzweb`. Also ,

 ```
$ cd %HOME_GZWEB%/http/client/assets     (`assets` folder may not exist. If so, create it)
$ ln -fs `rospack find tetris_gazebo`/models/apollo15_landing_site_1000x1000 .
```

6. Prepare joystick keypad (for tele-operation)

 Tele-operation is done by using [keyboardteleopjs](http://wiki.ros.org/keyboardteleopjs) that accepts command input from the keyboard through web browser.
 
 Put a `joystick.html` file under the docroot of your web server. We use `/var/www/` for `apache` in this document.

 ```
terminal-3$ cp `rospack find tetris_launch`/www/joystick.html /var/www/
```

 You might need to edit the file using your web server's IP address, and the name of `Twist` topic. Do that by following [the tutorial for keyboard teleop](http://wiki.ros.org/keyboardteleopjs/Tutorials/CreatingABasicTeleopWidgetWithSpeedControl).

## Run the web simulator server (Gzweb, Gazebo on web server)

You need to open multiple terminals and run the following.

 * Terminal-1: Run simulation engine, hakuto simulation moduels.
 * Terminal-2: Run web frontend for the simulation engine.

 ```
terminal-1$ roslaunch tetris_launch demo.launch gui:=false
```

 ```
terminal-2$ DISPLAY=:0.0 ROS_MASTER_URI=http://%WEBSERVER_IPADDR%:13311 ROS_IP=%WEBSERVER_IPADDR% %HOME_GZWEB%/start_gzweb.sh &

(Example)
terminal-2$ DISPLAY=:0.0 ROS_MASTER_URI=http://54.199.141.230:13311 ROS_IP=54.199.141.230 /usr/local/lib/node_modules/gzweb/start_gzweb.sh &
```
## hakuto ROS package 

Please see the manifest file of each package as follows for the description.

 * [tetris_description](https://github.com/tork-a/hakuto/blob/master/tetris_description/package.xml)
 * [tetris_gazebo](https://github.com/tork-a/hakuto/blob/master/tetris_gazebo/package.xml)
 * [tetris_launch](https://github.com/tork-a/hakuto/blob/master/tetris_launch/package.xml)

## Troubleshoot server

### When something is wrong...

On Ubuntu, check if all the necessary processes are running. Example:

 ```
$ ps -ef | grep ros
ubuntu    4351  2660  0 Jan14 pts/10   00:15:08 /usr/bin/python /opt/ros/indigo/bin/roscore
ubuntu    4363  4351  0 Jan14 ?        00:19:58 /usr/bin/python /opt/ros/indigo/bin/rosmaster --core -p 11311 __log:=/home/ubuntu/.ros/log/3e773a72-9c0c-11e4-ad41-0a43be0c09e0/master.log
ubuntu    4376  4351  0 Jan14 ?        00:23:56 /opt/ros/indigo/lib/rosout/rosout __name:=rosout __log:=/home/ubuntu/.ros/log/3e773a72-9c0c-11e4-ad41-0a43be0c09e0/rosout-1.log
ubuntu    4450  2808  0 Jan14 pts/12   00:14:37 /usr/bin/python /opt/ros/indigo/bin/roslaunch tetris_gazebo tetris_world.launch gui:=false
ubuntu    4482  4450  0 Jan14 ?        00:00:00 /bin/sh /opt/ros/indigo/lib/gazebo_ros/gzserver /opt/ros/indigo/share/tetris_gazebo/worlds/apollo15_landing_site.world __name:=gazebo __log:=/home/ubuntu/.ros/log/3e773a72-9c0c-11e4-ad41-0a43be0c09e0/gazebo-1.log
ubuntu    4490  4482 28 Jan14 ?        5-03:44:53 gzserver /opt/ros/indigo/share/tetris_gazebo/worlds/apollo15_landing_site.world __name:=gazebo __log:=/home/ubuntu/.ros/log/3e773a72-9c0c-11e4-ad41-0a43be0c09e0/gazebo-1.log -s /opt/ros/indigo/lib/libgazebo_ros_paths_plugin.so -s /opt/ros/indigo/lib/libgazebo_ros_api_plugin.so
ubuntu    4744  3306  0 Jan14 pts/16   00:15:11 /usr/bin/python /opt/ros/indigo/bin/roslaunch rosbridge_server rosbridge_websocket.launch
ubuntu    4762  4744  7 Jan14 ?        1-08:06:14 python /opt/ros/indigo/lib/rosbridge_server/rosbridge_websocket __name:=rosbridge_websocket __log:=/home/ubuntu/.ros/log/3e773a72-9c0c-11e4-ad41-0a43be0c09e0/rosbridge_websocket-1.log
ubuntu    4763  4744  7 Jan14 ?        1-06:59:59 python /opt/ros/indigo/lib/rosapi/rosapi __name:=rosapi __log:=/home/ubuntu/.ros/log/3e773a72-9c0c-11e4-ad41-0a43be0c09e0/rosapi-2.log
ubuntu   13117 11159  7 21:23 pts/4    00:00:05 python /opt/ros/indigo/lib/teleop_twist_keyboard/teleop_twist_keyboard.py cmd_vel:=tetris/cmd_vel
ubuntu   13181 12924  0 21:24 pts/18   00:00:00 grep --color=auto ros
```

# For Developers

Source code of hakuto package is opensourced at github repository: https://github.com/tork-a/hakuto

## (Option) Run on Gazebo, desktop simulator

### Set up Gazebo (do this only once)

[Desktop simulator version of Gazebo](http://gazebosim.org/) should be already installed by the previous steps (`rosdep`, in particular). We still need some customization.

1. Link model files directory.

 ```
$ cd /usr/share/gazebo-%VERSION_NUMBER%
$ cd /usr/share/gazebo-2.2               (Example)

$ sudo ln -fs %YOUR_CATKIN_WORKSPACE%/src/osrf/gazebo_models models
$ sudo ln -fs ~/catkinws/src/osrf/gazebo_models models               (Example following the directory used in above instruction)
```

### Run simulation on Gazebo

 ```
$ roslaunch tetris_launch demo.launch gui:=false
```

![Screenshot](https://cloud.githubusercontent.com/assets/1840401/5726189/57f0fb2c-9b0e-11e4-8ef4-c32f945d893c.png)

 * NOTE-1: 1st time run on a computer, internet access is required to download model files for Gazebo.
 * NOTE-2: `GAZEBO_MODEL_PATH` takes absolute path.
