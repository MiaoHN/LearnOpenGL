cmake_minimum_required(VERSION 3.15)

project(LearnOpenGL)

set(CMAKE_CXX_STANDARD 11)

# glfw
option(GLFW_BUILD_DOCS OFF)
option(GLFW_BUILD_EXAMPLES OFF)
option(GLFW_BUILD_TESTS OFF)
add_subdirectory(3rd/glfw)
include_directories(3rd/glfw/include)
LIST(APPEND LIBS glfw ${GLFW_LIBRARIES})

# glad
set(GLAD_SRC 3rd/glad/src/glad.c)
if(NOT WIN32)
  LIST(APPEND LIBS dl)
endif(NOT WIN32)
include_directories(3rd/glad/include)

# glm
include_directories(3rd/glm)

set(SOURCE_FILES src/main.cpp ${GLAD_SRC})
add_executable(${PROJECT_NAME} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} ${LIBS})