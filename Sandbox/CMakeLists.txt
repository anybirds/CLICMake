project(sandbox_project LANGUAGES CSharp)

include(CSharpUtilities)

file(GLOB_RECURSE SANDBOX_SOURCE "*.cs" "*.config" "*.xaml" "*.xaml.cs" "*.resx" "*.settings")

if(MSVC)
  source_group(TREE ${CMAKE_CURRENT_SOURCE_DIR} FILES ${SANDBOX_SOURCE})
endif()

add_executable(Sandbox ${SANDBOX_SOURCE})

set_target_properties(
  Sandbox PROPERTIES
  VS_DOTNET_TARGET_FRAMEWORK_VERSION "v4.6.1"
  WIN32_EXECUTABLE TRUE
  VS_DEBUGGER_WORKING_DIRECTORY "${CMAKE_SOURCE_DIR}"
)

set_property(TARGET Sandbox PROPERTY VS_DOTNET_REFERENCES
  "Microsoft.CSharp"
  "PresentationCore"
  "PresentationFramework"
  "System"
  "System.Core"
  "System.Data"
  "System.Data.DataSetExtensions"
  "System.Net.Http"
  "System.Xaml"
  "System.Xml"
  "System.Xml.Linq"
  "WindowsBase"
)

target_link_libraries(Sandbox Wrapper)