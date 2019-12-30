project(wrapper_project)

file(GLOB_RECURSE WRAPPER_SOURCE "*.hpp" "*.cpp")

if(MSVC)
  source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${WRAPPER_SOURCE})
endif()

add_library(Wrapper SHARED ${WRAPPER_SOURCE})
add_definitions(-DEXPMODULE)

target_link_libraries(Wrapper Core)

set_target_properties(
  Wrapper PROPERTIES
  COMMON_LANGUAGE_RUNTIME ""
  CXX_STANDARD 17
  CXX_STANDARD_REQUIRED ON
)