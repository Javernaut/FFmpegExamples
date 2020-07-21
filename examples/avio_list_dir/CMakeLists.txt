set(CMAKE_C_STANDARD 99)

add_executable(avio_list_dir avio_list_dir.c)

add_ffmpeg_dependencies(
        avio_list_dir

        avutil
        avcodec
        avformat
)
