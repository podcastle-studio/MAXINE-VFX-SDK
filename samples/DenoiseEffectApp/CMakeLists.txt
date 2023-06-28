set(SOURCE_FILES DenoiseEffectApp.cpp ../../nvvfx/src/NVVideoEffectsProxy.cpp ../../nvvfx/src/nvCVImageProxy.cpp)

# Set Visual Studio source filters
source_group("Source Files" FILES ${SOURCE_FILES})

add_executable(DenoiseEffectApp ${SOURCE_FILES})
target_include_directories(DenoiseEffectApp PRIVATE ${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_SOURCE_DIR}/../utils)
target_include_directories(DenoiseEffectApp PUBLIC ${SDK_INCLUDES_PATH})

target_link_libraries(DenoiseEffectApp PUBLIC
    NVVideoEffects
    NVCVImage
    OpenCV
    TensorRT
    CUDA
    )
