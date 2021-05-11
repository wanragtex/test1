cmake_minimum_required(VERSION 3.16)

set(CMAKE_BUILD_TYPE "Release" CACHE STRING "")

project(test1 VERSION 1.0 LANGUAGES CXX)

string(APPEND CMAKE_CXX_FLAGS_RELEASE " -std=c++17 -Wall -Wextra -Wnon-virtual-dtor -Wsign-promo -Wconversion -Wsign-conversion")
string(APPEND CMAKE_CXX_FLAGS_DEBUG " -std=c++17  -Wall -Wextra -Wnon-virtual-dtor -Wsign-promo -Wconversion -Wsign-conversion")

string(TOUPPER "${CMAKE_BUILD_TYPE}" build_type)
if(build_type STREQUAL "RELEASE")
    set(install_path "${CMAKE_SOURCE_DIR}/release")
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_RELEASE "${install_path}")
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_RELEASE "${install_path}")
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_RELEASE "${install_path}")
elseif(build_type STREQUAL "DEBUG")
    set(install_path "${CMAKE_SOURCE_DIR}/debug")
    set(CMAKE_RUNTIME_OUTPUT_DIRECTORY_DEBUG "${install_path}")
    set(CMAKE_LIBRARY_OUTPUT_DIRECTORY_DEBUG "${install_path}")
    set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY_DEBUG "${install_path}")
else()
    message(FATAL_ERROR "Unsupported build configuration")
endif()

add_subdirectory(src)
