#
# Copyright (c) 2015 Pavlo Lavrenenko
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

cmake_minimum_required(VERSION 2.6.0)
project (XASH3D)

set (XASH3D_VERSION 0.96.3030)
option (HL_SDK_DIR "Build Half Life 1 SDK [specify directory]" OFF)
option (XASHXT_CLIENT_DIR "Build the XashXT client [specify directory]]" OFF)
option (LINK_VGUI "Link the VGUI library from HLSDK" ON)

set (OUTPUT_DIR ${CMAKE_SOURCE_DIR}/output CACHE PATH "Output directory")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${OUTPUT_DIR})

if(WIN32)
	set(SDL_SHARED_ENABLED_BY_DEFAULT OFF)
	add_subdirectory(deps)
endif()

option(PANDORA "Set to ON if targeting an OpenPandora device" ${PANDORA})

if(NOT XASH_DEDICATED)
	add_subdirectory (mainui)
endif()

add_subdirectory (engine)
add_subdirectory (game_launch)
add_subdirectory (vgui_support)

if(WIN32)
    add_dependencies(xash SDL2main)
endif()

if(XASHXT_CLIENT_DIR)
    add_subdirectory(${XASHXT_CLIENT_DIR})
endif()

