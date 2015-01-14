cmake_minimum_required(VERSION 2.8.3)
project(tetris_gazebo)

find_package(catkin REQUIRED COMPONENTS)

catkin_package()

install(DIRECTORY launch worlds models
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  USE_SOURCE_PERMISSIONS)
