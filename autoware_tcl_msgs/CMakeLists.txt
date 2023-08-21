cmake_minimum_required(VERSION 3.5)

project(autoware_tcl_msgs)

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()
if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)
find_package(sensor_msgs REQUIRED)
find_package(std_msgs REQUIRED)
find_package(tcl_std_msgs REQUIRED)
find_package(tier4_perception_msgs REQUIRED)
find_package(autoware_auto_perception_msgs REQUIRED)
find_package(autoware_auto_planning_msgs REQUIRED)
find_package(autoware_auto_vehicle_msgs REQUIRED)

# declare the message files to generate code for
set(msg_files
  "msg/DetectedObjectsWithFeature.msg"
  "msg/DetectedObjects.msg"
  "msg/PredictedObjects.msg"
  "msg/TrackedObjects.msg"
  "msg/Path.msg"
  "msg/PathWithLaneId.msg"
  "msg/Trajectory.msg"
  "msg/PointCloud2.msg"
  "msg/VelocityReport.msg"
  "msg/TwistWithCovarianceStamped.msg"
  "msg/Odometry.msg"
  "msg/PoseWithCovarianceStamped.msg"
  "msg/CompressedImage.msg"
  "msg/Image.msg"
)

rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
  DEPENDENCIES 
  sensor_msgs 
  std_msgs 
  tcl_std_msgs 
  tier4_perception_msgs 
  autoware_auto_perception_msgs 
  autoware_auto_planning_msgs
  autoware_auto_vehicle_msgs
  ADD_LINTER_TESTS
)

ament_export_dependencies(rosidl_default_runtime)

ament_package()
