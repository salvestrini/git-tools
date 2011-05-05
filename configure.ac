#
# configure.ac
#
# Written by: Francesco Salvestrini <salvestrini@gmail.com>
#

AC_INIT([git-tools],[m4_esyscmd(build-aux/git-version-gen .tarball-version)],[salvestrini@gmail.com],[git-tools])

AC_PREREQ([2.65])

AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])

AM_INIT_AUTOMAKE([1.11 foreign no-installman no-installinfo -Wall])

AC_PROG_SED
AC_PROG_GREP
AC_PROG_MKDIR_P
AC_PROG_LN_S

AC_PATH_PROG([GIT], [git], [/bin/false])
AS_IF([test x"$GIT" = x""],[
    AC_MSG_ERROR([failed to find git executable])
])

GIT_EXEC_PATH=`$GIT --exec-path`
AC_SUBST([GIT_EXEC_PATH], [$GIT_EXEC_PATH])

AC_CONFIG_FILES([
        Makefile
])
AC_CONFIG_FILES([git-branch-create],[chmod u+x git-branch-create])
AC_CONFIG_FILES([git-branch-remove],[chmod u+x git-branch-remove])

AC_OUTPUT
