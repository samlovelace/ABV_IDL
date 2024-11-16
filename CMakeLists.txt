cmake_minimum_required(VERSION 3.8)
project(abv_idl)

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
find_package(rosidl_default_generators REQUIRED)

# Specify message files
set(msg_files
    "msg/AbvVec3.msg"
    "msg/AbvCommand.msg"
    "msg/AbvResponse.msg"
    "msg/AbvState.msg"
)

# Generate the C++ interfaces from the message files
rosidl_generate_interfaces(${PROJECT_NAME}
  ${msg_files}
)

# Export runtime dependencies
ament_export_dependencies(rosidl_default_runtime)
ament_package()
