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



# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.

AC_OUTPUT([Makefile src/bin/Makefile
                   src/sbin/Makefile])
