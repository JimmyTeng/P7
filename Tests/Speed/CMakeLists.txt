cmake_minimum_required(VERSION 2.8)
project(P7_SPEED_Cpp)
include_directories(./../../Headers)
include_directories(./../../Shared)
include_directories(./../../Shared/Platforms/Linux_x86)

add_executable (P7_SPEED_Cpp Speed.cpp)
target_link_libraries (P7_SPEED_Cpp P7 pthread dl rt)

