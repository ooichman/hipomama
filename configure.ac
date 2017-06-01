#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([hipomama], [0.1], [two.oes@gmail.com])
AC_CONFIG_SRCDIR([src/sbin/hipomamad.c])
AM_INIT_AUTOMAKE
AC_CONFIG_HEADERS([config.h])
LT_PREREQ([2.2])
LT_INIT([dlopen])
AC_CONFIG_MACRO_DIR([m4])
PKG_PROG_PKG_CONFIG

# Remember externally set CFLAGS
EXTERNAL_CFLAGS="$CFLAGS"


# Checks for programs.
AC_PROG_CC
AC_PROG_INSTALL
AM_PROG_CC_C_O

# Checks for libraries.

dnl checking for sqlite biraries
AC_SEARCH_LIBS([sqlite3_open], [sqlite3], [have_sqlite=yes],
   [AC_MSG_ERROR(["unable to locate sqlite3 libraries"])])

# Checks for header files.

dnl checking for header files for sqlite3
AC_CHECK_HEADERS([sqlite3.h], [have_sqlite=yes],
   [AC_MSG_ERROR(["unable to locate the sqlite3.h header file"])])

PKG_CHECK_MODULES([SQLITE3], [sqlite3], [have_libsqlite3=yes], [have_libsqlite3=no])
AM_CONDITIONAL([LIB_SQLITE3],  [test "$have_libsqlite3" = "yes"])

# Add debug support
AC_ARG_ENABLE(debug,
  AS_HELP_STRING(
    [--enable-debug],
    [enable debugging, default: no]),
    [case "${enableval}" in
      yes) debug=true ;;
      no)  debug=false ;;
      *)   AC_MSG_ERROR([bad value ${enableval} for --enable-debug]) ;;
    esac],
    [debug=false])
AM_CONDITIONAL(DEBUG, test x"$debug" = x"true")
AM_COND_IF(DEBUG,
    AC_DEFINE(DEBUG, 1, [Define to 0 if this is a release build]),
    AC_DEFINE(DEBUG, 0, [Define to 1 or higher if this is a debug build]))

# check for header files

AC_HEADER_STDC
AC_CHECK_HEADERS([stdio.h])

# adding AC OUTPUT files

AC_OUTPUT([Makefile src/bin/Makefile
                   src/sbin/Makefile])
