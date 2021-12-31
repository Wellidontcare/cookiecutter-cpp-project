add_executable({{ cookiecutter.project_slug }}_app {{ cookiecutter.project_slug }}_app.cpp)
target_link_libraries({{ cookiecutter.project_slug }}_app PRIVATE {{ cookiecutter.project_slug }})
add_custom_target(run ${CMAKE_BINARY_DIR}/app/{{ cookiecutter.project_slug }}_app DEPENDS {{ cookiecutter.project_slug }}_app)
