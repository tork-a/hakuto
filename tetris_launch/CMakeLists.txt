cmake_minimum_required(VERSION 2.8.3)
project(tetris_launch)

find_package(catkin REQUIRED COMPONENTS rostest)

catkin_package()

install(DIRECTORY launch test www
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
  USE_SOURCE_PERMISSIONS)

add_rostest(test/tetris.test)


