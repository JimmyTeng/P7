cmake_minimum_required(VERSION 3.14)
project(P7)

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
set(LIBRARY_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/Binaries)
#设置可执行程序路径
set(EXECUTABLE_OUTPUT_PATH ${PROJECT_SOURCE_DIR}/Binaries)

add_library(${PROJECT_NAME} SHARED
        Sources/ClBaical.h
        Sources/ClFile.h
        Sources/Client.h
        Sources/ClNull.h
        Sources/ClText.h
        Sources/ClTextConsole.h
        Sources/ClTextFile.h
        Sources/ClTextSink.h
        Sources/ClTextSyslog.h
        Sources/Common.h
        Sources/CommonClient.h
        Sources/Formatter.h
        Sources/PacketsPool.h
        Sources/resource.h
        Sources/targetver.h
        Sources/Telemetry.h
        Sources/Trace.h
        Sources/TPackets.h
        Sources/ClBaical.cpp
        Sources/ClFile.cpp
        Sources/Client.cpp
        Sources/ClNull.cpp
        Sources/ClText.cpp
        Sources/CRC32.cpp
        Sources/Telemetry.cpp
        Sources/Proxy.cpp
        Sources/Trace.cpp
        )


target_include_directories(${PROJECT_NAME}
        PUBLIC Sources
        PUBLIC Headers
        PUBLIC Shared
        PUBLIC Shared/Platforms/Linux_x86
        )

add_subdirectory(Examples/Cpp)
add_subdirectory(Tests/Trace)
add_subdirectory(Tests/Speed)