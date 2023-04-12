# CMakeLists.txt
#
# Depends on a complete build of MBed in the parent project. Because Mbed is
# hard to package without official support, this library is packaged as a
# "header-only" library, despite having implementation files.
#

cmake_minimum_required(VERSION 3.12 FATAL_ERROR)

project(
  4DGL-uLCD-144-MBedOS6
  VERSION 0.0.0
  DESCRIPTION "4DGL-uLCD-144-MBedOS6"
  LANGUAGES C CXX)

# Update source files here.
set(sources src/Control.cpp src/Graphics.cpp src/Media.cpp src/Text.cpp)

# Create library
add_library(4DGL-uLCD-144-MBedOS6 INTERFACE)
target_include_directories(
  4DGL-uLCD-144-MBedOS6
  INTERFACE $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/src/include>
            $<INSTALL_INTERFACE:include>)
set(sources_) # transform sources for inclusion.
foreach(source ${sources})
  list(APPEND sources_
       "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/${source}>"
       "$<INSTALL_INTERFACE:share/4DGL-uLCD-144-MBedOS6/${source}>")
endforeach()
target_sources(4DGL-uLCD-144-MBedOS6 INTERFACE ${sources_})

# Install library files
install(TARGETS 4DGL-uLCD-144-MBedOS6 EXPORT 4DGL-uLCD-144-MBedOS6Config)
install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/src/include/4DGL-uLCD-144-MBedOS6
        DESTINATION include)
install(FILES ${sources} DESTINATION share/4DGL-uLCD-144-MBedOS6/src)

# Install cmake files
export(EXPORT 4DGL-uLCD-144-MBedOS6Config
       FILE 4DGL-uLCD-144-MBedOS6Config.cmake)
install(
  EXPORT 4DGL-uLCD-144-MBedOS6Config
  FILE 4DGL-uLCD-144-MBedOS6Config.cmake
  DESTINATION share/cmake)
