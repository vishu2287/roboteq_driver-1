# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)

set(ROS_ROOT $ENV{ROS_ROOT})

option(SERIAL_UTILS_BUILD_WIHOUT_ROS "Build without ROS?" OFF)

if(DEFINED ROS_ROOT AND NOT SERIAL_UTILS_BUILD_WIHOUT_ROS)
  # Build with ROS
  include(serial_utils_ros.cmake)
  message("Building with ROS")
  build_serial_utils()
else(DEFINED ROS_ROOT AND NOT SERIAL_UTILS_BUILD_WIHOUT_ROS)
  # Build normally
  include(serial_utils.cmake)
  message("Building stand alone")
  build_serial_utils()
endif(DEFINED ROS_ROOT AND NOT SERIAL_UTILS_BUILD_WIHOUT_ROS)
