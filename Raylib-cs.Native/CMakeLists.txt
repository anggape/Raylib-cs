cmake_minimum_required(VERSION 3.28)
project(Raylib-cs.Native LANGUAGES C CXX)

include(FetchContent)
set(FETCHCONTENT_QUIET FALSE)
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

option(RAYLIB_TAG "raylib version")
option(RAYLIB_OUTPUT "library output directory")

if(NOT RAYLIB_TAG)
    message(FATAL_ERROR "'RAYLIB_TAG' is required.")
endif()
if(NOT RAYLIB_OUTPUT)
    message(FATAL_ERROR "'RAYLIB_OUTPUT' is required.")
endif()

fetchcontent_declare(raylib URL https://github.com/raysan5/raylib/archive/refs/tags/${RAYLIB_TAG}.zip)
fetchcontent_makeavailable(raylib)

set_target_properties(
    raylib glfw
    PROPERTIES ARCHIVE_OUTPUT_DIRECTORY ${RAYLIB_OUTPUT}
               LIBRARY_OUTPUT_DIRECTORY ${RAYLIB_OUTPUT}
               RUNTIME_OUTPUT_DIRECTORY ${RAYLIB_OUTPUT}
               ARCHIVE_OUTPUT_DIRECTORY_DEBUG ${RAYLIB_OUTPUT}
               LIBRARY_OUTPUT_DIRECTORY_DEBUG ${RAYLIB_OUTPUT}
               RUNTIME_OUTPUT_DIRECTORY_DEBUG ${RAYLIB_OUTPUT}
               ARCHIVE_OUTPUT_DIRECTORY_RELEASE ${RAYLIB_OUTPUT}
               LIBRARY_OUTPUT_DIRECTORY_RELEASE ${RAYLIB_OUTPUT}
               RUNTIME_OUTPUT_DIRECTORY_RELEASE ${RAYLIB_OUTPUT})
