cmake_minimum_required(VERSION 3.14)
project(p7)

# common settings
if (NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif ()
message("Build type: " ${CMAKE_BUILD_TYPE})

if (NOT CMAKE_SYSTEM_PROCESSOR)
    set(CMAKE_SYSTEM_PROCESSOR "x86_64")
endif ()

set(CMAKE_CXX_STANDARD 14)
#设置库文件路径
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/lib)
#设置可执行程序路径
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/bin)

add_library(${PROJECT_NAME} STATIC
        src/ClBaical.h
        src/ClFile.h
        src/Client.h
        src/ClNull.h
        src/ClText.h
        src/ClTextConsole.h
        src/ClTextFile.h
        src/ClTextSink.h
        src/ClTextSyslog.h
        src/Common.h
        src/CommonClient.h
        src/Formatter.h
        src/PacketsPool.h
        src/resource.h
        src/targetver.h
        src/Telemetry.h
        src/Trace.h
        src/TPackets.h
        src/ClBaical.cpp
        src/ClFile.cpp
        src/Client.cpp
        src/ClNull.cpp
        src/ClText.cpp
        src/CRC32.cpp
        src/Telemetry.cpp
        src/Proxy.cpp
        src/Trace.cpp
        )

target_include_directories(${PROJECT_NAME}
        PUBLIC src
        PUBLIC include
        PUBLIC p7_shared
        PUBLIC p7_shared/Platforms/Linux_x86
        )
INSTALL(TARGETS p7 DESTINATION ${CMAKE_INSTALL_PREFIX}/lib)
INSTALL(DIRECTORY include/p7 DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
INSTALL(DIRECTORY p7_shared DESTINATION ${CMAKE_INSTALL_PREFIX}/include)
if (CMAKE_SYSTEM_PROCESSOR STREQUAL "x86_64")
    add_subdirectory(examples/Cpp)
    add_subdirectory(tests/Trace)
    add_subdirectory(tests/Speed)
endif ()
