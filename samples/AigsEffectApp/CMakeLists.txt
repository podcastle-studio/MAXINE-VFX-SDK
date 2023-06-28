set(SOURCE_FILES
    AigsEffectApp.cpp
    ../../nvvfx/src/NVVideoEffectsProxy.cpp
    ../../nvvfx/src/nvCVImageProxy.cpp)

source_group("Source Files" FILES ${SOURCE_FILES})

add_executable(AigsEffectApp ${SOURCE_FILES})
target_include_directories(AigsEffectApp PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}
    ${CMAKE_CURRENT_SOURCE_DIR}/../utils
    )
target_include_directories(AigsEffectApp PUBLIC
    ${SDK_INCLUDES_PATH}
    )


target_link_libraries(AigsEffectApp PUBLIC
    NVVideoEffects
    NVCVImage
    OpenCV
    TensorRT
    CUDA
    )

