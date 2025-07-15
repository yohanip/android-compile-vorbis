cmake_minimum_required(VERSION 3.26)

project(YoOggVorbis)

add_subdirectory(ogg)
add_subdirectory(vorbis)

# if main project

if(CMAKE_SOURCE_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
    install(
        DIRECTORY vorbis/include/
        DESTINATION include
    )
endif()
