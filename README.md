hakuto [![Build Status](https://magnum.travis-ci.com/tork-a/hakuto.svg?token=CnBWT8crLoonzXSDK29D&branch=master)](https://magnum.travis-ci.com/tork-a/hakuto)
====================================

With this ROS package, we can realize [lunar rovers at Hakuto](http://team-hakuto.jp/team/rover), in particular `Tetris`, in a simulated lunar surface on web browser. Document here is the end user's usage and server-side operation for maintanance tasks.

If you're system administrator responsible for install, maintainance work, please see [./tetris_launch/doc/sysadmin.rst](https://github.com/tork-a/hakuto/tree/master/tetris_launch/doc/sysadmin.rst) doc.

# Simulator Usage

## Operating System and Web Browser tested

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

Users can access the simulator thru the following link: 54.92.58.250:8080/#
You'll see simulator similar to the following image:

![hakuto web simulator](/tetris_launch/doc/gzweb-1.2_tetris_osx_ff.png.jpg)

Assigned keys vary per each OS and web browser. Typically you use `mouse buttons and wheel`, `Shift` key to control `Zoom`, `Tilt` and `Elevation`.

### Keypad for simulator

Then, users can send commands from another web page: http://54.199.141.230/joystick.html
You'll see keys like below:

![hakuto web simulator keypad](http://wiki.ros.org/keyboardteleopjs?action=AttachFile&do=get&target=example.png)

There you can use ***keyboard*** to send commands that are associated with each key. 
NOTE that the images in the web page are NOT buttons; they are there to indicate which keys are associated with what commands.

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
