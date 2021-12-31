pybind11_add_module({{ cookiecutter.project_slug.replace("-", "") }}_python {{ cookiecutter.project_slug }}_python.cpp)
target_link_libraries({{ cookiecutter.project_slug.replace("-", "") }}_python PUBLIC {{ cookiecutter.project_slug}})
set_target_properties({{ cookiecutter.project_slug.replace("-", "") }}_python PROPERTIES OUTPUT_NAME {{ cookiecutter.project_slug.replace("-", "") }})


set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
add_custom_command(TARGET {{ cookiecutter.project_slug }}_python POST_BUILD
  COMMAND ln -s ${CMAKE_BINARY_DIR}/compile_commands.json .
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Linking compile commands for target {{ cookiecutter.project_slug }}_python"
)
