cmake_minimum_required(VERSION 3.17)

project(nenya
    LANGUAGES CXX
    VERSION 0.1.0
    HOMEPAGE_URL "https://github.com/albin-johansson/nenya")

set(CMAKE_MODULE_PATH ${PROJECT_SOURCE_DIR}/cmake)
set(CMAKE_CXX_STANDARD 20)
set(CXX_STANDARD_REQUIRED ON)
set(CXX_EXTENSIONS OFF)

set(NENYA_INCLUDE_DIR ${PROJECT_SOURCE_DIR}/include)

include(Utilities)

add_subdirectory(test)