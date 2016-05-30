cmake_minimum_required(VERSION 2.8)
project(SKCF-Tracker)

find_package(OpenCV REQUIRED video videoio imgproc imgcodecs)
include_directories(${OpenCV_INCLUDE_DIRS})

set(PROJECT_SOURCE_DIR "${PROJECT_SOURCE_DIR}/src")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -g")

include_directories(${PROJECT_SOURCE_DIR})
add_library(skcf ${PROJECT_SOURCE_DIR}/gradient
                 ${PROJECT_SOURCE_DIR}/ktrackers
                 ${PROJECT_SOURCE_DIR}/skcfdcf)
target_link_libraries(skcf ${OpenCV_LIBS})
