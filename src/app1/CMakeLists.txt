set(SOURCES
  imgui/imgui_demo.cpp
  imgui/imgui_draw.cpp
  imgui/imgui_impl_glfw.cpp
  imgui/imgui_impl_opengl3.cpp
  imgui/imgui_tables.cpp
  imgui/imgui_widgets.cpp
  imgui/imgui.cpp
  main.cpp
)


set(CMAKE_PREFIX_PATH "/opt/homebrew")
find_package(glfw3 3.4 REQUIRED) # change version if needed

add_executable(app1 ${SOURCES})

#target_link_libraries(app1 PRIVATE glfw "-framework OpenGL")
#target_link_libraries(app1 PRIVATE examplelib)
target_link_libraries(app1 
  PRIVATE 
    glfw "-framework OpenGL"
)
