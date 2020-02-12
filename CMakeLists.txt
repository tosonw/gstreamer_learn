cmake_minimum_required(VERSION 3.5)
project(gstreamer_learn)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED TRUE)
SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -pthread -g")


MESSAGE(STATUS "operation system is ${CMAKE_SYSTEM}")
MESSAGE(STATUS "CMAKE_SYSTEM_NAME is ${CMAKE_SYSTEM}")
IF (CMAKE_SYSTEM_NAME MATCHES "Linux")
    MESSAGE(STATUS "current platform: Linux ")
ELSEIF (CMAKE_SYSTEM_NAME MATCHES "Windows")
    MESSAGE(STATUS "current platform: Windows")
ELSEIF (CMAKE_SYSTEM_NAME MATCHES "FreeBSD")
    MESSAGE(STATUS "current platform: FreeBSD")
ELSE ()
    MESSAGE(STATUS "other platform: ${CMAKE_SYSTEM_NAME}")
ENDIF (CMAKE_SYSTEM_NAME MATCHES "Linux")


if(${CMAKE_SYSTEM} MATCHES "Linux-4.9.140-tegra")
    message("On TEGRA PLATFORM.")
    add_definitions(-DPLATFORM_TEGRA)
    set(SYS_USR_LIB /usr/lib/aarch64-linux-gnu)
    set(SYS_LIB /lib/aarch64-linux-gnu)
    set(DS_LIB /opt/nvidia/deepstream/deepstream-4.0/lib)
else()
    message("On X86 PLATFORM.")
    set(SYS_USR_LIB /usr/lib/x86_64-linux-gnu)
    set(SYS_LIB /lib/x86_64-linux-gnu)
endif()

include_directories(
        includes
        /usr/include/gstreamer-1.0
        /usr/include/glib-2.0
        ${SYS_USR_LIB}/glib-2.0/include
)
link_libraries(
        ${SYS_USR_LIB}/libgtk3-nocsd.so.0
        ${SYS_USR_LIB}/libgstreamer-1.0.so.0
        ${SYS_USR_LIB}/libgobject-2.0.so.0
        ${SYS_USR_LIB}/libglib-2.0.so.0
        ${SYS_LIB}/libc.so.6
#        /lib/ld-linux-aarch64.so.1
        ${SYS_LIB}/libdl.so.2
        ${SYS_LIB}/libpthread.so.0
        ${SYS_USR_LIB}/libgmodule-2.0.so.0
        ${SYS_LIB}/libm.so.6
        ${SYS_USR_LIB}/libffi.so.6
        ${SYS_LIB}/libpcre.so.3
)

add_executable(demo_1_version_ demo_gstreamer_1_version.cpp)
add_executable(demo_2_init_ demo_gstreamer_2_init.cpp)
add_executable(demo_3_element_fac_ demo_gstreamer_3_element_factory.cpp)
add_executable(demo_4_get_element_info_ demo_gstreamer_4_get_element_info.cpp)
add_executable(demo_5_link_elements_ demo_gstreamer_5_link_elements.cpp)
add_executable(demo_6_pads_ demo_gstreamer_6_pads.cpp)
add_executable(demo_8_helloworld_ demo_gstreamer_8_helloworld.cpp)

add_executable(demo_gstreamer_rtsp_ demo_gstreamer_rtsp.cpp)

