set(CMAKE_C_STANDARD 99)

add_executable(filtering_audio filtering_audio.c)

add_ffmpeg_dependencies(
        filtering_audio

        avutil
        avcodec
        avformat
        avfilter
)
