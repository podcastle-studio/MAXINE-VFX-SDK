set(SOURCE_FILES VideoEffectsApp.cpp ../../nvvfx/src/NVVideoEffectsProxy.cpp ../../nvvfx/src/nvCVImageProxy.cpp)

# Set Visual Studio source filters
source_group("Source Files" FILES ${SOURCE_FILES})

add_executable(VideoEffectsApp ${SOURCE_FILES})
target_include_directories(VideoEffectsApp PRIVATE ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../utils)
target_include_directories(VideoEffectsApp PUBLIC ${SDK_INCLUDES_PATH})

target_link_libraries(VideoEffectsApp PUBLIC
    NVVideoEffects
    NVCVImage
    OpenCV
    TensorRT
    CUDA
    )
