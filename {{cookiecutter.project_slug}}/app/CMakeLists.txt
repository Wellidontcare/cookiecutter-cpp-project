add_executable({{ cookiecutter.project_slug }}_app {{ cookiecutter.project_slug }}_app.cpp)
target_link_libraries({{ cookiecutter.project_slug }}_app PRIVATE {{ cookiecutter.project_slug }})
add_custom_target(run ${CMAKE_BINARY_DIR}/app/{{ cookiecutter.project_slug }}_app DEPENDS {{ cookiecutter.project_slug }}_app)

set(CMAKE_EXPORT_COMPILE_COMMANDS ON)
add_custom_command(TARGET {{ cookiecutter.project_slug }}_app POST_BUILD
  COMMAND ln -s ${CMAKE_BINARY_DIR}/compile_commands.json .
    WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}
    COMMENT "Linking compile commands for target {{ cookiecutter.project_slug }}_app"
)
