# FFmpegExamples

Here are the official examples of [FFmpeg](http://ffmpeg.org) that are rearranged into the individual CMake modules. The main goal is seamless importing of them into [CLion IDE](https://www.jetbrains.com/clion) and other IDEs that support [CMake](https://cmake.org/). Building in terminal is also possible. 

## What exact examples are here?

All examples of FFmpeg **4.3.1** are integrated. However, a lower version of FFmpeg can be used to compile the examples.
The original sources can be found [here](https://git.ffmpeg.org/gitweb/ffmpeg.git/tree/6b6b9e593dd4d3aaf75f48d40a13ef03bdef9fdb:/doc/examples).

## What OS are supported?

On **Linux** and **macOS** the project can be integrated into an IDE or used in terminal.

**Windows** wasn't tested, but the command line building should work in Linux subsystem installed using [WSL](https://docs.microsoft.com/en-us/windows/wsl/about).

## Requirements

First of all you need to install `cmake`, `make`, both C and C++ compilers (`gcc`, `g++` or `clang` will do). By default all examples are compiled using C99 standard, but using C++ is also available.

On macOS:
```
brew install cmake make llvm
```
On Ubuntu:
```
sudo apt-get install cmake make gcc g++
```

You also need all FFmpeg's shared libraries with their header files.

On macOS:
```
brew install ffmpeg
```
On Ubuntu:
```
sudo apt-get install ffmpeg libavutil-dev libavcodec-dev libavformat-dev libavfilter-dev libpostproc-dev libswscale-dev libswresample-dev
```
Different versions of Ubuntu will install different version of these packages. Specifically:
- Ubuntu 16.05 - FFmpeg 2.8.x
- Ubuntu 18.04 - FFmpeg 3.4.x
- Ubuntu 20.04 - FFmpeg 4.2.x (currently)

Here are implications of using different version of FFmpeg:
- FFmpeg 4.0 and above - all examples are compilable
- FFmpeg 3.4 - `hw_decode` and `transcode_aac` aren't compilable, but the rest is
- FFmpeg 3.3.x and 2.8.x aren't tested and are out of the focus

Certain examples require additional packages to be installed (see below).

## How to import the project into CLion IDE?

This is pretty simple:
- Make 'Open' or 'Open or Import' action
- Select the root CMakeLists.txt of this project
- Select 'Open as Project'

Now the project should be imported into CLion. You can easily switch between targets (examples) to build and execute. Beware that all examples require certain arguments like paths to media files or else. So just executing an example will not do any valuable job. You can customize build targets to pass these arguments. For that you need to specify Program arguments in a respective Run Configuration. See [this link](https://www.jetbrains.com/help/clion/run-debug-configuration-application.html#1) for more info.
Also for simplicity you can hardcode such parameters inside the examples' source code.

<img src="https://user-images.githubusercontent.com/979018/88188320-5c7eab80-cc40-11ea-8f14-f23c5df9d646.png">

## How to build examples in terminal?

CMake doesn't support building inside the source code directory, so it is necessary to create a separate directory for that. From inside the root of this project execute the following commands:
```
mkdir build
cd build
cmake ..
```

That will prepare a directory that is capable of compiling the sources. From now you can build all example at once using one of the following commands from inside that `build` directory:
```
cmake --build .
```
or
```
make
```

If you wish to build only a specific target use one of the following commands (with necessary example name):
```
cmake --build . --target avio_reading
```
or
```
make avio_reading
```

After the compilation each example will be located at `${PROJECT_PATH}/build/examples/${EXAMPLE_NAME}/${EXAMPLE_NAME}`. The first `${EXAMPLE_NAME}` is a directory and the second one is a binary file name.

## Notes about certain examples

### qsvdec

The Intel Quick Sync Video (QSV) example will work if these conditions are met:
- building happens NOT on macOS
- the `libmfx-dev` package is installed (available on Ubuntu 19.10+)
- there is a custom ffmpeg built with `--enable-libmfx` and installed

### vaapi_encode and vaapi_transcode

The Video Acceleration API (VAAPI) examples will work if these conditions are met:
- the `libva-dev` package is installed
- there is a custom ffmpeg built with `--enable-vaapi` and installed
