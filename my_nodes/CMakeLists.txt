cmake_minimum_required(VERSION 3.5)
project(my_nodes)

# Default to C++17
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 17)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(ament_cmake REQUIRED)
find_package(my_interfaces REQUIRED)
find_package(rclcpp REQUIRED)

add_executable(my_node src/node.cpp)
ament_target_dependencies(my_node
  my_interfaces rclcpp
)
install(TARGETS
  my_node
  DESTINATION lib/${PROJECT_NAME})

ament_package()
