# Generated automatically from Makefile.in.in by configure.
# Makefile for program source directory in GNU NLS utilities package.
# Copyright (C) 1995 Free Software Foundation, Inc.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.

PACKAGE = sharutils
VERSION = 4.2.1

SHELL = /bin/sh


srcdir = .
top_srcdir = ..

prefix = /usr/local
exec_prefix = ${prefix}
datadir = $(prefix)/share
localedir = $(datadir)/locale
gnulocaledir = $(prefix)/share/locale
gettextsrcdir = $(prefix)/share/gettext
subdir = po

INSTALL = /bin/install -c
INSTALL_DATA = ${INSTALL} -m 644

CC = gcc
GENCAT = 
GMSGFMT = msgfmt
MSGFMT = msgfmt
XGETTEXT = xgettext
TUPDATE = tupdate

DEFS = -DHAVE_CONFIG_H
CFLAGS = -g -O
CPPFLAGS = 

INCLUDES = -I.. -I$(top_srcdir)/intl

COMPILE = $(CC) -c $(DEFS) $(INCLUDES) $(CPPFLAGS) $(CFLAGS) $(XCFLAGS)

SOURCES = cat-id-tbl.c
POFILES =  de.po fr.po ja_JP.EUC.po nl.po pt.po sv.po
GMOFILES =  de.gmo fr.gmo ja_JP.EUC.gmo nl.gmo pt.gmo sv.gmo
DISTFILES = ChangeLog Makefile.in.in POTFILES.in $(PACKAGE).pot \
stamp-cat-id $(POFILES) $(GMOFILES) $(SOURCES)

POTFILES = \
	../lib/error.c \
	../lib/getopt.c \
	../lib/xmalloc.c \
	../src/shar.c \
	../src/unshar.c \
	../src/uudecode.c \
	../src/uuencode.c

CATALOGS =  de.gmo fr.gmo ja_JP.EUC.gmo nl.gmo pt.gmo sv.gmo
CATOBJEXT = .gmo
INSTOBJEXT = .mo

.SUFFIXES:
.SUFFIXES: .c .o .po .pox .gmo .mo .msg .cat

.c.o:
	$(COMPILE) $<

.po.pox:
	$(MAKE) $(PACKAGE).pot
	$(TUPDATE) $(srcdir)/$(PACKAGE).pot $< > $*.pox

.po.mo:
	$(MSGFMT) -o $@ $<

