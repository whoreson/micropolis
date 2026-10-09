XINCLUDE = /usr/local/include
XLIB = /usr/local/lib
TCLHOME = ../tcl
TKHOME = ../tk
TCLXHOME = ../tclx
TCLLIBRARY = /usr/local/lib/tcl
TKLIBRARY = /usr/local/lib/tk

CC = gcc

OPTFLAGS = -O3
#OPTFLAGS = -g

#DEFINES = -DIS_LINUX -DCAM -DNET
DEFINES = -DIS_LINUX -DNO_AIRCRASH

CFLAGS = $(OPTFLAGS) $(DEFINES)

LDFLAGS = -L/usr/local/lib

INSTALL = install -s

INCLUDES = \
	-Iheaders \
	-I$(XINCLUDE) \
	-I$(TCLHOME) \
	-I$(TCLXHOME)/src \
	-I$(TKHOME)

CPPFLAGS = $(INCLUDES)

LIBS =	$(TCLXHOME)/libtk.a \
	$(TCLXHOME)/libtcl.a \
	-lm \
	-L/usr/local/lib \
        -lX11 \
        -lXext \
	-lXpm

SRCS = \
	sim.c \
	s_alloc.c \
	s_disast.c \
	s_eval.c \
	s_gen.c \
	s_init.c \
	s_msg.c \
	s_power.c \
	s_scan.c \
	s_sim.c \
	s_traf.c \
	s_zone.c \
	s_fileio.c \
	g_setup.c \
	g_ani.c \
	g_bigmap.c \
	g_map.c \
	g_smmaps.c \
	w_stubs.c \
	w_sound.c \
	w_resrc.c \
	w_keys.c \
	w_util.c \
	w_con.c \
	w_eval.c \
	w_budget.c \
	w_graph.c \
	w_date.c \
	w_update.c \
	w_tool.c \
	w_x.c \
	w_tk.c \
	w_sim.c \
	w_editor.c \
	w_map.c \
	w_sprite.c \
	w_piem.c \
	w_inter.c \
	w_cam.c \
	g_cam.c \
	w_net.c \
	rand.c \
	random.c

HEADERS = \
	headers/mac.h \
	headers/macros.h \
	headers/sim.h \
	headers/view.h \
	headers/animtab.h

OBJS = $(SRCS:.c=.o)
ALLOBJS = $(OBJS)

all: sim

lint:
	alint $(INCLUDES) $(SRCS) > LINT

$(TCLHOME)/libtcl.a:
	(cd $(TCLHOME); gmake libtcl.a)

$(TKHOME)/libtk.a: $(TCLHOME)/libtcl.a
	(cd $(TKHOME); gmake libtk.a)

$(TCLXHOME)/libtcl.a: $(TCLHOME)/libtcl.a
	(cd $(TCLXHOME); gmake)

$(TCLXHOME)/libtk.a: $(TKHOME)/libtk.a
	cp $(TKHOME)/libtk.a $(TCLXHOME)/libtk.a

sim: $(ALLOBJS) $(TCLXHOME)/libtk.a $(TCLXHOME)/libtcl.a
	$(CC) $(CFLAGS) $(LDFLAGS) $(INCLUDES) $(ALLOBJS) $(LIBS) -o sim

clean:
	rm -f $(OBJS) \
	 sim a.out core gmon.out *~ *.BAK Headers/*~

etags:
	etags $(SRCS) $(HEADERS)
