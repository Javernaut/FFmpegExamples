set(CMAKE_C_STANDARD 99)

add_executable(vaapi_encode vaapi_encode.c)

add_ffmpeg_dependencies(
        vaapi_encode

        avutil
        avcodec
)
