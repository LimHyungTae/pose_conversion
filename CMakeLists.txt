cmake_minimum_required(VERSION 2.8.3)
project(pose_conversion)

## Compile as C++11, supported in ROS Kinetic and newer
# add_compile_options(-std=c++11)


set(CMAKE_CXX_FLAGS "-std=c++11"
)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  geometry_msgs
  genmsg
  pcl_conversions
  pcl_ros
)

#find_package(PCL REQUIRED)
include_directories(${PCL_INCLUDE_DIRS})
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})


include_directories(
  include
  ${catkin_INCLUDE_DIRS}
  src
)

add_executable(pose_type_conversion src/main.cpp src/pose_conversion.cpp)
add_dependencies(pose_type_conversion ${catkin_EXPORTED_TARGETS})
target_link_libraries(pose_type_conversion ${catkin_LIBRARIES})

