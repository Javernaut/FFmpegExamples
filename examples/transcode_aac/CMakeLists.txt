set(CMAKE_C_STANDARD 99)

add_executable(transcode_aac transcode_aac.c)

add_ffmpeg_dependencies(
        transcode_aac

        avutil
        avcodec
        avformat
        swresample
)
