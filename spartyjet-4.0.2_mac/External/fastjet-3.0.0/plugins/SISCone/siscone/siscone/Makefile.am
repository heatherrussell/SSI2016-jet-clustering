SUBDIRS = . spherical

# build information for the SISCone library
# this is built as a libtool lib.
lib_LTLIBRARIES = libsiscone.la
libsiscone_la_SOURCES = ranlux.cpp reference.cpp geom_2d.cpp\
   momentum.cpp hash.cpp quadtree.cpp vicinity.cpp\
   protocones.cpp split_merge.cpp siscone.cpp\
   siscone_error.cpp area.cpp

EXTRA_DIST = makefile.static

# install the SISCone headers
includedir = $(prefix)/include/siscone
include_HEADERS = area.h\
  circulator.h\
  defines.h\
  geom_2d.h\
  hash.h\
  momentum.h\
  protocones.h\
  quadtree.h\
  ranlux.h\
  reference.h\
  siscone_error.h\
  siscone.h\
  split_merge.h\
  vicinity.h

# Don't distribute config.h. Note that it'll be accessible through -I.
nodist_include_HEADERS = config.h
