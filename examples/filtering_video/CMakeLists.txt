set(CMAKE_C_STANDARD 99)

add_executable(filtering_video filtering_video.c)

add_ffmpeg_dependencies(
        filtering_video

        avutil
        avcodec
        avformat
        avfilter
)
