# Top-level convenience makefile for Micropolis build
# Usage: gmake       - build everything
#        gmake clean - clean everything

all:
	(cd tcl; gmake libtcl.a)
	(cd tk; gmake libtk.a)
	(cd tclx; gmake)
	cp tk/libtk.a tclx/libtk.a
	(cd sim; gmake)

clean:
	(cd tcl; gmake clean)
	(cd tk; gmake clean)
	(cd tclx; gmake clean)
	(cd sim; gmake clean)

rebuild: clean all
