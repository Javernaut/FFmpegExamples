set(CMAKE_C_STANDARD 99)

add_executable(remuxing remuxing.c)

add_ffmpeg_dependencies(
        remuxing

        avutil
        avcodec
        avformat
)
