AUTOMAKE_OPTIONS=nostdinc
ACLOCAL_AMFLAGS = -I m4

if COMPOSITE
COMPOSITE_DIR=composite
endif

if GLX
GLX_DIR=glx
endif

if DBE
DBE_DIR=dbe
endif

if RECORD
RECORD_DIR=record
endif

SUBDIRS = \
	doc \
	include \
	dix  \
	fb \
	mi \
	Xext \
	miext \
	os \
	randr \
	render  \
	Xi \
	xkb \
	$(DBE_DIR) \
	$(RECORD_DIR) \
	xfixes \
	damageext \
	$(COMPOSITE_DIR) \
	$(GLX_DIR) \
	exa \
	config \
	hw \
	test \
	proto

if XORG
aclocaldir = $(datadir)/aclocal
aclocal_DATA = xorg-server.m4

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = xorg-server.pc
endif

EXTRA_DIST = xorg-server.pc.in xorg-server.m4 autogen.sh

DISTCHECK_CONFIGURE_FLAGS=\
	--with-xkb-path=$(XKB_BASE_DIRECTORY) \
	--with-xkb-bin-directory=$(XKB_BIN_DIRECTORY) \
	--with-xkb-output='$${datadir}/X11/xkb/compiled'

DISTCLEANFILES = doltcompile doltlibtool

.PHONY: ChangeLog INSTALL

INSTALL:
	$(INSTALL_CMD)

ChangeLog:
	$(CHANGELOG_CMD)

dist-hook: ChangeLog INSTALL

DIST_SUBDIRS = \
	doc \
	include \
	dix  \
	fb \
	mi \
	Xext \
	miext \
	os \
	randr \
	render  \
	Xi \
	xkb \
	dbe \
	record \
	xfixes \
	damageext \
	composite \
	glx \
	exa \
	config \
	hw \
	test

# gross hack
relink: all
	$(AM_V_at)$(MAKE) -C hw relink
