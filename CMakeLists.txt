cmake_minimum_required(VERSION 3.8)

project(CLICmake)

add_subdirectory(Core)
add_subdirectory(Wrapper)
add_subdirectory(Sandbox)

add_dependencies(Wrapper Core)
add_dependencies(Sandbox Wrapper)

set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT Sandbox)