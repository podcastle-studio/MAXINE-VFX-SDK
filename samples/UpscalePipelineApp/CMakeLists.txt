set(SOURCE_FILES UpscalePipeline.cpp ../../nvvfx/src/NVVideoEffectsProxy.cpp ../../nvvfx/src/nvCVImageProxy.cpp)

# Set Visual Studio source filters
source_group("Source Files" FILES ${SOURCE_FILES})

add_executable(UpscalePipelineApp ${SOURCE_FILES})
target_include_directories(UpscalePipelineApp PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/../utils
    )
target_include_directories(UpscalePipelineApp PUBLIC
    ${SDK_INCLUDES_PATH}
    )

target_link_libraries(UpscalePipelineApp PUBLIC
    NVVideoEffects
    NVCVImage
    OpenCV
    TensorRT
    CUDA
    )