set(CMAKE_C_STANDARD 99)

add_executable(filter_audio filter_audio.c)

add_ffmpeg_dependencies(
        filter_audio

        avutil
        avfilter
)

target_link_libraries(filter_audio PRIVATE m)
