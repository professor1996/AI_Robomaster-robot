cmake_minimum_required(VERSION 2.8.3)
project(control)

## Compile as C++11, supported in ROS Kinetic and newer
 add_compile_options(-std=c++11)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  roscpp
  rospy
  std_msgs
  message_generation
whurobot_msgs
nav_msgs
sensor_msgs
tf
tf2
move_base_msgs
)


catkin_package(
#  INCLUDE_DIRS include
#  LIBRARIES serial
CATKIN_DEPENDS geometry_msgs roscpp rospy std_msgs whurobot_msgs nav_msgs tf sensor_msgs tf2 move_base_msgs
#  DEPENDS system_lib
)



include_directories(
 include
  ${catkin_INCLUDE_DIRS} 
)


 add_executable(control_node src/MainControl.cpp)

 target_link_libraries(control_node
   ${catkin_LIBRARIES}
 )


 add_executable(odom_broadcaster src/odom_broadcaster.cpp)

 target_link_libraries(odom_broadcaster
   ${catkin_LIBRARIES} 
 )

 add_executable(enemy_listen src/enemy_listen.cpp)

 target_link_libraries(enemy_listen
   ${catkin_LIBRARIES} 
 )
