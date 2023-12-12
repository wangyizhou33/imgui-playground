cmake_minimum_required(VERSION 3.8)
project(test_package LANGUAGES CXX)

find_package(imgui REQUIRED CONFIG)
find_package(GLFW3)
find_package(GLEW)

add_executable(${PROJECT_NAME} 
               main.cpp
               imgui_impl_opengl3.cpp
               imgui_impl_glfw.cpp
)
target_link_libraries(${PROJECT_NAME} PRIVATE
                      glfw
                      GLEW::GLEW
                      imgui::imgui
)

option(DOCKING "Test docking" OFF)

if (DOCKING)
    target_compile_definitions(${PROJECT_NAME} PRIVATE -DDOCKING)
endif()

target_compile_features(${PROJECT_NAME} PRIVATE cxx_std_11)