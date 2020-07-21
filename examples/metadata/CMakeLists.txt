set(CMAKE_C_STANDARD 99)

add_executable(metadata metadata.c)

add_ffmpeg_dependencies(
        metadata

        avutil
        avformat
)
