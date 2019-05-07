# For more information about using CMake with Android Studio, read the
# documentation: https://d.android.com/studio/projects/add-native-code.html

# Sets the minimum version of CMake required to build the native library.

cmake_minimum_required(VERSION 3.4.1)


set(CMAKE_VERBOSE_MAKEFILE on)
set(COMMON_SOURCE_DIR ${CMAKE_SOURCE_DIR}/../../../../common)

file( GLOB app_src_files
        "src/main/cpp/*.cpp")


add_library(ndk_camera SHARED ${app_src_files})

# now build app's shared lib
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Werror")

target_link_libraries(ndk_camera
        android
        log
        camera2ndk
        mediandk
        )
