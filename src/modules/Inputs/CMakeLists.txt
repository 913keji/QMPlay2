cmake_minimum_required(VERSION 3.1)
project(Inputs)

set(Inputs_HDR
    Inputs.hpp
    ToneGenerator.hpp
    PCM.hpp
    Rayman2.hpp
)

set(Inputs_SRC
    Inputs.cpp
    ToneGenerator.cpp
    PCM.cpp
    Rayman2.cpp
)

set(Inputs_RESOURCES
    icons.qrc
)

include_directories(../../qmplay2/headers)

add_library(${PROJECT_NAME} ${QMPLAY2_MODULE}
    ${Inputs_HDR}
    ${Inputs_SRC}
    ${Inputs_RESOURCES}
)

target_link_libraries(${PROJECT_NAME}
    libqmplay2
)

install(TARGETS ${PROJECT_NAME} LIBRARY DESTINATION ${MODULES_INSTALL_PATH})
