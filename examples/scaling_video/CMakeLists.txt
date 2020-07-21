set(CMAKE_C_STANDARD 99)

add_executable(scaling_video scaling_video.c)

add_ffmpeg_dependencies(
        scaling_video

        avutil
        swscale
)
