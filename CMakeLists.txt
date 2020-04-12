cmake_minimum_required(VERSION 3.15)

project(Twilight)
set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

set(CMAKE_CXX_STANDARD 17)

find_package(Boost REQUIRED)
find_package(Glog REQUIRED)

file(GLOB_RECURSE INCLUDE_FILES src/*.h)
file(GLOB_RECURSE LIBRARY_FILES src/*.cpp)

set(INCLUDE_DIRS
        3rdparty
        ${Boost_INCLUDE_DIRS}
        ${GLOG_INCLUDE_DIRS}
        ${INCLUDE_FILES}
)

set(LIBRARIES
        ${Boost_LIBRARIES}
        ${GLOG_LIBRARIES}
)

add_subdirectory(3rdparty/fmt)

include_directories(${INCLUDE_DIRS} ${CMAKE_CURRENT_SOURCE_DIR}/fmt)

add_library(STATIC ${LIBRARY_FILES})

add_executable(twilight src/Twilight.cpp)

target_link_libraries(twilight ${LIBRARIES} ${LIBRARY_FILES} 3rdparty/fmt)
