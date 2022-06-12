cmake_minimum_required(VERSION 3.0.0)
project(c-ls VERSION 0.1.0 LANGUAGES CXX)

set(default_build_type "Debug")

include(CTest)
enable_testing()

set(CPACK_PROJECT_NAME ${PROJECT_NAME})
set(CPACK_PROJECT_VERSION ${PROJECT_VERSION})
include(CPack)

add_compile_options(
    $<$<CONFIG:DEBUG>:-g>
    $<$<CONFIG:RELEASE>:-O3>
    $<$<CONFIG:RELEASE>:-Wall>
    $<$<CONFIG:RELEASE>:-Werror>
)

add_link_options(
    $<$<CONFIG:RELEASE>:-Wl,--strip-all>
)

include_directories(include)

add_executable(ls.bin src/core/ls.cpp)
target_link_libraries(ls.bin)
