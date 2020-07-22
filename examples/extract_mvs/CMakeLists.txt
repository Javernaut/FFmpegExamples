set(CMAKE_C_STANDARD 99)

add_executable(extract_mvs extract_mvs.c)

add_ffmpeg_dependencies(
        extract_mvs

        avutil
        avcodec
        avformat
)
