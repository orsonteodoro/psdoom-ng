AUX_DIST_GEN =                          \
        $(ac_aux_dir)/install-sh        \
        $(ac_aux_dir)/missing

MSVC_FILES=                             \
        msvc/chocolate.sln              \
        msvc/config.h                   \
        msvc/doom.vcproj                \
        msvc/heretic.vcproj             \
        msvc/hexen.vcproj               \
        msvc/inttypes.h                 \
        msvc/libpcsound.vcproj          \
        msvc/libtextscreen.vcproj       \
        msvc/README                     \
        msvc/server.vcproj              \
        msvc/setup.vcproj               \
        msvc/stdint.h                   \
        msvc/win32.rc

CODEBLOCKS_FILES=                              \
        codeblocks/chocolate.workspace         \
        codeblocks/config.h                    \
        codeblocks/doom.cbp                    \
        codeblocks/game-res.rc                 \
        codeblocks/heretic.cbp                 \
        codeblocks/hexen.cbp                   \
        codeblocks/libpcsound.cbp              \
        codeblocks/libtextscreen.cbp           \
        codeblocks/README                      \
        codeblocks/server.cbp                  \
        codeblocks/setup.cbp                   \
        codeblocks/setup-res.rc

DOC_FILES=                              \
        README                          \
        README.Music                    \
        NEWS                            \
        PHILOSOPHY                      \
        ChangeLog

EXTRA_DIST=                             \
        $(AUX_DIST_GEN)                 \
        $(MSVC_FILES)                   \
        $(CODEBLOCKS_FILES)             \
        $(DOC_FILES)                    \
        NOT-BUGS                        \
        README.Strife                   \
        .lvimrc                         \
        HACKING                         \
        TODO                            \
        rpm.spec

PSDO0M_DOC_FILES=                       \
        CHANGELOG.psdoom-ng             \
        COPYING.psdoom-ng               \
        CREDITS.psdoom-ng               \
        README.psdoom-ng                \
        TODO.psdoom-ng

psdoomngdocsdir = ${docdir}/../psdoom-ng
psdoomngdocs_DATA = $(DOC_FILES) $(PSDO0M_DOC_FILES)

#doomdocsdir = ${docdir}/../${PROGRAM_PREFIX}doom
#doomdocs_DATA = $(DOC_FILES) NOT-BUGS

#hereticdocsdir = ${docdir}/../${PROGRAM_PREFIX}heretic
#hereticdocs_DATA = $(DOC_FILES)

#hexendocsdir = ${docdir}/../${PROGRAM_PREFIX}hexen
#hexendocs_DATA = $(DOC_FILES)

#strifedocsdir = ${docdir}/../${PROGRAM_PREFIX}strife
#strifedocs_DATA = $(DOC_FILES) README.Strife

MAINTAINERCLEANFILES =  $(AUX_DIST_GEN)

SUBDIRS=textscreen opl pcsound data src man

DIST_SUBDIRS=pkg $(SUBDIRS)

if HAVE_PYTHON

INSTALL : man/INSTALL.template man/simplecpp
	./man/simplecpp -DDOOM -DHERETIC -DHEXEN -DSTRIFE \
	                < man/INSTALL.template > $@

endif

psdoomngcfgdir = ${prefix}/share/psdoom-ng
psdoomngcfg_DATA = psdoom-ng.conf.example

psdoomngwrapperdir = ${prefix}/bin
psdoomngwrapper_PROGRAMS = psd

psd : psd.in
	cp psd.in psd
