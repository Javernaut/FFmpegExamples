set(CMAKE_C_STANDARD 99)

add_executable(encode_audio encode_audio.c)

add_ffmpeg_dependencies(
        encode_audio

        avutil
        avcodec
)
