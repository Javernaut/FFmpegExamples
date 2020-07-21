set(CMAKE_C_STANDARD 99)

add_executable(vaapi_transcode vaapi_transcode.c)

add_ffmpeg_dependencies(
        vaapi_transcode

        avutil
        avcodec
        avformat
)
