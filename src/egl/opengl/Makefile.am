# Copyright © 2010 Intel Corporation
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice (including the next
# paragraph) shall be included in all copies or substantial portions of the
# Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.
#
# Authors:
#    Eric Anholt <eric@anholt.net>

# These programs aren't intended to be included with the normal distro.
# They're not too interesting but they're good for testing.

AM_CFLAGS = \
	$(DEMO_CFLAGS) \
	$(EGL_CFLAGS) \
	-I$(top_srcdir)/src/egl/eglut \
	-I$(top_srcdir)/src/util
AM_LDFLAGS = \
	$(DEMO_LIBS) \
	$(EGL_LIBS)

if HAVE_X11
EGL_X11_DEMOS = \
	eglgears_x11 \
	egltri_x11 \
	xeglgears \
	xeglthreads
endif

if HAVE_DRM
if HAVE_GBM
EGL_DRM_DEMOS = \
	eglkms
endif
endif

if HAVE_EGL
noinst_PROGRAMS = \
	eglinfo \
	peglgears \
	$(EGL_DRM_DEMOS) \
	$(EGL_X11_DEMOS)
endif

egltri_x11_SOURCES = egltri.c
eglgears_x11_SOURCES = eglgears.c

eglgears_x11_LDFLAGS = $(AM_LDFLAGS) $(X11_LIBS)
egltri_x11_LDFLAGS = $(AM_LDFLAGS) $(X11_LIBS)
xeglgears_LDFLAGS = $(AM_LDFLAGS) $(X11_LIBS)
xeglthreads_LDFLAGS = $(AM_LDFLAGS) $(X11_LIBS) -pthread

eglgears_x11_LDADD = ../eglut/libeglut_x11.la
egltri_x11_LDADD = ../eglut/libeglut_x11.la

eglkms_SOURCES = eglkms.c
eglkms_CFLAGS = $(AM_CFLAGS) $(DRM_CFLAGS) $(GBM_CFLAGS)
eglkms_LDADD = $(AM_LDFLAGS) $(DRM_LIBS) $(GBM_LIBS)
