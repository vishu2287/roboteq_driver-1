# Catkin User Guide: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/user_guide.html
# Catkin CMake Standard: http://www.ros.org/doc/groovy/api/catkin/html/user_guide/standards.html
cmake_minimum_required(VERSION 2.8.3)

set(ROS_ROOT $ENV{ROS_ROOT})

if(DEFINED ROS_ROOT)
  option(SERIAL_BUILD_WIHOUT_ROS "Build without ROS?" OFF)
else(DEFINED ROS_ROOT)
  option(SERIAL_BUILD_WIHOUT_ROS "Build without ROS?" ON)
endif(DEFINED ROS_ROOT)

if(DEFINED ROS_ROOT AND NOT SERIAL_BUILD_WIHOUT_ROS)
  # Build with ROS
  include(serial_ros.cmake)
  message("Building with ROS")
  build_serial()
else(DEFINED ROS_ROOT AND NOT SERIAL_BUILD_WIHOUT_ROS)
  # Build normally
  include(serial.cmake)
  message("Building stand alone")
  build_serial()
endif(DEFINED ROS_ROOT AND NOT SERIAL_BUILD_WIHOUT_ROS)
