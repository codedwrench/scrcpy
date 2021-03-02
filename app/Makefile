SHELL = /bin/bash
ARCHS = arm64
TARGET := iphone:clang:11.4:11.4
INSTALL_TARGET_PROCESSES = scrcpy

include $(THEOS)/makefiles/common.mk

.PHONY: all

# Create links to the different libraries, we don't want any system libraries to be added, which is why these libs are
# added specifically in this way, supports both /usr/include and /usr/local/include
all ::
	@[ ! -L ./libavcodec ] && [ -d "/usr/include/libavcodec" ] && ln -s /usr/include/libavcodec ./libavcodec || true
	@[ ! -L ./libavutil ] && [ -d "/usr/include/libavutil" ] && ln -s /usr/include/libavutil ./libavutil || true
	@[ ! -L ./libavformat ] && [ -d "/usr/include/libavformat" ] && ln -s /usr/include/libavformat ./libavformat || true
	@[ ! -L ./SDL2 ] && [ -d "/usr/include/SDL2" ] && ln -s /usr/include/SDL2 ./SDL2 || true
	@[ ! -L ./libavcodec ] && [ -d "/usr/local/include/libavcodec" ] && ln -s /usr/local/include/libavcodec ./libavcodec || true
	@[ ! -L ./libavutil ] && [ -d "/usr/local/include/libavutil" ] && ln -s /usr/local/include/libavutil ./libavutil || true
	@[ ! -L ./libavformat ] && [ -d "/usr/local/include/libavformat" ] && ln -s /usr/local/include/libavformat ./libavformat || true
	@[ ! -L ./SDL2 ] && [ -d "/usr/local/include/SDL2" ] && ln -s /usr/local/include/SDL2 ./SDL2 || true


APPLICATION_NAME = scrcpy
scrcpy_FILES=src/main.c src/cli.c src/command.c src/control_msg.c src/controller.c src/decoder.c src/device.c src/device_msg.c src/event_converter.c src/file_handler.c src/fps_counter.c src/input_manager.c src/opengl.c src/receiver.c src/recorder.c src/scrcpy.c src/screen.c src/server.c src/stream.c src/tiny_xpm.c src/video_buffer.c src/util/net.c src/util/str_util.c src/sys/unix/command.c
scrcpy_FRAMEWORKS= AVFoundation AudioToolbox CoreAudio CoreFoundation CoreGraphics CoreMotion Foundation GameController OpenGLES QuartzCore UIKit
scrcpy_CFLAGS =  -DPORTABLE -D_M_ARM64 -DSDL_DISABLE_EMMINTRIN_H -DSDL_DISABLE_PMMINTRIN_H -DSDL_DISABLE_XMMINTRIN_H -DSDL_DISABLE_IMMINTRIN_H -DSDL_DISABLE_MMINTRIN_H -fno-implicit-module-maps -fobjc-arc -w -I./ -I./src
# These dylibs would otherwise not link at all?
scrcpy_LDFLAGS = -L./precompiled_libs -lSDL2 -lm -liconv -lm -liconv ./precompiled_libs/libavcodec.dylib ./precompiled_libs/libavutil.dylib ./precompiled_libs/libavformat.dylib


include $(THEOS_MAKE_PATH)/application.mk
