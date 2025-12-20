
CFLAGS = -Wall -O2 -DARCH="Linux" -DMATRIXSTORAGE -DNETWORKOUT
FFLAGS = -Wall -O2 -cpp 

CC=cc
FC=gfortran

.c.o :
	$(CC) $(CFLAGS) -c $<
.f.o :
	$(FC) $(FFLAGS) -c $<

include Makefile.inc

SCCXMAIN = ccx_2.23.c

OCCXF = $(SCCXF:.f=.o)
OCCXC = $(SCCXC:.c=.o)
OCCXMAIN = $(SCCXMAIN:.c=.o)

DIR=
LIBS = -llapack -lblas -lm

ccx_2.23: $(OCCXMAIN) ccx_2.23.a  $(LIBS)
	./date.pl; $(CC) $(CFLAGS) -c ccx_2.23.c; $(FC)  -Wall -O2 -o $@ $(OCCXMAIN) ccx_2.23.a $(LIBS) -fopenmp

ccx_2.23.a: $(OCCXF) $(OCCXC)
	ar vr $@ $?
