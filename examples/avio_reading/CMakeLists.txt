set(CMAKE_C_STANDARD 99)

add_executable(avio_reading avio_reading.c)

add_ffmpeg_dependencies(
        avio_reading

        avutil
        avcodec
        avformat
)
