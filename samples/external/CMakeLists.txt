#######################
# Interface to OpenCV #
#######################

find_package(OpenCV REQUIRED PATHS /usr /usr/local PATH_SUFFIXES share/OpenCV share/opencv4)
add_library(OpenCV INTERFACE)
target_include_directories(OpenCV INTERFACE ${OpenCV_INCLUDE_DIRS})
target_link_libraries(OpenCV INTERFACE ${OpenCV_LIBRARIES})
message(STATUS "OpenCV_INCLUDE_DIRS ${OpenCV_INCLUDE_DIRS}")
message(STATUS "OpenCV_LIBRARIES ${OpenCV_LIBRARIES}")

find_package(CUDA 11.3 REQUIRED)
add_library(CUDA INTERFACE)
target_include_directories(CUDA INTERFACE ${CUDA_INCLUDE_DIRS})
target_link_libraries(CUDA INTERFACE "${CUDA_LIBRARIES};cuda")
message(STATUS "CUDA_INCLUDE_DIRS ${CUDA_INCLUDE_DIRS}")
message(STATUS "CUDA_LIBRARIES ${CUDA_LIBRARIES}")

set(TENSORRT_DIR "/usr/local/TensorRT-8.5.1.7")
# find_package(TensorRT 8 REQUIRED)
set(LIBRARY_FOLDER ${TENSORRT_DIR}/lib)
file(GLOB TensorRT_LIBRARIES "${LIBRARY_FOLDER}/*.so")
set(TensorRT_INCLUDE_DIRS ${TENSORRT_DIR}/include)
add_library(TensorRT INTERFACE)
target_include_directories(TensorRT INTERFACE ${TensorRT_INCLUDE_DIRS})
target_link_libraries(TensorRT INTERFACE ${TensorRT_LIBRARIES})
message(STATUS "TensorRT_INCLUDE_DIRS ${TensorRT_INCLUDE_DIRS}")
message(STATUS "TensorRT_LIBRARIES ${TensorRT_LIBRARIES}")