.po.gmo:
	file=$(srcdir)/`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<

.po.cat:
	sed -f ../intl/po2msg.sed < $< > $*.msg \
	  && rm -f $@ && $(GENCAT) $@ $*.msg


all: cat-id-tbl.c $(CATALOGS)

$(PACKAGE).pot: $(POTFILES)
	$(XGETTEXT) --default-domain=$(PACKAGE) --directory=$(top_srcdir) \
	  --add-comments --keyword=_ --keyword=N_ \
	  --files-from=$(srcdir)/POTFILES.in
	if cmp -s $(PACKAGE).po $(srcdir)/$(PACKAGE).pot; then \
	  rm -f $(PACKAGE).po; \
	else \
	  rm -f $(srcdir)/$(PACKAGE).pot \
	    && mv $(PACKAGE).po $(srcdir)/$(PACKAGE).pot; \
	fi

cat-id-tbl.c: stamp-cat-id
stamp-cat-id: $(PACKAGE).pot
	rm -f cat-id-tbl.tmp.c
	sed -f ../intl/po2tbl.sed $(srcdir)/$(PACKAGE).pot \
		| sed -e "s/@PACKAGE NAME@/$(PACKAGE)/" > cat-id-tbl.tmp.c
	if cmp -s cat-id-tbl.tmp.c $(srcdir)/cat-id-tbl.c; then \
	  rm cat-id-tbl.tmp.c; \
	else \
	  echo cat-id-tbl.c changed; \
	  rm -f $(srcdir)/cat-id-tbl.c; \
	  mv cat-id-tbl.tmp.c $(srcdir)/cat-id-tbl.c; \
	fi
	cd $(srcdir) && rm -f stamp-cat-id && echo timestamp > stamp-cat-id


install: install-exec install-data
install-exec:
install-data: all
	$(top_srcdir)/mkinstalldirs $(datadir)
	catalogs='$(CATALOGS)'; \
	for cat in $$catalogs; do \
	  if test "`echo $$cat | sed 's/.*\(\..*\)/\1/'`" = ".gmo"; then \
	    destdir=$(gnulocaledir); \
	  else \
	    destdir=$(localedir); \
	  fi; \
	  lang=`echo $$cat | sed 's/$(CATOBJEXT)$$//'`; \
	  dir=$$destdir/$$lang/LC_MESSAGES; \
	  $(top_srcdir)/mkinstalldirs $$dir; \
	  if test -r $$cat; then \
	    $(INSTALL_DATA) $$cat $$dir/$(PACKAGE)$(INSTOBJEXT); \
	  else \
	    $(INSTALL_DATA) $(srcdir)/$$cat $$dir/$(PACKAGE)$(INSTOBJEXT); \
	  fi; \
	done

# This installation goal is only used in GNU gettext.  Packages which
# only use the library should use install instead.
install-src: install
	$(top_srcdir)/mkinstalldirs $(gettextsrcdir)
	cd $(srcdir) && \
	  $(INSTALL_DATA) Makefile.in.in $(gettextsrcdir)/po-Makefile.in.in

uninstall:
	catalogs='$(CATALOGS)'; \
	for cat in $$catalogs; do \
	  lang=`echo $$cat | sed 's/$(CATOBJEXT)$$//'`; \
	  rm -f $(localedir)/$$lang/LC_MESSAGES/$(PACKAGE)$(INSTOBJEXT); \
	  rm -f $(gnulocaledir)/$$lang/LC_MESSAGES/$(PACKAGE)$(INSTOBJEXT); \
	done
	rm -f $(gettextsrcdir)/po-Makefile.in.in

check: all

cat-id-tbl.o: ../intl/libgettext.h

TAGS ID:

mostlyclean:
	rm -f core core.* *.pox $(PACKAGE).po *.old.po cat-id-tbl.tmp.c

clean: mostlyclean

distclean: clean
	rm -f Makefile Makefile.in POTFILES *.mo *.msg *.cat

maintainer-clean: distclean
	@echo "This command is intended for maintainers to use;"
	@echo "it deletes files that may require special tools to rebuild."

distdir = ../$(PACKAGE)-$(VERSION)/$(subdir)
dist dist-gettext: update-po $(DISTFILES)
	for file in $(DISTFILES); do \
	  ln $(srcdir)/$$file $(distdir) 2> /dev/null \
	    || cp -p $(srcdir)/$$file $(distdir); \
	done

update-po: Makefile
	$(MAKE) $(PACKAGE).pot
	cd $(srcdir); \
	catalogs='$(CATALOGS)'; \
	for cat in $$catalogs; do \
	  lang=`echo $$cat | sed 's/$(CATOBJEXT)$$//'`; \
	  mv $$lang.po $$lang.old.po; \
	  if $(TUPDATE) $(PACKAGE).pot $$lang.old.po > $$lang.po; then \
	    rm -f $$lang.old.po; \
	  else \
	    echo "tupdate for $$cat failed!"; \
	    rm -f $$lang.po; \
	    mv $$lang.old.po $$lang.po; \
	  fi; \
	done

POTFILES: POTFILES.in
	( if test 'x$(srcdir)' != 'x.'; then \
	    posrcprefix='$(top_srcdir)/'; \
	  else \
	    posrcprefix="../"; \
	  fi; \
	  sed -e '/^#/d' -e '/^[ 	]*$$/d' \
	      -e "s@.*@	$$posrcprefix& \\\\@" \
	      -e '$$s/\(.*\) \\/\1/' < $(srcdir)/POTFILES.in > POTFILES )

Makefile: Makefile.in.in ../config.status POTFILES
	cd .. && CONFIG_FILES=$(subdir)/$@.in CONFIG_HEADERS= ./config.status

# Tell versions [3.59,3.63) of GNU make not to export all variables.
# Otherwise a system limit (for SysV at least) may be exceeded.
.NOEXPORT:
