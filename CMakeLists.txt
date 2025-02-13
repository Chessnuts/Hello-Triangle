cmake_minimum_required(VERSION 3.5.0)
project(Hello-Triangle)


set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Add dependencies
#SDL
set(SDL_TEST OFF)  
add_subdirectory(dependencies/SDL EXCLUDE_FROM_ALL)

#Vulkan
add_subdirectory(dependencies/Vulkan-Hpp)

# Create the executable
add_executable(Hello-Triangle src/main.cpp)

# Link SDL to the project
target_link_libraries(Hello-Triangle PRIVATE SDL3::SDL3)
target_link_libraries(Hello-Triangle INTERFACE Vulkan::Headers)

# Ensure SDL doesn't redefine main
target_compile_definitions(Hello-Triangle PRIVATE SDL_MAIN_HANDLED)