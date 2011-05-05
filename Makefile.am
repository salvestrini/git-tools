#
# Makefile.am
#
# Written by: Francesco Salvestrini <salvestrini@gmail.com>
#

ACLOCAL_AMFLAGS  = -I m4 --install
EXTRA_DIST       =
DISTCLEANFILES   =
BUILT_SOURCES    =

porcelaindir=$GIT_EXEC_PATH

porcelain_SCRIPTS =				\
	git-branch-create			\
	git-branch-remove

.PHONY: AUTHORS
AUTHORS:
	$(GIT) log --format="%aN <%aE>" | $(SORT) | $(UNIQ) > AUTHORS || { \
		rm -f AUTHORS ;						   \
		exit 1 ;						   \
        }

EXTRA_DIST     += AUTHORS
DISTCLEANFILES += AUTHORS

BUILT_SOURCES  += $(top_srcdir)/.version
$(top_srcdir)/.version:
	echo $(VERSION) > $@-t && mv $@-t $@

dist-hook:
	echo $(VERSION) > $(distdir)/.tarball-version

.PHONY: ChangeLog
ChangeLog:
	rm -f ChangeLog &&						     \
	$(GIT) log --decorate --format="%aN <%aE>:%d%n  %s%n" --date-order > \
		ChangeLog || {						     \
		rm -f ChangeLog ;					     \
		exit 1 ;						     \
	}

EXTRA_DIST += ChangeLog
