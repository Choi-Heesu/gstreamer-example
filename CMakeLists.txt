CMAKE_MINIMUM_REQUIRED(VERSION 3.14)

PROJECT(gstreamer-example) #Project name

SET(CMAKE_CXX_STANDARD 14) #setting C++ 14 standard
FIND_PACKAGE(PkgConfig) #finding pkg-config is a helper tool

#using pkg-config to getting Gstreamer
PKG_CHECK_MODULES(GSTREAMER REQUIRED gstreamer-1.0)
PKG_CHECK_MODULES(GLIB REQUIRED glib-2.0)

#including GStreamer header files directory
INCLUDE_DIRECTORIES(PUBLIC
  ${GLIB_INCLUDE_DIRS}
  ${GSTREAMER_INCLUDE_DIRS}
  )

#linking GStreamer library directory
LINK_DIRECTORIES(PUBLIC
  ${GLIB_LIBRARY_DIRS}
  ${GSTREAMER_LIBRARY_DIRS}
  )

#building target executable
ADD_EXECUTABLE(${PROJECT_NAME} src/example_01.cpp)

#linking Gstreamer library with target executable
TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${GSTREAMER_LIBRARIES})

