cmake_minimum_required(VERSION 2.8.9) # CMake version
project(gatewayCPP) # Name
set(JSON_BuildTests OFF CACHE INTERNAL "")

# set(CMAKE_BUILD_TYPE Debug) # Set debug mode

LINK_DIRECTORIES(
    ${CMAKE_CURRENT_SOURCE_DIR}/lib/json
)


include_directories(
	${CMAKE_CURRENT_SOURCE_DIR}/inc # Includes
	${CMAKE_CURRENT_SOURCE_DIR}/lib/json # for Libs
)


file(GLOB SOURCES "src/*.cpp")
add_executable(main ${SOURCES})
set_property(TARGET main PROPERTY CXX_STANDARD 17) # CPP version
set_target_properties(main PROPERTIES OUTPUT_NAME "gatewayCPP") # Binary file name
install(TARGETS main DESTINATION bin) # for sudo make install for installation

target_link_libraries(main 
	pthread # Link pthread library to main
    -L${CMAKE_CURRENT_SOURCE_DIR}/lib/json # link external lib to main
)


