set(CMAKE_C_STANDARD 99)

add_executable(http_multiclient http_multiclient.c)

add_ffmpeg_dependencies(
        http_multiclient

        avutil
        avformat
)
