# Makefile for PF layer
LIB	= pf
INCDIR	= ${MINIREL_HOME}/h
INCS	=
SRCS	= pf.c
TESTS	= pftest.c
OBJS	= ${SRCS:.c=.o}
LIBS	= lib${LIB}.a ../bf/libbf.a

#############################################################################
# This macro definition can be overwritten by command-line definitions.
CC	= gcc
CFLAGS	= -g -ansi -pedantic
#CFLAGS	= -O -ansi -pedantic
#############################################################################

#all: lib${LIB}.a ${LIB}test shsontest
all: lib${LIB}.a ${LIB}test

${LIB}test: ${LIB}test.o ${LIBS}
	$(CC) $(CFLAGS) -o $@ $< ${LIBS}

../bf/libbf.a:
	cd ../bf && $(MAKE)

#shsontest: shsontest.o ${LIBS}
#	$(CC) $(CFLAGS) -o $@ $< ${LIBS}


lib${LIB}.a:$(OBJS)
	ar cr lib${LIB}.a $(OBJS)
	ranlib lib${LIB}.a

$(OBJS): ${INCS}

clean:
	cd ../bf && make clean
	rm -f lib${LIB}.a *.o ${LIB}test *.bak *~

.c.o:
	$(CC) $(CFLAGS) -c $< -I. -I$(INCDIR)

run:
	make clean; make; ./pftest; ./pftest > pftest.out; diff pftest.out pftest.out.orig
