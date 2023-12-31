cmake_minimum_required(VERSION 3.20)

set(DRAFT_PROJECT_NAME "draft-engine")

set(DRAFT_VERSION_MAJOR 1)
set(DRAFT_VERSION_MINOR 0)

set(DRAFT_EXECUTABLE_NAME "draft")

project(${DRAFT_PROJECT_NAME} 
    VERSION ${DRAFT_VERSION_MAJOR}.${DRAFT_VERSION_MINOR})

set(DRAFT_INCLUDE_DIRECTORIES
    ${PROJECT_SOURCE_DIR}/includes/)

set(DRAFT_LIBRARIES_DIRECTORY
    ${PROJECT_SOURCE_DIR}/libraries/)

option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)

add_subdirectory(${DRAFT_LIBRARIES_DIRECTORY}/glfw)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

file(GLOB_RECURSE DRAFT_INCLUDE_FILES
    ${PROJECT_SOURCE_DIR}/includes/*.h
    ${PROJECT_SOURCE_DIR}/includes/*.hpp)

file(GLOB_RECURSE DRAFT_SOURCE_FILES
    ${PROJECT_SOURCE_DIR}/sources/*.c
    ${PROJECT_SOURCE_DIR}/sources/*.cpp)

add_executable(${DRAFT_EXECUTABLE_NAME} 
    ${DRAFT_INCLUDE_FILES} ${DRAFT_INCLUDE_FILES})

target_include_directories(${DRAFT_EXECUTABLE_NAME}
    ${DRAFT_INCLUDE_DIRECTORIES})