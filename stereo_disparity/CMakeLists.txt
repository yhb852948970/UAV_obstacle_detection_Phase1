cmake_minimum_required(VERSION 2.8.3)
project(stereo_disparity)

find_package(catkin REQUIRED COMPONENTS
  geometry_msgs
  cv_bridge
  image_transport
  pcl_ros
  roscpp
  sensor_msgs
  std_msgs
  tf
)
find_package(OpenCV REQUIRED core highgui imgproc calib3d contrib)

catkin_package(
   LIBRARIES stereo_disparity
   CATKIN_DEPENDS common_msgs cv_bridge geometry image_transport pcl_ros roscpp sensor_msgs std_msgs tf
   DEPENDS system_lib
)

SET(CMAKE_BUILD_TYPE release) 

include_directories( ${catkin_INCLUDE_DIRS} ${OpenCV_INCLUDE_DIRS} )
add_executable(stereo_disparity_node src/stereo_disparity.cpp)
target_link_libraries(stereo_disparity_node ${catkin_LIBRARIES} ${OpenCV_LIBRARIES})





