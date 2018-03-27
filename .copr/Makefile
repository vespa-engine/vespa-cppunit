TOP = $(realpath $(dir $(lastword $(MAKEFILE_LIST))))

# Version
MAJOR=1
MINOR=12
PATCH=1

RPMTOPDIR=$(TOP)/rpmbuild
SOURCEDIR=$(RPMTOPDIR)/SOURCES
SPECDIR=$(RPMTOPDIR)/SPECS
SPECFILE=$(SPECDIR)/vespa-cppunit.spec

all:
	mkdir -p $(SPECDIR) $(SOURCEDIR)
	cat vespa-cppunit.spec.tmpl | sed "s/_TMPL_VER_MAJOR/$(MAJOR)/" | sed "s/_TMPL_VER_MINOR/$(MINOR)/" | sed "s/_TMPL_VER_PATCH/$(PATCH)/" > $(SPECFILE)
	spectool -g -C $(SOURCEDIR) $(SPECFILE)
	cp -a patch*.txt $(SOURCEDIR)
	rpmbuild -bs --define "_topdir $(RPMTOPDIR)" $(SPECFILE)

clean:
	-rm -rf $(RPMTOPDIR)

.PHONY: all clean
