# Building

## Windows
* #### Prerequisites
* [Git for Windows] - https://git-scm.com/downloads
* [Visual Studio] - https://www.visualstudio.com/en-us/news/vs2013-community-vs.aspx
* [CMake] - http://www.cmake.org/download/


* #### Building
* Open Visual Studio Command Prompt
* Enter the following:
```sh
git clone git://github.com/SDLash3D/xash3d.git
cd xash3d
git clone git://github.com/SDLash3D/halflife deps/HLSDK
git clone git://github.com/spurious/SDL-mirror deps/SDL2
mkdir build
cd build
cmake -G "Visual Studio 12" -DHL_SDK_DIR=deps/HLSDK ../
```
* Open generated solution in "build" directory and compile it. 
* Compiled executables will be placed in the "output" directory.


## Linux

* TODO