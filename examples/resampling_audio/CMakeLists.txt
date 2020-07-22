set(CMAKE_C_STANDARD 99)

add_executable(resampling_audio resampling_audio.c)

add_ffmpeg_dependencies(
        resampling_audio

        avutil
        swresample
)

target_link_libraries(resampling_audio PRIVATE m)
