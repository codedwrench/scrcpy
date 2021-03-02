ARCHS = arm64
TARGET := iphone:clang:11.4:11.4
INSTALL_TARGET_PROCESSES = scrcpy

include $(THEOS)/makefiles/common.mk

APPLICATION_NAME = scrcpy
scrcpy_FILES=src/main.c src/cli.c src/command.c src/control_msg.c src/controller.c src/decoder.c src/device.c src/device_msg.c src/event_converter.c src/file_handler.c src/fps_counter.c src/input_manager.c src/opengl.c src/receiver.c src/recorder.c src/scrcpy.c src/screen.c src/server.c src/stream.c src/tiny_xpm.c src/video_buffer.c src/util/net.c src/util/str_util.c src/sys/unix/command.c
scrcpy_FRAMEWORKS= AVFoundation AudioToolbox CoreAudio CoreFoundation CoreGraphics CoreMotion Foundation GameController OpenGLES QuartzCore UIKit
scrcpy_CFLAGS =  -D_M_ARM64 -DSDL_DISABLE_EMMINTRIN_H -DSDL_DISABLE_PMMINTRIN_H -DSDL_DISABLE_XMMINTRIN_H -DSDL_DISABLE_IMMINTRIN_H -DSDL_DISABLE_MMINTRIN_H -fno-implicit-module-maps -fobjc-arc -w -I./SDL2 -I./libavformat -I./libavcodec -I./libavutil
# These dylibs would otherwise not link at all?
scrcpy_LDFLAGS = -v -L./precompiled_libs -lSDL2 -lm -liconv -lm -liconv ./precompiled_libs/libavcodec.dylib ./precompiled_libs/libavutil.dylib ./precompiled_libs/libavformat.dylib

include $(THEOS_MAKE_PATH)/application.mk
