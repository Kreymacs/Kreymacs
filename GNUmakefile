# Generated using: grep -oP "^[a-zA-Z-]+\:.*" Makefile | sed s/:.*// | grep -v PHONY | tr '\n' ' '
PHONY:

# Metadata
NAME ?= Kreymacs
VERSION = 0.0.0

# Command overrides
## These are used to support non-standard system configuration through exporting environment variables
EXIT ?= exit
PRINTF ?= printf
MKDIR ?= mkdir

# Directory overrides
BUILDDIR ?= "$(PWD)/build"
INSTAL ?= whatever

#@ Default target invoked on 'make' (outputs syntax error on this project)
all:
	@ "$(PRINTF)" '%s\n' "Target 'all' is not allowed, use 'make list' to list available targets or read the 'Makefile' file"
	@ "$(EXIT)" 2 # Syntax error exit

#@ List all targets
list:
	@ "$(PRINTF)" 'FIXME: %s\n' "Puts ': something' in the output, implement in a way that is comforming posix"
	@ "$(TRUE)" \
		&& "$(GREP)" -A 1 "^#@.*" Makefile | "$(SED)" s/--//gm | "$(SED)" "s/#@/#/gm" | while IFS= "$(READ)" -r line; do \
			case "$$line" in \
				"#"*|"") "$(PRINTF)" '%s\n' "$$line" ;; \
				*) "$(PRINTF)" '%s\n' "make $$line"; \
			esac; \
		done

#@ Output a help message
help:
	@ "$(PRINTF)" '%s\n' \
		"NOTE:  This is a brief summary of some common make targets." \
		"For more detailed information, please read the files INSTALL," \
		"INSTALL.REPO, Makefile or visit this URL:" \
		"https://www.gnu.org/prep/standards/html_node/Standard-Targets.html" \
		"" \
		"make build            -- compile and build $(NAME)" \
		"make install          -- install Emacs to the location specified by TARGETDIR variable" \
		"make TAGS             -- update tags tables" \
		"make clean            -- delete built files but preserve configuration" \
		"make mostlyclean      -- like 'make clean', but leave those files that" \
		"                         usually do not need to be recompiled" \
		"make distclean        -- delete all build and configuration files," \
		"                         leave only files included in source distribution" \
		"make maintainer-clean -- delete almost everything that can be regenerated" \
		"make bootstrap        -- delete all compiled files to force a new bootstrap" \
		"                         from a clean slate, then build in the normal way" \
		"make uninstall        -- remove files installed by 'make install'" \
		"make check            -- run the Emacs test suite" \
		"make docs             -- generate Emacs documentation in info format" \
		"make html             -- generate documentation in html format" \
		"make ps               -- generate documentation in ps format" \
		"make pdf              -- generate documentation in pdf format "
	@ "$(EXIT)" 0


#@ Clean the temporary files
clean:
	@ [ ! -d "$(BUILDDIR)" ] || "$(RM)" -r "$(BUILDDIR)"

#@ Buiold the project
build:
	@ [ -d "$(BUILDDIR)" ] || "$(MKDIR)" "$(BUILDDIR)"


# ---

# Build Emacs from a fresh tarball or version-control checkout.

# Copyright (C) 2011-2020 Free Software Foundation, Inc.
#
# This file is part of GNU Emacs.
#
# GNU Emacs is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GNU Emacs is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GNU Emacs.  If not, see <https://www.gnu.org/licenses/>.
#
# written by Paul Eggert


# This GNUmakefile is for GNU Make.  It is for convenience, so that
# one can run 'make' in an unconfigured source tree.  In such a tree,
# this file causes GNU Make to first create a standard configuration
# with the default options, and then reinvokes itself on the
# newly-built Makefile.  If the source tree is already configured,
# this file defers to the existing Makefile.

# If you want non-default build options, or if you want to build in an
# out-of-source tree, you should run 'configure' before running 'make'.
# But run 'autogen.sh' first, if the source was checked out directly
# from the repository.


# Display help.

ifeq (help,$(filter help,$(MAKECMDGOALS)))
help:
	@ "$(PRINTF)" '%s\n' \
		"NOTE:  This is a brief summary of some common make targets." \
		"For more detailed information, please read the files INSTALL," \
		"INSTALL.REPO, Makefile or visit this URL:" \
		"https://www.gnu.org/prep/standards/html_node/Standard-Targets.html" \
		"" \
		"make all              -- compile and build Emacs" \
		"make install          -- install Emacs" \
		"make TAGS             -- update tags tables" \
		"make clean            -- delete built files but preserve configuration" \
		"make mostlyclean      -- like 'make clean', but leave those files that" \
		"                         usually do not need to be recompiled" \
		"make distclean        -- delete all build and configuration files," \
		"                         leave only files included in source distribution" \
		"make maintainer-clean -- delete almost everything that can be regenerated" \
		"make bootstrap        -- delete all compiled files to force a new bootstrap" \
		"                         from a clean slate, then build in the normal way" \
		"make uninstall        -- remove files installed by 'make install'" \
		"make check            -- run the Emacs test suite" \
		"make docs             -- generate Emacs documentation in info format" \
		"make html             -- generate documentation in html format" \
		"make ps               -- generate documentation in ps format" \
		"make pdf              -- generate documentation in pdf format "
	@ "$(EXIT)" 0

.PHONY: help

else

# If a Makefile already exists, just use it.

ifeq ($(wildcard Makefile),Makefile)
include Makefile
else

# If cleaning and Makefile does not exist, don't bother creating it.
# The source tree is already clean, or is in a weird state that
# requires expert attention.

ifeq ($(filter-out %clean,$(or $(MAKECMDGOALS),default)),)

$(MAKECMDGOALS):
	@echo >&2 'No Makefile; skipping $@.'

else

# No Makefile, and not cleaning.
# If 'configure' does not exist, Emacs must have been checked
# out directly from the repository; run ./autogen.sh.
# Once 'configure' exists, run it.
# Finally, run the actual 'make'.

ORDINARY_GOALS = $(filter-out configure Makefile bootstrap,$(MAKECMDGOALS))

default $(ORDINARY_GOALS): Makefile
	$(MAKE) -f Makefile $(MAKECMDGOALS)
# Execute in sequence, so that multiple user goals don't conflict.
.NOTPARALLEL:

configure:
	@ "$(PRINTF)" '%s\n' \

	@ echo >&2 'There seems to be no "configure" file in this directory.'
	@ echo >&2 Running ./autogen.sh ...
	./autogen.sh
	@ echo >&2 '"configure" file built.'

Makefile: configure
	@ echo >&2 'There seems to be no Makefile in this directory.'
	@ echo >&2 'Running ./configure ...'
	./configure
	@ echo >&2 'Makefile built.'

# 'make bootstrap' in a fresh checkout needn't run 'configure' twice.
bootstrap: Makefile
	$(MAKE) -f Makefile all

.PHONY: bootstrap default $(ORDINARY_GOALS)

endif
endif
endif
