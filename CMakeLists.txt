cmake_minimum_required(VERSION 2.8.3)
project(laser_scan_combiner)

add_definitions(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  tf
  pcl_ros
  sensor_msgs
)

catkin_package(
  CATKIN_DEPENDS roscpp tf pcl_ros sensor_msgs
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(combine_laser_scans src/combine_laser_scans.cpp)

target_link_libraries(combine_laser_scans
  ${catkin_LIBRARIES}
)

install(TARGETS combine_laser_scans 
  ARCHIVE DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  LIBRARY DESTINATION ${CATKIN_PACKAGE_LIB_DESTINATION}
  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
)

install(DIRECTORY launch
  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}
)

