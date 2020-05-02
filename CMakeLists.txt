cmake_minimum_required(VERSION 3.6)
project(arduino-linux-abstraction)

set(CMAKE_CXX_STANDARD 11)

include_directories(src)

set(ABSTRACTION_FILES
        src/Arduino.h
        src/Arduino.cpp
        src/SD.h
        src/SD.cpp
        )

if (${BUILD_LINUX_RH_SERIAL})
    # The RH_SERIAL transport uses RadioHead - be sure this module knows it.
    add_definitions(-DRH_PLATFORM)
endif (${BUILD_LINUX_RH_SERIAL})

add_library(arduino-linux-abstraction ${ABSTRACTION_FILES})
