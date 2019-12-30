project(core_project)

file(GLOB_RECURSE CORE_SOURCE "*.hpp" "*.cpp")

if(MSVC)
  source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${CORE_SOURCE})
endif()

add_library(Core ${CORE_SOURCE})
add_definitions(-DEXPMODULE)

set_target_properties(
  Core PROPERTIES
  CXX_STANDARD 17
  CXX_STANDARD_REQUIRED ON
)