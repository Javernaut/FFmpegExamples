set(CMAKE_C_STANDARD 99)

add_executable(transcoding transcoding.c)

add_ffmpeg_dependencies(
        transcoding

        avutil
        avcodec
        avformat
        avfilter
)
