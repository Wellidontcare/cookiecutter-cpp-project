add_library({{ cookiecutter.project_slug }} {{ cookiecutter.project_slug }}.cpp)
target_include_directories({{ cookiecutter.project_slug }} PUBLIC
  $<BUILD_INTERFACE:${CMAKE_SOURCE_DIR}/include/>
  $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
add_custom_command(TARGET {{ cookiecutter.project_slug }} POST_BUILD
  COMMAND ln -s ${CMAKE_BINARY_DIR}/compile_commands.json .
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Linking compile commands for target {{ cookiecutter.project_slug }}"
)
