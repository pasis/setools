bwidget_destdir = @BWIDGET_DESTDIR@
dist_noinst_DATA = BWidget-1.8.0.tar.bz2 combobox.tcl mainframe.tcl notebook.tcl \
	Doxyfile

SUBDIRS = rpm

if COPY_BWIDGET
  copy_bwidget = yes
else
  copy_bwidget = no
endif

pkgconfig_DATA = libqpol.pc libapol.pc libpoldiff.pc libseaudit.pc libsefs.pc
pkgconfigdir = @libdir@/pkgconfig

BUILT_SOURCES = $(pkgconfig_DATA)

$(pkgconfig_DATA): $(top_builddir)/config.status

install-data-local:
	if test $(copy_bwidget) = "yes"; then \
		tar jxf BWidget-1.8.0.tar.bz2; \
		test -z "$(bwidget_destdir)" || $(mkdir_p) "$(bwidget_destdir)" ;  \
		cd BWidget-1.8.0 ; \
		find . -type d -exec $(mkdir_p) "$(bwidget_destdir)/{}" \; ; \
		find . -type f -exec $(INSTALL_DATA) '{}' $(bwidget_destdir)/'{}' \; ; \
	fi

%.pc: %.pc.in Makefile
	cd $(top_builddir) && $(SHELL) ./config.status $(subdir)/$@ $(am__depfiles_maybe)

uninstall-local:
	if test $(copy_bwidget) = "yes"; then \
		rm -rf $(bwidget_destdir) ; \
	fi

clean-local:
	-rm -rf BWidget-1.8.0
