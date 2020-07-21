set(CMAKE_C_STANDARD 99)

add_executable(hw_decode hw_decode.c)

add_ffmpeg_dependencies(
        hw_decode

        avutil
        avcodec
        avformat
)
