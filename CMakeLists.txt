cmake_minimum_required(VERSION 3.10)

project(SDL_CMake_Setup)

add_executable(${PROJECT_NAME} src/main.cpp)

find_package(Git QUIET)
if(GIT_FOUND AND EXISTS "${PROJECT_SOURCE_DIR}/.git")
    option(GIT_SUBMODULE "Check submodules during build" ON)
    if(GIT_SUBMODULE)
        message(STATUS "Submodule update")
        execute_process(
            COMMAND ${GIT_EXECUTABLE} 
            submodule update --init --recursive
            WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
            RESULT_VARIABLE GIT_SUBMOD_RESULT
        )
        if(NOT GIT_SUBMOD_RESULT EQUAL "0")
            message(FATAL_ERROR "git submodule update --init failed with ${GIT_SUBMOD_RESULT}")
        endif()
    endif()
endif()

add_subdirectory(external/sdl)

target_include_directories(${PROJECT_NAME} PUBLIC external/sdl/include)
target_link_directories(${PROJECT_NAME} PRIVATE external/sdl)
target_link_libraries(${PROJECT_NAME} mingw32 SDL2main SDL2)
