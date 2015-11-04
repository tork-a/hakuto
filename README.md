hakuto [![Build Status](https://travis-ci.org/tork-a/hakuto.svg?branch=master)](https://travis-ci.org/tork-a/hakuto)
====================================

With this ROS package, we can realize [lunar rovers at Hakuto](http://team-hakuto.jp/team/rover), in particular `Tetris`, in a simulated lunar surface on web browser. Document here is the end user's usage and server-side operation for maintanance tasks.

If you're system administrator responsible for install/maintainance work please see [./tetris_launch/doc/sysadmin.rst](https://github.com/tork-a/hakuto/tree/master/tetris_launch/doc/sysadmin.rst) doc.

# Operating System and Web Browser tested

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

# Simulator Basic Usage

## Simulator view

Users can access the simulator thru the following link: 54.92.58.250:8080/#
You'll see simulator similar to the following image:

![hakuto web simulator](/tetris_launch/doc/img/gzweb-1.2_tetris_osx_ff.png.jpg)

Assigned keys vary per each OS and web browser. Typically you use `mouse buttons and wheel`, `Shift` key to control `Zoom`, `Tilt` and `Elevation`.

## Keypad for simulator

Then, users can send commands from another web page: http://54.199.141.230/joystick.html
You'll see keys like below:

![hakuto web simulator keypad](http://wiki.ros.org/keyboardteleopjs?action=AttachFile&do=get&target=example.png)

There you can use ***keyboard*** to send commands that are associated with each key. 
NOTE that the images in the web page are NOT buttons; they are there to indicate which keys are associated with what commands.

# Simulator Advanced Usage

## Modify environment 

 tetris_launch/doc/img/hakuto_gzweb_panel_sun.png 

## Reset views

Sometimes you want to "reset" the robot's pose, environment, and the view (where you're looking from at the simulation) to the initial status. 

![Use the tab on the left side of the simulator](/tetris_launch/doc/img/hakuto_gzweb_initdisplay.png)

## Restart simulation

At the time of writing (Mar 2015) there's no end-user feature to restart the simulation. Please either `reset` views, or contact the simulation system admins.
See the troubleshooting.

# Troubleshooting

The Hakuto web simulation is administered by [TORK](http://opensource-robotics.tokyo.jp/), but this is subject to change. For now (Mar, 2015) any issues and requests can be contacted on [the issue tracker on github](https://github.com/tork-a/hakuto/issues).
