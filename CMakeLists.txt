cmake_minimum_required(VERSION 3.0.0)
project(rasterizer VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 17)
if(MSVC)  
    set(CMAKE_CXX_FLAGS_RELEASE "${CMAKE_CXX_FLAGS_RELEASE} /MT")
    set(CMAKE_CXX_FLAGS_DEBUG "${CMAKE_CXX_FLAGS_DEBUG} /MTd")
    if(NOT DEFINED NANA_INCLUDE)
        message("NANA_INCLUDE not set, using default")
        set(NANA_INCLUDE "C:\\Program Files (x86)\\nana\\include")
    endif()

    if(NOT DEFINED NANA_LIB)
        message("NANA_LIB not set, using default")
        set(NANA_LIB "C:\\Program Files (x86)\\nana\\lib\\nana.lib")
    endif()
endif(MSVC)

add_executable(rasterizer main.cpp)

target_include_directories(rasterizer PRIVATE  ${NANA_INCLUDE})
target_link_libraries(rasterizer PUBLIC ${NANA_LIB})
