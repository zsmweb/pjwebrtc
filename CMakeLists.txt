cmake_minimum_required(VERSION 3.10)
project(pjwebrtc)

set(CMAKE_CXX_STANDARD 14)

#set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -framework AudioUnit")
#set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -framework CoreAudio")
#set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -framework AudioToolbox")

#set(CMAKE_C_FLAGS "-U__STRICT_ANSI__ -c -g -Wall -std=c++14")
#set(CMAKE_CXX_FLAGS "-U__STRICT_ANSI__ -c -g -Wall -std=c++14")

set(MAIN_DIR .)
set(LIB_DIR ${MAIN_DIR}/lib)

aux_source_directory(${LIB_DIR}/promise/src PROMISE_SRC_LIST)
include_directories(${LIB_DIR}/promise/include)

aux_source_directory(${LIB_DIR}/wsxx/src WSXX_SRC_LIST)
include_directories(${LIB_DIR}/wsxx/include)

include_directories(${LIB_DIR})

aux_source_directory(${MAIN_DIR}/src SRC_FILE_LIST)

set(SOURCES main.cpp ${SRC_FILE_LIST} ${PROMISE_SRC_LIST} ${WSXX_SRC_LIST})

add_executable(pjwebrtc ${SOURCES})

set(PJ_SUFIX unknown-linux-gnu)

target_link_libraries(pjwebrtc
        stdc++
        opus
        pjnath-aarch64-${PJ_SUFIX}
        pjmedia-aarch64-${PJ_SUFIX}
        pjmedia-videodev-aarch64-${PJ_SUFIX}
        pjmedia-audiodev-aarch64-${PJ_SUFIX}
        pjmedia-codec-aarch64-${PJ_SUFIX}
        pjsip-simple-aarch64-${PJ_SUFIX}
        pjsip-ua-aarch64-${PJ_SUFIX}
        pjsip-aarch64-${PJ_SUFIX}
        pjsua-aarch64-${PJ_SUFIX}
        pjsua2-aarch64-${PJ_SUFIX}
        resample-aarch64-${PJ_SUFIX}
        gsmcodec-aarch64-${PJ_SUFIX}
        speex-aarch64-${PJ_SUFIX}
        ilbccodec-aarch64-${PJ_SUFIX}
        g7221codec-aarch64-${PJ_SUFIX}
        yuv-aarch64-${PJ_SUFIX}
        webrtc-aarch64-${PJ_SUFIX}
        srtp-aarch64-${PJ_SUFIX}
        pj-aarch64-${PJ_SUFIX}
        pjlib-util-aarch64-${PJ_SUFIX}
        )

target_link_libraries(pjwebrtc ssl crypto pthread asound uuid)

#target_link_libraries(pjwebrtc
#        /usr/local/opt/openssl@1.1/lib/libssl.1.1.dylib
#        /usr/local/opt/openssl@1.1/lib/libcrypto.1.1.dylib
#        )
