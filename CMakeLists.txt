cmake_minimum_required(VERSION 3.10)

set(SUPPORT_JPG OFF)

project(sdl_cmake)

add_executable(${PROJECT_NAME}
    src/main.cpp
)

set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR})

add_subdirectory(external/sdl)

target_include_directories(${PROJECT_NAME}
    PUBLIC external/sdl/include
)

target_link_directories(${PROJECT_NAME}
    PUBLIC external/sdl
)

if(WIN32 AND NOT MSVC)
    target_link_libraries(${PROJECT_NAME} mingw32 SDL2main SDL2)
else()
    target_link_libraries(${PROJECT_NAME} SDL2main SDL2)
endif()