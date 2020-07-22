set(CMAKE_C_STANDARD 99)

add_executable(muxing muxing.c)

add_ffmpeg_dependencies(
        muxing

        avutil
        avcodec
        avformat
        swscale
        swresample
)

target_link_libraries(muxing PRIVATE m)
