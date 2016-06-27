cmake_minimum_required(VERSION 2.8)
project(SKCF-Tracker)

get_directory_property(HAS_PARENT PARENT_DIRECTORY)

set(PROJECT_SOURCE_DIR "${PROJECT_SOURCE_DIR}/src")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread")

set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} -O0 -g")

set(SKCF_INCLUDE "${CMAKE_CURRENT_SOURCE_DIR}/src")
if (HAS_PARENT)
    set(SKCF_INCLUDE ${SKCF_INCLUDE} PARENT_SCOPE)
endif()
include_directories(${SKCF_INCLUDE})

find_package(OpenCV REQUIRED video videoio imgproc imgcodecs)
include_directories(${OpenCV_INCLUDE_DIRS})

add_library(skcf ${PROJECT_SOURCE_DIR}/gradient
                 ${PROJECT_SOURCE_DIR}/ktrackers)
target_link_libraries(skcf ${OpenCV_LIBS})
