cmake_minimum_required(VERSION 3.5)
project(harpia_simulator)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

if(BUILD_TESTING)
  find_package(autoware_testing REQUIRED)
  add_smoke_test(${PROJECT_NAME} ${NODE_NAME})
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(gazebo_ros REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

# Install
install(
  DIRECTORY launch models worlds 
  DESTINATION share/${PROJECT_NAME}
)


ament_export_dependencies(ament_cmake)
ament_export_dependencies(gazebo_ros)
ament_package()