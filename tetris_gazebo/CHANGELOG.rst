^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package tetris_gazebo
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Forthcoming
-----------
* Add gazebo_ros_diff_drive until https://github.com/ros-simulation/gazebo_ros_pkgs/pull/298 is merged
* [model.sdf] set surface parameters, not sure if this is correct
* [apollo15_landing_site_1000x1000] add new model, near dune crater
* remove dummy hight map, which is fixed in https://bitbucket.org/osrf/gzweb/pull-request/75/fix-loading-heightmap-with-one-texture/diff
* Contributors: Isaac IY Saito, Tokyo Opensource Robotics Programmer 534o

0.0.1 (2015-01-14)
------------------
* install models
* use export gaebo_ros tag to specify gazebo_media_path and gazebo_model_path
* copy models/apollo15_landing_site_1000x1000 from https://bitbucket.org/osrf/gazebo_models/pull-request/115/add-apollo15_landing_site_1000x/diff
* Fix typo
* Add run_depend to install libgazebo_ros_control.so.
* add tetris_gazebo, this package requires apollo_15_landing_site, https://bitbucket.org/osrf/gazebo_models/pull-request/115/add-apollo15_landing_site_1000x/diff
* Contributors: Isaac IY Saito, Tokyo Opensource Robotics Programmer 534o
