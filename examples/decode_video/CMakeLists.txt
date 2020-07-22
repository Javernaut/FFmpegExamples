set(CMAKE_C_STANDARD 99)

add_executable(decode_video decode_video.c)

add_ffmpeg_dependencies(
        decode_video

        avutil
        avcodec
)
