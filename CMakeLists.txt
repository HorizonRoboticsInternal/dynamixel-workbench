cmake_minimum_required(VERSION 3.5)
project(dynamixel_workbench_toolbox)

if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

find_package(dynamixel_sdk REQUIRED)
include_directories(
  include
)

set(dependencies_lib
  "dynamixel_sdk"
)

set(LIB_NAME "dynamixel_workbench_toolbox")

add_library(${LIB_NAME} SHARED
  src/${PROJECT_NAME}/dynamixel_item.cpp
  src/${PROJECT_NAME}/dynamixel_driver.cpp
  src/${PROJECT_NAME}/dynamixel_tool.cpp
  src/${PROJECT_NAME}/dynamixel_workbench.cpp
)

install(TARGETS ${LIB_NAME}
  ARCHIVE DESTINATION lib
  LIBRARY DESTINATION lib
  RUNTIME DESTINATION bin/${PROJECT_NAME}
)

install(
  DIRECTORY
    include/
  DESTINATION
    include/
)
