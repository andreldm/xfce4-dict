noinst_LTLIBRARIES = 							\
	libdict.la

libdict_la_SOURCES =							\
	dbus.c										\
	dbus.h										\
	common.c									\
	common.h									\
	dictd.c										\
	dictd.h										\
	gui.c										\
	gui.h										\
	libdict.h									\
	prefs.c										\
	prefs.h										\
	resources.c									\
	resources.h									\
	speedreader.c								\
	speedreader.h								\
	spell.c										\
	spell.h										\
	wraplabel.c									\
	wraplabel.h

libdict_la_CFLAGS =								\
	-I$(top_srcdir)								\
	$(LIBXFCE4UI_CFLAGS)						\
	$(LIBXFCE4PANEL_CFLAGS)						\
	-DPACKAGE_LOCALE_DIR=\"$(localedir)\"		\
	@GTHREAD_CFLAGS@

libdict_la_LIBADD =								\
	$(LIBXFCE4PANEL_LIBS)						\
	$(LIBXFCE4UI_LIBS)							\
	@GTHREAD_LIBS@

DISTCLEANFILES =								\
	resources.c										\
	resources.h										\
	dbus.c												\
	dbus.h

gui.c: resources.c dbus.c

resources.c: resources.h
	glib-compile-resources resources.xml --sourcedir=../pixmaps --generate-source --c-name dict

resources.h:
	glib-compile-resources resources.xml --sourcedir=../pixmaps --generate-header --c-name dict

dbus.c:
	gdbus-codegen --interface-prefix org.xfce --generate-c-code dbus dbus.xml
