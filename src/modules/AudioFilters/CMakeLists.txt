cmake_minimum_required(VERSION 3.1)
project(AudioFilters)

set(AudioFilters_HDR
    AudioFilters.hpp
    Equalizer.hpp
    EqualizerGUI.hpp
    VoiceRemoval.hpp
    PhaseReverse.hpp
    SwapStereo.hpp
    Echo.hpp
    DysonCompressor.hpp
    BS2B.hpp
    bs2b/bs2b_lib.cpp
)

set(AudioFilters_SRC
    AudioFilters.cpp
    Equalizer.cpp
    EqualizerGUI.cpp
    VoiceRemoval.cpp
    PhaseReverse.cpp
    SwapStereo.cpp
    Echo.cpp
    DysonCompressor.cpp
    BS2B.cpp
    bs2b/bs2b.hpp
    bs2b/bs2bversion.hpp
)

set(AudioFilters_RESOURCES
    icon.qrc
)

link_directories(${LIBAVCODEC_LIBRARY_DIRS} ${LIBAVUTIL_LIBRARY_DIRS})

include_directories(../../qmplay2/headers ${LIBAVCODEC_INCLUDE_DIRS} ${LIBAVUTIL_INCLUDE_DIRS})

add_library(${PROJECT_NAME} ${QMPLAY2_MODULE}
    ${AudioFilters_HDR}
    ${AudioFilters_SRC}
    ${AudioFilters_RESOURCES}
)

target_link_libraries(${PROJECT_NAME}
    ${LIBAVCODEC_LIBRARIES}
    ${LIBAVUTIL_LIBRARIES}
    libqmplay2
)

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${MODULES_INSTALL_PATH})
