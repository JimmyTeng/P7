cmake_minimum_required(VERSION 2.8)
project(P7_Test_Cpp)
include_directories(../../include)
include_directories(../../p7_shared)
include_directories(../../p7_shared/Platforms/Linux_x86)

add_executable (P7_Test Main.cpp)
target_link_libraries (P7_Test p7 pthread dl rt)

