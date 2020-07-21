set(CMAKE_C_STANDARD 99)

add_executable(demuxing_decoding demuxing_decoding.c)

add_ffmpeg_dependencies(
        demuxing_decoding

        avutil
        avformat
)
