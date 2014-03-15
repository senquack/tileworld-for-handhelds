PLATFORM_GCW=1

#CFLAGS=-O0 -c -g -Wall
CFLAGS=-c -flto -O3 -Wall

LDFLAGS=

#GP2X:
#GPLDFLAGS=-L/opt/open2x/gcc-4.1.1-glibc-2.3.6/lib -Wl,-rpath,/opt/open2x/gcc-4.1.1-glibc-2.3.6/lib \
#		-static -lSDL_gfx -lSDL_image -ljpeg -lpng12 -lz -lSDL_mixer -lmikmod -lvorbisidec -lmad -lSDL \
#		 -lpthread -lgcc -lm -lc -ldl -msoftfloat
#GCW (debug):
#GPLDFLAGS=-L/opt/gcw0-toolchain/usr/mipsel-gcw0-linux-uclibc/sysroot/usr/lib -Wl,-rpath,/opt/gcw0-toolchain/usr/mipsel-gcw0-linux-uclibc/sysroot/usr/lib \
#		-lSDL_image -lSDL_gfx -ljpeg -lpng14 -lz -lSDL_mixer -lvorbisidec -lvorbisfile -lvorbis -lSDL \
#		 -lpthread -lgcc -lm -lc  
#GCW (optimized)
GPLDFLAGS=-flto -O3 -L/opt/gcw0-toolchain/usr/mipsel-gcw0-linux-uclibc/sysroot/usr/lib -Wl,-rpath,/opt/gcw0-toolchain/usr/mipsel-gcw0-linux-uclibc/sysroot/usr/lib \
		-lSDL_image -lSDL_gfx -ljpeg -lpng14 -lz -lSDL_mixer -lvorbisidec -lvorbisfile -lvorbis -lSDL \
		 -lpthread -lgcc -lm -lc  

#PCLDFLAGS=-L/usr/lib -Wl,-rpath,/usr/lib -lSDL -lpthread -lSDL_gfx -lSDL_image -lz -lpng12 -lSDL_mixer \
#		 -lmikmod  -lgcc 

SOURCES=cmdline.c encoding.c err.c fileio.c help.c lxlogic.c mslogic.c play.c random.c res.c \
		score.c series.c solution.c tworld.c unslist.c \
		oshw-sdl/SFont.c oshw-sdl/ccicon.c oshw-sdl/sdlerr.c oshw-sdl/sdlin.c \
		oshw-sdl/sdloshw.c oshw-sdl/sdlout.c oshw-sdl/sdlsfx.c oshw-sdl/sdltext.c \
		oshw-sdl/sdltile.c oshw-sdl/sdltimer.c oshw-sdl/port_cfg.c


OBJECTS=$(SOURCES:.c=.o)
EXECUTABLEPC=tworld
EXECUTABLEGP=tworld

CC=/opt/gcw0-toolchain/usr/bin/mipsel-gcw0-linux-uclibc-gcc
CFLAGS+=-I/opt/gcw0-toolchain/usr/mipsel-gcw0-linux-uclibc/sysroot/usr/include \
		-I/opt/gcw0-toolchain/usr/mipsel-gcw0-linux-uclibc/sysroot/usr/include/SDL \
		-D_REENTRANT \
		-DPLATFORM_GCW

all: 
#	make pcversion
#	make cleanobjs
#	make arm=1 gpversion
	make gpversion
	#make gpold

pcversion: $(SOURCES) $(EXECUTABLEPC)


gpversion: $(SOURCES) $(EXECUTABLEGP)


$(EXECUTABLEPC): $(OBJECTS) 
	$(CC) $(LDFLAGS) $(PCLDFLAGS) $(OBJECTS) -o $@


#$(EXECUTABLEGP): $(OBJECTS) 
#	$(CC) $(LDFLAGS) $(GPLDFLAGS) $(OBJECTS) -o $@
$(EXECUTABLEGP): $(OBJECTS) 
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@ $(GPLDFLAGS)


.c.o:
	$(CC) $(CFLAGS) $< -o $@

cleanobjs:
	rm -f $(OBJECTS)

clean:
	-rm -f tworld *~ *.o *.bak oshw-sdl/*.o oshw-sdl/*.bak oshw-sdl/*~

