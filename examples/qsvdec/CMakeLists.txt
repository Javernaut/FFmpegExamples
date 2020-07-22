set(CMAKE_C_STANDARD 99)

add_executable(qsvdec qsvdec.c)

add_ffmpeg_dependencies(
        qsvdec

        avutil
        avcodec
        avformat
)
