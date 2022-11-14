cmake_minimum_required(VERSION 3.16.3)

project(lesson1 CUDA CXX)

set(CMAKE_EXPORT_COMPILE_COMMANDS on)

include(CheckLanguage)
check_language(CUDA)

find_package(OpenGL REQUIRED)
find_package(GLUT REQUIRED)
find_package(PCL REQUIRED)

if(NOT DEFINED CMAKE_CUDA_STANDARD)
    set(CMAKE_CUDA_STANDARD 11)
    set(CMAKE_CUDA_STANDARD_REQUIRED ON)
endif()

add_executable(
    lesson1
    src/lesson_1_main.cpp
    src/cudaWrapper.cpp
    src/lesson_1.cu
)

target_link_libraries(lesson1 PRIVATE
    ${OPENGL_LIBRARIES}
	${GLUT_LIBRARIES}
	${PCL_LIBRARIES}
)

target_include_directories(lesson1 PRIVATE
    ./include
    ${PCL_INCLUDE_DIRS}
)
