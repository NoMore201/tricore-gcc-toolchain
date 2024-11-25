#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_INIT([tricore-toolchain],[1.0])

# Checks for programs.
AC_PROG_YACC
AC_PROG_CC
AC_PROG_LEX

AC_PATH_PROG([BASH], [bash],
	[AC_MSG_ERROR([bash not found])])

need_gcc_external_libraries="no"
AC_CHECK_LIB(gmp, __gmpz_init, ,
        [need_gcc_external_libraries="yes"])
AC_CHECK_LIB(mpfr, mpfr_init, ,
        [need_gcc_external_libraries="yes"])
AC_CHECK_LIB(mpc, mpc_init2, ,
        [need_gcc_external_libraries="yes"])
AS_IF([test x"$need_gcc_external_libraries" != xno],
      [AC_SUBST(NEED_GCC_EXTERNAL_LIBRARIES,true)],
      [AC_SUBST(NEED_GCC_EXTERNAL_LIBRARIES,false)])

AC_ARG_WITH(host,
	[AS_HELP_STRING([--with-host=x86_64-w64-mingw32],
			[Sets the host for the tools, you probably want nothing])],
	[],
	[with_host=default]
	)

AS_IF([test "x$with_host" != xdefault],
	[AC_SUBST(configure_host,--host=$with_host)],
	[AC_SUBST(configure_host,"")])

AC_ARG_WITH(binutils-src,
	[AS_HELP_STRING([--with-binutils-src],[Set binutils source path, use builtin source by default])],
	[],
	[with_binutils_src=default]
	)

AS_IF([test "x$with_binutils_src" != xdefault],
	[AC_SUBST(with_binutils_src,$with_binutils_src)],
	[AC_SUBST(with_binutils_src,"\$(srcdir)/tricore-binutils-gdb")])

AC_ARG_WITH(newlib-src,
	[AS_HELP_STRING([--with-newlib-src],[Set newlib source path, use builtin source by default])],
	[],
	[with_newlib_src=default]
	)

AS_IF([test "x$with_newlib_src" != xdefault],
	[AC_SUBST(with_newlib_src,$with_newlib_src)],
	[AC_SUBST(with_newlib_src,"\$(srcdir)/tricore-newlib-cygwin")])

AC_ARG_WITH(gcc-src,
	[AS_HELP_STRING([--with-gcc-src],[Set gcc source path, use builtin source by default])],
	[],
	[with_gcc_src=default]
	)

AS_IF([test "x$with_gcc_src" != xdefault],
	[AC_SUBST(with_gcc_src,$with_gcc_src)],
	[AC_SUBST(with_gcc_src,"\$(srcdir)/tricore-gcc")])

AC_CONFIG_FILES([Makefile])

AC_OUTPUT
