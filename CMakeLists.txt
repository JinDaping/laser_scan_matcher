cmake_minimum_required(VERSION 2.4.6)
include($ENV{ROS_ROOT}/core/rosbuild/rosbuild.cmake)

# Set the build type.  Options are:
#  Coverage       : w/ debug symbols, w/o optimization, w/ code-coverage
#  Debug          : w/ debug symbols, w/o optimization
#  Release        : w/o debug symbols, w/ optimization
#  RelWithDebInfo : w/ debug symbols, w/ optimization
#  MinSizeRel     : w/o debug symbols, w/ optimization, stripped binaries
#set(ROS_BUILD_TYPE RelWithDebInfo)

rosbuild_init()

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)

#Include csm project code and compile it
include( ${CMAKE_CURRENT_SOURCE_DIR}/csm/GetCSM.cmake )
download_and_compile_csm()

find_package(PCL REQUIRED QUIET)
include_directories(${csm_INCLUDE_DIRS} ${PCL_INCLUDE_DIRS})

#uncomment if you have defined messages
#rosbuild_genmsg()
#uncomment if you have defined services
#rosbuild_gensrv()

#common commands for building c++ executables and libraries
#rosbuild_add_library(${PROJECT_NAME} src/example.cpp)
#target_link_libraries(${PROJECT_NAME} another_library)
#rosbuild_add_boost_directories()
#rosbuild_link_boost(${PROJECT_NAME} thread)
#rosbuild_add_executable(example examples/example.cpp)
#target_link_libraries(example ${PROJECT_NAME})

rosbuild_add_library(laser_scan_matcher src/laser_scan_matcher.cpp)
target_link_libraries( laser_scan_matcher ${csm_LIBRARIES})
add_dependencies(laser_scan_matcher ${csm_EXPORTED_TARGETS})
#Creating Nodelet
rosbuild_add_library(laser_scan_matcher_nodelet src/laser_scan_matcher_nodelet.cpp)
target_link_libraries(laser_scan_matcher_nodelet laser_scan_matcher)
#Create node
rosbuild_add_executable(laser_scan_matcher_node src/laser_scan_matcher_node.cpp)
target_link_libraries( laser_scan_matcher_node laser_scan_matcher )
install_csm()
