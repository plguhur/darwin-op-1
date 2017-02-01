###############################################################
#
# Purpose: Makefile for "monter_gyropode"
# Author.: robotis / P.L. Guhur
# Version: 0.1
# License: GPL
#
###############################################################

TARGET = monter_gyropode

INCLUDE_DIRS = -I../../Linux/include -I../../Framework/include

CXX = g++
CXXFLAGS += -g -DLINUX -Wall $(INCLUDE_DIRS)
#CXXFLAGS += -O2 -DDEBUG -DLINUX -Wall $(INCLUDE_DIRS)
LFLAGS += -lpthread -ljpeg -lrt

OBJECTS =   main.o

all: $(TARGET)

clean:
	rm -f *.a *.o $(TARGET) core *~ *.so *.lo

libclean:
	make -C ../../Linux/build clean

distclean: clean libclean

darwin.a:
	make -C ../../Linux/build

$(TARGET): darwin.a $(OBJECTS)
	$(CXX) $(CXXFLAGS) $(CFLAGS) $(LFLAGS) $(OBJECTS) ../../Linux/lib/darwin.a -o $(TARGET)
	chmod 755 $(TARGET)

# useful to make a backup "make tgz"
tgz: clean
	mkdir -p backups
	tar czvf ./backups/monter_gyropode_`date +"%Y_%m_%d_%H.%M.%S"`.tgz --exclude backups *
