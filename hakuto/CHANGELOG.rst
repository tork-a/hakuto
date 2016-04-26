^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package hakuto
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.1.5 (2016-04-27)
------------------

0.1.4 (2015-11-06)
------------------
* [improved] Sun light is stronger on the Moon
* [fix] Temporary workaround to Gzweb not showing model (`#45 <https://github.com/tork-a/hakuto/issues/45>`_)
* [fix] Workaround for teleop dying error ( `#23 <https://github.com/tork-a/hakuto/issues/23>`_)
* [sys] all link is rended by texture, so material is not needed
* [sys] mv texture location to materials/textures, see https://bitbucket.org/osrf/gazebo_models/commits/0bde1dbe0cc62cefbcdd4a5a760e4f2e2aeb8bb6
* [doc] Use rosdoc_lite. Add more Gzweb server-side usage
* Contributors: Kei Okada, Isaac I.Y. Saito

0.1.3 (2015-04-11)
------------------
* (Improve) Cosmetics; Robot spawned at more adventurous starting pose. Sun location to cast more realistic shadow.
* (Doc) No fragment aura around the earth to fix `#40 <https://github.com/tork-a/hakuto/issues/40>`_
* Contributors: Isaac IY Saito

0.1.2 (2015-04-09)
------------------
* (Feature) Add starry sky scene, earth seen from lunar surface taken by Kaguya, JAXA
* Contributors: Isaac IY Saito

0.1.1 (2015-04-09)
------------------
* (Feature) More friction for better uphill climbing.
* (Doc) Elaborate instruction.
* Contributors: Isaac IY Saito

0.1.0 (2015-03-22)
------------------
* Initial release into ROS buildfarm.
* Add kinematic parameters obtained from designers.
* Run keyboardteleop by default.
* Add joystick.html example for keyboardteleop
* Add gazebo_ros_diff_drive until https://github.com/ros-simulation/gazebo_ros_pkgs/pull/298 is merged
* [model.sdf] set surface parameters, not sure if this is correct
* [apollo15_landing_site_1000x1000] add new model, near dune crater
* remove dummy hight map, which is fixed in https://bitbucket.org/osrf/gzweb/pull-request/75/fix-loading-heightmap-with-one-texture/diff
* [tetris_description] update model parameters, not sure if this is correct
* [tetris.urdf.xacro] add hardwareInterface to joint
* Contributors: Tokyo Opensource Robotics Programmer 534o, Isaac IY Saito

0.0.1 (2015-01-14)
------------------
