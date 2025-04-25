cmake_minimum_required(VERSION 2.8.3)
project(robotic_arm)

## Find catkin macros and libraries
find_package(catkin REQUIRED COMPONENTS
  roscpp
  rospy
  std_msgs
  urdf
  gazebo_ros
  controller_manager
  joint_state_controller
  effort_controllers
  robot_state_publisher
)

## Find Gazebo
find_package(gazebo REQUIRED)

###################################
## Catkin-specific configuration ##
###################################
catkin_package(
  CATKIN_DEPENDS roscpp rospy std_msgs urdf gazebo_ros controller_manager
)

#############
## Install ##
#############

foreach(dir config launch meshes urdf)
  install(DIRECTORY ${dir}/
    DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/${dir})
endforeach()

#############
## Build + Linking (Optional if no C++ nodes) ##
#############

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${GAZEBO_INCLUDE_DIRS}
)

link_directories(
  ${GAZEBO_LIBRARY_DIRS}
)

# If you have source files, uncomment and modify the following:
# add_executable(my_node src/my_node.cpp)
# target_link_libraries(my_node ${catkin_LIBRARIES} ${GAZEBO_LIBRARIES})