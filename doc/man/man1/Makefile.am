htmldir = ${datadir}/doc/${PACKAGE}-${SLURM_VERSION_STRING}/html

man1_MANS = \
	sacct.1 \
	sacctmgr.1 \
	salloc.1 \
	sattach.1 \
	sbatch.1 \
	sbcast.1 \
	scancel.1 \
	scontrol.1 \
	scrun.1 \
	scrontab.1 \
	sdiag.1	\
	sinfo.1   \
	slurm.1 \
	sprio.1 \
	squeue.1 \
	sreport.1 \
	srun.1 \
	sshare.1 \
	sstat.1 \
	strigger.1

if BUILD_HDF5
man1_MANS += sh5util.1
endif

if BUILD_SVIEW
man1_MANS += sview.1
endif

if HAVE_MAN2HTML

html_DATA = \
	sacct.html \
	sacctmgr.html \
	salloc.html \
	sattach.html \
	sbatch.html \
	sbcast.html \
	scancel.html \
	scontrol.html \
	scrun.html \
	scrontab.html \
	sdiag.html \
	sinfo.html \
	sprio.html \
	squeue.html \
	sreport.html \
	srun.html \
	sshare.html \
	sstat.html \
	strigger.html

if BUILD_HDF5
html_DATA += sh5util.html
endif

if BUILD_SVIEW
html_DATA += sview.html
endif

MOSTLYCLEANFILES = ${html_DATA}

SUFFIXES = .html

.1.html:
	`dirname $<`/../man2html.py @SLURM_MAJOR@.@SLURM_MINOR@ $(srcdir)/../../html/header.txt $(srcdir)/../../html/footer.txt $<

endif
