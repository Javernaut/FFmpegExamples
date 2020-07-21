set(CMAKE_C_STANDARD 99)

add_executable(decode_audio decode_audio.c)

add_ffmpeg_dependencies(
        decode_audio
        
        avcodec
        avutil
)
