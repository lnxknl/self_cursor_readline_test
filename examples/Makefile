#
# This is the Makefile for the readline examples subdirectory.
#
# Copyright (C) 1994,2008,2009 Free Software Foundation, Inc.

#   This program is free software: you can redistribute it and/or modify
#   it under the terms of the GNU General Public License as published by
#   the Free Software Foundation, either version 3 of the License, or
#   (at your option) any later version.

#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.

#   You should have received a copy of the GNU General Public License
#   along with this program.  If not, see <http://www.gnu.org/licenses/>.

RL_LIBRARY_VERSION = 7.0

SHELL = /bin/sh
RM = rm -f

prefix = /usr/local
exec_prefix = ${prefix}

datarootdir = ${prefix}/share

bindir = ${exec_prefix}/bin
srcdir = .
datadir = ${datarootdir}

top_srcdir = ..
#BUILD_DIR = .
BUILD_DIR = /home/tong/utils/dl/readline-7.0
installdir = $(datadir)/readline

INSTALL = /usr/bin/install -c
INSTALL_PROGRAM = ${INSTALL}
INSTALL_DATA = ${INSTALL} -m 644

EXEEXT = 
OBJEXT = o

# Support an alternate destination root directory for package building
DESTDIR =

DEFS = -DHAVE_CONFIG_H
CC = gcc
CFLAGS = -fPIC
LOCAL_CFLAGS =  -DREADLINE_LIBRARY -DRL_LIBRARY_VERSION='"$(RL_LIBRARY_VERSION)"'
CPPFLAGS = 

INCLUDES = -I$(srcdir) -I$(top_srcdir) -I..

CCFLAGS  = $(DEFS) $(LOCAL_CFLAGS) $(INCLUDES) $(CPPFLAGS) $(CFLAGS)
LDFLAGS = -g -L.. 

READLINE_LIB = ../libreadline.a
HISTORY_LIB = ../libhistory.a

TERMCAP_LIB = -ltinfo

.c.o:
	${RM} $@
	$(CC) $(CCFLAGS) -c $<

SOURCES = excallback.c fileman.c histexamp.c manexamp.c rl-fgets.c rl.c \
		rlbasic.c rlcat.c rlevent.c rlptytest.c rltest.c rlversion.c \
		rl-callbacktest.c hist_erasedups.c hist_purgecmd.c 

EXECUTABLES = fileman$(EXEEXT) rltest$(EXEEXT) rl$(EXEEXT) rlcat$(EXEEXT) \
		rlevent$(EXEEXT) rlversion$(EXEEXT) histexamp$(EXEEXT) \
		rl-callbacktest$(EXEEXT) rlbasic$(EXEEXT) \
		hist_erasedups$(EXEEXT) hist_purgecmd$(EXEEXT)

OBJECTS = fileman.o rltest.o rl.o rlevent.o rlcat.o rlversion.o histexamp.o \
	  rl-callbacktest.o rlbasic.o hist_erasedups.o hist_purgecmd.o

OTHEREXE = rlptytest$(EXEEXT)
OTHEROBJ = rlptytest.o

all: $(EXECUTABLES)
everything: all

check:	rlversion$(EXEEXT)
	@echo Readline version: `rlversion$(EXEEXT)`

installdirs:
	-$(SHELL) $(top_srcdir)/support/mkdirs $(DESTDIR)$(installdir)

install:	installdirs
	@for f in $(SOURCES); do \
		$(RM) $(DESTDIR)$(installdir)/$$f ; \
		$(INSTALL_DATA) $(srcdir)/$$f $(DESTDIR)$(installdir) ; \
	done

uninstall:
	@for f in $(SOURCES); do \
		$(RM) $(DESTDIR)$(installdir)/$$f ; \
	done
	-rmdir $(DESTDIR)$(installdir)

rl$(EXEEXT): rl.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rl.o $(READLINE_LIB) $(TERMCAP_LIB)

rlbasic$(EXEEXT): rlbasic.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rlbasic.o $(READLINE_LIB) $(TERMCAP_LIB)

rlcat$(EXEEXT): rlcat.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rlcat.o $(READLINE_LIB) $(TERMCAP_LIB)

rlevent$(EXEEXT): rlevent.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rlevent.o $(READLINE_LIB) $(TERMCAP_LIB)

fileman$(EXEEXT): fileman.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ fileman.o $(READLINE_LIB) $(TERMCAP_LIB)

rltest$(EXEEXT): rltest.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rltest.o $(READLINE_LIB) $(TERMCAP_LIB)

rl-callbacktest$(EXEEXT): rl-callbacktest.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rl-callbacktest.o $(READLINE_LIB) $(TERMCAP_LIB)

rlptytest$(EXEEXT): rlptytest.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rlptytest.o $(READLINE_LIB) $(TERMCAP_LIB) $(LIBUTIL)

rlversion$(EXEEXT): rlversion.o $(READLINE_LIB)
	$(CC) $(LDFLAGS) -o $@ rlversion.o $(READLINE_LIB) $(TERMCAP_LIB)

histexamp$(EXEEXT): histexamp.o $(HISTORY_LIB)
	$(CC) $(LDFLAGS) -o $@ histexamp.o -lhistory $(TERMCAP_LIB)

hist_erasedups$(EXEEXT): hist_erasedups.o $(HISTORY_LIB)
	$(CC) $(LDFLAGS) -o $@ hist_erasedups.o -lhistory $(TERMCAP_LIB)

hist_purgecmd$(EXEEXT): hist_purgecmd.o $(HISTORY_LIB)
	$(CC) $(LDFLAGS) -o $@ hist_purgecmd.o -lhistory $(TERMCAP_LIB)

clean mostlyclean:
	$(RM) $(OBJECTS) $(OTHEROBJ)
	$(RM) $(EXECUTABLES) $(OTHEREXE) *.exe

distclean maintainer-clean: clean
	$(RM) Makefile

fileman.o: fileman.c
rltest.o: rltest.c
rl.o: rl.c
rlversion.o: rlversion.c
histexamp.o: histexamp.c
hist_erasedups.o: hist_erasedups.c
hist_purgecmd.o: hist_purgecmd.c
rlbasic.o: rlbasic.c
rlcat.o: rlcat.c
rlptytest.o: rlptytest.c
rl-callbacktest.o: rl-callbacktest.c

fileman.o: $(top_srcdir)/readline.h
rltest.o: $(top_srcdir)/readline.h
rl.o: $(top_srcdir)/readline.h
rlversion.o: $(top_srcdir)/readline.h
histexamp.o: $(top_srcdir)/history.h
hist_erasedups.o: $(top_srcdir)/history.h
hist_purgecmd.o: $(top_srcdir)/history.h
rlbasic.o: $(top_srcdir)/readline.h $(top_srcdir)/history.h
rlcat.o: $(top_srcdir)/readline.h $(top_srcdir)/history.h
rlptytest.o: $(top_srcdir)/readline.h $(top_srcdir)/history.h
rl-callbacktest.o: $(top_srcdir)/readline.h $(top_srcdir)/history.h
