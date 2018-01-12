# makefile for rnx2rtkp

SRC     = ../../src

#OPTS    = -DTRACE -DENAGLO -DENAQZS -DENAGAL -DENACMP -DENAIRN -DNFREQ=3
OPTS    = -DTRACE -DENAGLO -DENAQZS -DENAGAL -DENACMP -DENAIRN -DNFREQ=3 -DIERS_MODEL
#OPTS    = -DENAGLO -DENAQZS -DENAGAL -DENACMP -DNFREQ=2

# for no lapack
CFLAGS  = -Wall -ansi -pedantic -Wno-unused-but-set-variable -I$(SRC) $(OPTS) -g -fPIC
#LDLIBS  = -lm -lrt
LDLIBS  = ../../lib/iers/gcc/iers.a -lgfortran -lm -lrt

#CFLAGS  = -Wall -O3 -ansi -pedantic -Wno-unused-but-set-variable -I$(SRC) -DLAPACK $(OPTS)
#LDLIBS  = -lm -lrt -llapack -lblas

# for gprof
#CFLAGS  = -Wall -O3 -ansi -pedantic -Wno-unused-but-set-variable -I$(SRC) -DLAPACK $(OPTS) -pg
#LDLIBS  = -lm -lrt -llapack -lblas -pg

# for mkl
##MKLDIR  = /opt/intel/mkl
#MKLDIR  = /proj/madoca/lib/mkl
#CFLAGS  = -O3 -ansi -pedantic -Wno-unused-but-set-variable -I$(SRC) $(OPTS) -DMKL
#LDLIBS  = -L$(MKLDIR)/intel64 -lmkl_intel_lp64 -lmkl_core -lmkl_gnu_thread -lpthread -lgomp -lm -lrt

all        : librtklib.so
librtklib.so  : rtkcmn.o rinex.o rtkpos.o postpos.o solution.o lambda.o geoid.o sbas.o preceph.o pntpos.o ephemeris.o options.o ppp.o ppp_ar.o ppp_corr.o rtcm.o rtcm2.o rtcm3.o rtcm3e.o ionex.o tides.o qzslex.o
	$(CC)  -fPIC -shared -o librtklib.so rtkcmn.o rinex.o rtkpos.o postpos.o solution.o lambda.o geoid.o sbas.o preceph.o pntpos.o ephemeris.o options.o ppp.o ppp_ar.o ppp_corr.o rtcm.o rtcm2.o rtcm3.o rtcm3e.o ionex.o tides.o qzslex.o

rtkcmn.o   : $(SRC)/rtkcmn.c
	$(CC) -c $(CFLAGS) $(SRC)/rtkcmn.c
rinex.o    : $(SRC)/rinex.c
	$(CC) -c $(CFLAGS) $(SRC)/rinex.c
rtkpos.o   : $(SRC)/rtkpos.c
	$(CC) -c $(CFLAGS) $(SRC)/rtkpos.c
postpos.o  : $(SRC)/postpos.c
	$(CC) -c $(CFLAGS) $(SRC)/postpos.c
solution.o : $(SRC)/solution.c
	$(CC) -c $(CFLAGS) $(SRC)/solution.c
lambda.o   : $(SRC)/lambda.c
	$(CC) -c $(CFLAGS) $(SRC)/lambda.c
geoid.o    : $(SRC)/geoid.c
	$(CC) -c $(CFLAGS) $(SRC)/geoid.c
sbas.o     : $(SRC)/sbas.c
	$(CC) -c $(CFLAGS) $(SRC)/sbas.c
preceph.o  : $(SRC)/preceph.c
	$(CC) -c $(CFLAGS) $(SRC)/preceph.c
pntpos.o   : $(SRC)/pntpos.c
	$(CC) -c $(CFLAGS) $(SRC)/pntpos.c
ephemeris.o: $(SRC)/ephemeris.c
	$(CC) -c $(CFLAGS) $(SRC)/ephemeris.c
options.o  : $(SRC)/options.c
	$(CC) -c $(CFLAGS) $(SRC)/options.c
ppp.o      : $(SRC)/ppp.c
	$(CC) -c $(CFLAGS) $(SRC)/ppp.c
ppp_ar.o   : $(SRC)/ppp_ar.c
	$(CC) -c $(CFLAGS) $(SRC)/ppp_ar.c
ppp_corr.o : $(SRC)/ppp_corr.c
	$(CC) -c $(CFLAGS) $(SRC)/ppp_corr.c
rtcm.o     : $(SRC)/rtcm.c
	$(CC) -c $(CFLAGS) $(SRC)/rtcm.c
rtcm2.o    : $(SRC)/rtcm2.c
	$(CC) -c $(CFLAGS) $(SRC)/rtcm2.c
rtcm3.o    : $(SRC)/rtcm3.c
	$(CC) -c $(CFLAGS) $(SRC)/rtcm3.c
rtcm3e.o   : $(SRC)/rtcm3e.c
	$(CC) -c $(CFLAGS) $(SRC)/rtcm3e.c
ionex.o    : $(SRC)/ionex.c
	$(CC) -c $(CFLAGS) $(SRC)/ionex.c
tides.o    : $(SRC)/tides.c
	$(CC) -c $(CFLAGS) $(SRC)/tides.c
qzslex.o   : $(SRC)/qzslex.c
	$(CC) -c $(CFLAGS) $(SRC)/qzslex.c

rnx2rtkp.o : $(SRC)/rtklib.h
rtkcmn.o   : $(SRC)/rtklib.h
rinex.o    : $(SRC)/rtklib.h
rtkpos.o   : $(SRC)/rtklib.h
postpos.o  : $(SRC)/rtklib.h
solution.o : $(SRC)/rtklib.h
lambda.o   : $(SRC)/rtklib.h
geoid.o    : $(SRC)/rtklib.h
sbas.o     : $(SRC)/rtklib.h
preceph.o  : $(SRC)/rtklib.h
pntpos.o   : $(SRC)/rtklib.h
ephemeris.o: $(SRC)/rtklib.h
options.o  : $(SRC)/rtklib.h
ppp.o      : $(SRC)/rtklib.h
ppp_ar.o   : $(SRC)/rtklib.h
rtcm.o     : $(SRC)/rtklib.h
rtcm2.o    : $(SRC)/rtklib.h
rtcm3.o    : $(SRC)/rtklib.h
rtcm3e.o   : $(SRC)/rtklib.h
ionex.o    : $(SRC)/rtklib.h
tides.o    : $(SRC)/rtklib.h
qzslex.o   : $(SRC)/rtklib.h

clean :
	rm -f rnx2rtkp rnx2rtkp.exe *.o *.pos *.trace

prof :
	gprof rnx2rtkp > prof.txt

