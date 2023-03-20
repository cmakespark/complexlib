cmake_minimum_required(VERSION 3.5.2 FATAL_ERROR)

project(complexlib)

# Download build system
if(DEFINED ENV{CMAKESPARK})
    list(APPEND CMAKE_MODULE_PATH "$ENV{CMAKESPARK}")
    message(STATUS "Using cmakespark from $ENV{CMAKESPARK}")
elseif(DEFINED CMAKESPARK)
    list(APPEND CMAKE_MODULE_PATH "${CMAKESPARK}")
    message(STATUS "Using cmakespark from ${CMAKESPARK}")
else()
    if(NOT EXISTS "${CMAKE_BINARY_DIR}/buildsys")
        message(STATUS "Downloading buildsystem...")

        find_package(Git REQUIRED)
        execute_process(COMMAND ${GIT_EXECUTABLE} clone --branch master https://github.com/cmakespark/cmake.git ${CMAKE_BINARY_DIR}/buildsys)
    endif()
    list(APPEND CMAKE_MODULE_PATH "${CMAKE_BINARY_DIR}/buildsys")
endif()

###############################
# Project specific parameters #
# Change as you see fit       #
###############################

#Set & cache variable version number, Change global QT version number here
set(QT_MAJOR_VERSION_REQUIRED 6 CACHE STRING "QT Major version variable")

option(BUILD_SHARED_LIBS "Build as shared library" OFF)

# Include common cmake modules
include(CommonConfig)

add_subdirectory(complexlib)
add_subdirectory(QComplexLib)
add_subdirectory(complexapp)
