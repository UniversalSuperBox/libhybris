lib_LTLIBRARIES = \
	libhybris-common.la

if WANT_EXPERIMENTAL
SUBDIRS = mm
libhybris_common_la_LIBADD = mm/libandroid-linker.la
else
# JB linker works fine for ICS
if HAS_ANDROID_4_0_0
SUBDIRS = jb
libhybris_common_la_LIBADD= jb/libandroid-linker.la
else
if HAS_ANDROID_5_0_0
SUBDIRS = jb
libhybris_common_la_LIBADD= jb/libandroid-linker.la
else
if HAS_ANDROID_2_3_0
SUBDIRS = gingerbread
libhybris_common_la_LIBADD= gingerbread/libandroid-linker.la
else
$(error No Android Version is defined)
endif
endif
endif
endif

libhybris_common_la_SOURCES = \
	hooks.c \
	hooks_shm.c \
	strlcpy.c \
	strlcat.c \
	dlfcn.c \
	logging.c \
	sysconf.c
libhybris_common_la_CPPFLAGS = \
	-I$(top_srcdir)/include \
	$(ANDROID_HEADERS_CFLAGS) \
	-I$(top_srcdir)/common
if WANT_TRACE
libhybris_common_la_CPPFLAGS += -DDEBUG
endif
if WANT_DEBUG
libhybris_common_la_CPPFLAGS += -ggdb -O0
endif
if WANT_MALI_QUIRKS
libhybris_common_la_CPPFLAGS += -DMALI_QUIRKS
endif
libhybris_common_la_LDFLAGS = \
	-ldl \
	-lrt \
	-lpthread \
	-lc \
	-lstdc++ \
	$(top_builddir)/properties/libandroid-properties.la \
	-version-info "$(LT_CURRENT)":"$(LT_REVISION)":"$(LT_AGE)"
