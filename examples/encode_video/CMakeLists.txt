set(CMAKE_C_STANDARD 99)

add_executable(encode_video encode_video.c)

add_ffmpeg_dependencies(
        encode_video

        avutil
        avcodec
)
