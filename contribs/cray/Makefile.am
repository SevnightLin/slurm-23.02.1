#
# Makefile for cray tools
#

SUBDIRS = csm slurmsmwd

AUTOMAKE_OPTIONS = foreign

if HAVE_NATIVE_CRAY
sbin_SCRIPTS = slurmconfgen.py
noinst_DATA = opt_modulefiles_slurm
endif

AM_CPPFLAGS = -I$(top_srcdir) -I$(top_srcdir)/src/common $(JSON_CPPFLAGS)

if WITH_JSON_PARSER
convenience_libs = $(LIB_SLURM)
sbin_PROGRAMS = capmc_suspend capmc_resume
capmc_suspend_SOURCES  = capmc_suspend.c
capmc_suspend_LDADD    = $(convenience_libs)
capmc_suspend_LDFLAGS  = $(JSON_LDFLAGS)
capmc_resume_SOURCES   = capmc_resume.c
capmc_resume_LDADD     = $(convenience_libs)
capmc_resume_LDFLAGS   = $(JSON_LDFLAGS)
endif

# Don't rely on autoconf to replace variables outside of makefiles
opt_modulefiles_slurm: opt_modulefiles_slurm.in Makefile
	sed -e 's|@prefix[@]|$(prefix)|g' \
	    -e 's|@MUNGE_DIR[@]|$(MUNGE_DIR)|g' \
	    -e 's|@libdir[@]|$(libdir)|g' \
	    ${abs_srcdir}/opt_modulefiles_slurm.in >opt_modulefiles_slurm

slurmconfgen.py: slurmconfgen.py.in Makefile
	sed -e 's|@sysconfdir[@]|$(sysconfdir)|g' \
	    ${abs_srcdir}/slurmconfgen.py.in >slurmconfgen.py

clean-generic:
	rm -f opt_modulefiles_slurm slurmconfgen.py

force:
$(convenience_libs) : force
	@cd `dirname $@` && $(MAKE) `basename $@`
