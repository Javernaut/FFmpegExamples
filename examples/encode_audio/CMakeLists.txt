set(CMAKE_C_STANDARD 99)

add_executable(encode_audio encode_audio.c)

add_ffmpeg_dependencies(
        encode_audio

        avutil
        avcodec
)

target_link_libraries(encode_audio PRIVATE m)
