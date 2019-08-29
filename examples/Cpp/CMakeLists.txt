cmake_minimum_required(VERSION 2.8)
project(P7_Cpp_Example)
include_directories(../../include)
include_directories(../../p7_shared)

add_executable (P7_Cpp Main.cpp)
target_link_libraries (P7_Cpp p7 pthread dl rt)

