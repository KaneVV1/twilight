cmake_minimum_required(VERSION 3.15)
project(twilight)

set(CMAKE_CXX_STANDARD 17)

find_package(Boost)

include_directories(3rdparty)

add_executable(twilight src/twilight.cpp)