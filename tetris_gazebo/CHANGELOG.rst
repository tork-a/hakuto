^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package tetris_gazebo
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

0.1.4 (2015-11-06)
------------------
* [improved] Sun light is stronger on the Moon
* [fix] Temporary workaround to Gzweb not showing model (`#45 <https://github.com/tork-a/hakuto/issues/45>`_)
* Contributors: Kei Okada, Isaac I.Y. Saito

0.1.3 (2015-04-11)
------------------
* (Improve) Cosmetics; Robot spawned at more adventurous starting pose. Sun location to cast more realistic shadow.
* Contributors: Isaac IY Saito

0.1.2 (2015-04-09)
------------------
* (Feature) Add starry sky scene, earth seen from lunar surface taken by Kaguya, JAXA
* Contributors: Isaac IY Saito

0.1.1 (2015-04-09)
------------------
* More friction for better uphill climbing.
* Contributors: Isaac IY Saito

0.1.0 (2015-03-22)
------------------
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
