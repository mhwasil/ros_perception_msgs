cmake_minimum_required(VERSION 2.8.3)
project(ros_perception_msgs)

find_package(catkin REQUIRED
  COMPONENTS
    genmsg
    actionlib_msgs
    actionlib
    geometry_msgs
    message_generation
    roscpp
    rospy
    sensor_msgs
    std_msgs
    visualization_msgs
)

#add_action_files(DIRECTORY action
#  FILES
#    DetectScene.action
#)

add_message_files(
  FILES
    BoundingBox.msg
    BoundingBoxList.msg
    BoundingBox2D.msg
    ImageList.msg
    Object.msg
    ObjectList.msg
    PlanarPolygon.msg
    ImageCloud.msg
)

add_service_files(
  FILES
    GetSegmentedImage.srv
    RecognizeImage.srv
    RecognizeObject.srv
)

generate_messages(
  DEPENDENCIES
    geometry_msgs
    sensor_msgs
    std_msgs
    actionlib_msgs
)

catkin_package(
  CATKIN_DEPENDS
    geometry_msgs
    message_runtime
    sensor_msgs
    std_msgs
)

include_directories(
  ${catkin_INCLUDE_DIRS}
)

### EXECUTABLES ###
#add_executable(object_msg_visualizer_node
#  ros/src/object_msg_visualizer_node.cpp
#)
#add_dependencies(object_msg_visualizer_node
#  ${catkin_EXPORTED_TARGETS}
#  ${PROJECT_NAME}_gencpp
#)
#target_link_libraries(object_msg_visualizer_node
#  ${catkin_LIBRARIES}
#)

### TESTS
#if(CATKIN_ENABLE_TESTING)
#  find_package(roslaunch REQUIRED)

#  roslaunch_add_file_check(ros/launch)
#endif()


### INSTALLS
#install(
#  TARGETS
#    object_msg_visualizer_node
#  RUNTIME DESTINATION ${CATKIN_PACKAGE_BIN_DESTINATION}
#)

##install(DIRECTORY ros/launch
#  DESTINATION ${CATKIN_PACKAGE_SHARE_DESTINATION}/ros/launch
#)
