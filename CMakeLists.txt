cmake_minimum_required(VERSION 2.8)

# project name
project(rpi0-oled-mp3)

set(SOURCES ${PROJECT_SOURCE_DIR}/rpi0-oled-mp3.c
    ${PROJECT_SOURCE_DIR}/rpi0-oled-mp3.h
    ${PROJECT_SOURCE_DIR}/rotaryencoder.c
    ${PROJECT_SOURCE_DIR}/rotaryencoder.h)

set(CMAKE_BINARY_DIR ${CMAKE_SOURCE_DIR}/bin)
#set(CMAKE_SOURCE_DIR ${CMAKE
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR})
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR})

# The following folder will be included
include_directories("${PROJECT_SOURCE_DIR}")
#add_library(ao mpg123 pthread m wiringPi wiringPiDev asound)

#find_package(libao-dev REQUIRED libasound-dev REQUIRED)
find_file(/usr/local/include/wiringPi.h /usr/include/wiringPi.h)

add_executable(rpi0-oled-mp3 ${PROJECT_SOURCE_DIR}/rpi0-oled-mp3.c rpi0-oled-mp3.h rotaryencoder.c rotaryencoder.h oled96.h)
target_link_libraries( rpi0-oled-mp3 ao mpg123 pthread m wiringPi wiringPiDev asound oled96 )
