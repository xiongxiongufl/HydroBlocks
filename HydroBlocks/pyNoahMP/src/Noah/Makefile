# Makefile 
#
.SUFFIXES:
.SUFFIXES: .o .F

include ../user_build_options

OBJS = \
	module_sf_noahmplsm.o \
	module_sf_noahmp_glacier.o \
	module_sf_noahmp_groundwater.o \
	module_sf_myjsfc.o \
	module_sf_sfclay.o \
        pyNoahMP.o

CPPHRLDAS = -D_HRLDAS_OFFLINE_

all:	$(OBJS)

.F.o:
	@echo ""
	$(RM) $(*).f90
	$(CPP) $(CPPFLAGS) $(CPPHRLDAS) $(*).F > $(*).f90
	$(COMPILERF90) -o $(@) -c $(MODFLAG). $(MODFLAG)../Utility_routines $(F90FLAGS) $(LIBS) $(FREESOURCE) $(*).f90
	@echo ""

#
# Dependencies:
#
module_sf_noahmplsm.o:	module_sf_myjsfc.o module_sf_sfclay.o
#module_sf_noahmpdrv.o:	module_sf_noahmplsm.o module_sf_noahmp_glacier.o module_sf_noahmp_groundwater.o

#
# This command cleans up object (etc) files:
#

clean:
	$(RM) *.o *.mod *.stb *~ *.f90

