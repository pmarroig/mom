# The following three directory may need to set.
NETCDFPATH = /usr/local/netcdf-3.6.2
SHAREDIR = $(PWD)/../../shared/mosaic
COREDIR  = $(PWD)
TOOLSHAREDIR = $(PWD)/../shared
CFLAGS = -O2 -fast -I$(TOOLSHAREDIR) -I$(COREDIR) -I$(SHAREDIR) -I${NETCDFPATH}/include -I/usr/include
LDFLAGS =  -L${NETCDFPATH}/lib -lm -lnetcdf
DEFFLAG = -Duse_netCDF
LNFLAGS = -v
CC      = icc

OBJS = mosaic_util.o create_xgrid.o read_mosaic.o mpp.o mpp_domain.o mpp_io.o  river_regrid.o tool_util.o interp.o

HEADERS = Makefile $(TOOLSHAREDIR)/mpp.h  $(TOOLSHAREDIR)/mpp_domain.h   \
          $(TOOLSHAREDIR)/mpp_io.h $(SHAREDIR)/mosaic_util.h                    \
          $(SHAREDIR)/interp.h $(SHAREDIR)/create_xgrid.h
river_regrid: $(OBJS)
	$(CC) $(LNFLAGS) -o $@ $(OBJS) $(LDFLAGS)

river_regrid.o: $(COREDIR)/river_regrid.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(COREDIR)/river_regrid.c 

mosaic_util.o: $(SHAREDIR)/mosaic_util.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(SHAREDIR)/mosaic_util.c


create_xgrid.o: $(SHAREDIR)/create_xgrid.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(SHAREDIR)/create_xgrid.c 

interp.o: $(SHAREDIR)/interp.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(SHAREDIR)/interp.c 

read_mosaic.o: $(SHAREDIR)/read_mosaic.c $(HEADERS)
	$(CC) $(DEFFLAG) $(CFLAGS) -c $(SHAREDIR)/read_mosaic.c 

mpp.o: $(TOOLSHAREDIR)/mpp.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(TOOLSHAREDIR)/mpp.c 

mpp_domain.o: $(TOOLSHAREDIR)/mpp_domain.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(TOOLSHAREDIR)/mpp_domain.c 

mpp_io.o: $(TOOLSHAREDIR)/mpp_io.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(TOOLSHAREDIR)/mpp_io.c

tool_util.o: $(TOOLSHAREDIR)/tool_util.c $(HEADERS)
	$(CC) $(CFLAGS) -c $(TOOLSHAREDIR)/tool_util.c


