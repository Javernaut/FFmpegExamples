cmake_minimum_required(VERSION 3.0)

project(FFmpegExamples)

# Names of libraries the FFmpeg consists of
set(
        ffmpeg_lib_names

        avutil
        avcodec
        avformat
        avfilter
        avdevice
        postproc
        swscale
        swresample
)

# Names of header files that are 'main entry' for a respective library
set(
        ffmpeg_headers_to_find

        libavutil/avutil.h
        libavcodec/avcodec.h
        libavformat/avformat.h
        libavfilter/avfilter.h
        libavdevice/avdevice.h
        libpostproc/postprocess.h # here the name of a header file differs from the library name
        libswscale/swscale.h
        libswresample/swresample.h
)

# Names of official examples of FFmpeg that are integrated to this project
set(
        example_names

        avio_list_dir
        avio_reading
        decode_audio
        decode_video
        demuxing_decoding
        encode_audio
        encode_video
        extract_mvs
        filter_audio
        filtering_audio
        filtering_video
        http_multiclient
        hw_decode
        metadata
        muxing
        remuxing
        resampling_audio
        scaling_video
        transcode_aac
        transcoding
        vaapi_encode
        vaapi_transcode
)

# The Intel Quick Sync Video (QSV) example isn't available for macOS
if (NOT ${CMAKE_SYSTEM_NAME} STREQUAL Darwin)
    list(APPEND example_names qsvdec)
endif()

# Function that adds FFmpeg libraries as dependencies to a specified target
# ARGV0 is a target name
# ARGV1+ vararg of dependencies to link against
function(add_ffmpeg_dependencies)
    set(executable_name ${ARGV0})
    math(EXPR dep_upper_bound "${ARGC} - 1")
    foreach (dep_index RANGE 1 ${dep_upper_bound})
        list(GET ARGV ${dep_index} dep_name)
        list(FIND ffmpeg_lib_names ${dep_name} lib_index)

        list(GET ffmpeg_headers_to_find ${lib_index} dep_header)

        find_path( ${dep_name}_include_dir ${dep_header} )
        find_library( ${dep_name}_library ${dep_name} )

        target_include_directories( ${executable_name} PRIVATE ${${dep_name}_include_dir} )
        target_link_libraries( ${executable_name} PRIVATE ${${dep_name}_library})
    endforeach ()
endfunction()

foreach (example_name ${example_names})
    add_subdirectory(examples/${example_name})
endforeach ()

# Additional playground module
add_subdirectory(playground)
