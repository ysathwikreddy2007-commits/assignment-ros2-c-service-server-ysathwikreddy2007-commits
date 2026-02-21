cmake_minimum_required(VERSION 3.8)
project(ros2_service_server)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# ==============================
# Find Dependencies
# ==============================
find_package(ament_cmake REQUIRED)
find_package(rclcpp REQUIRED)
find_package(example_interfaces REQUIRED)

# ==============================
# Add Executable
# ==============================
add_executable(add_two_ints_server src/add_two_ints_server.cpp)

# ==============================
# Link Dependencies
# ==============================
ament_target_dependencies(add_two_ints_server
  rclcpp
  example_interfaces
)

# ==============================
# Install Target
# ==============================
install(TARGETS
  add_two_ints_server
  DESTINATION lib/${PROJECT_NAME}
)

# ==============================
# Testing
# ==============================
if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
