cmake_minimum_required(VERSION 3.10)

project(NvVideoEffects_SDK CXX)

# Set common build path for all targets
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake" ${CMAKE_MODULE_PATH})

# Require C++11 and disable non-standard extensions
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

# Add target for NVVideoEffects
add_library(NVVideoEffects INTERFACE)

# found in different locations depending on type of package
find_path(VideoFX_INCLUDES
        NAMES nvVideoEffects.h
        PATHS
        /usr/local/VideoFX/include
        /usr/include/x86_64-linux-gnu
        /usr/include
        REQUIRED
        )

target_include_directories(NVVideoEffects INTERFACE ${VideoFX_INCLUDES})
set(SDK_INCLUDES_PATH ${VideoFX_INCLUDES})

find_library(VideoFX_LIB
        NAMES libVideoFX.so
        PATHS
        /usr/local/VideoFX/lib
        /usr/lib/x86_64-linux-gnu
        /usr/lib64
        /usr/lib
        REQUIRED
        NO_DEFAULT_PATH)

target_link_libraries(NVVideoEffects INTERFACE "${VideoFX_LIB}")
message(STATUS "VideoFX_LIB: ${VideoFX_LIB}")
message(STATUS "SDK_INCLUDES_PATH: ${SDK_INCLUDES_PATH}")


# Add target for NVCVImage
add_library(NVCVImage INTERFACE)
# found in different locations depending on type of package
find_path(NVCVImage_INCLUDES
        NAMES nvCVImage.h
        PATHS
        /usr/local/VideoFX/include
        /usr/include/x86_64-linux-gnu
        /usr/include
        REQUIRED
        )
target_include_directories(NVCVImage INTERFACE ${NVCVImage_INCLUDES})
find_library(NVCVImage_LIB
        NAMES libNVCVImage.so
        PATHS
        /usr/local/VideoFX/lib
        /usr/lib/x86_64-linux-gnu
        /usr/lib64
        /usr/lib
        REQUIRED
        NO_DEFAULT_PATH)
target_link_libraries(NVCVImage INTERFACE "${NVCVImage_LIB}")
message(STATUS "NVCVImage_LIB: ${NVCVImage_LIB}")
message(STATUS "NVCVImage_INCLUDES_PATH: ${NVCVImage_INCLUDES}")

add_subdirectory(samples)
