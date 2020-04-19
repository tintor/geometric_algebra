cmake_minimum_required(VERSION 3.5)
project(klein_project)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_definitions(-O3 -mavx2 -mfma -DNDEBUG -Wfatal-errors)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -ferror-limit=1")

add_executable(main main.cc)

# Add Klein
include(FetchContent)
FetchContent_Declare(
    klein
    GIT_REPOSITORY https://github.com/jeremyong/Klein.git
    GIT_TAG origin/master
)
FetchContent_MakeAvailable(klein)
target_link_libraries(main PUBLIC klein::klein_sse42)
