##
## LINUX barebone makefile for c examples : good for all platforms
##
## Simply run make or make clean
##
## Intend this makefile only as a "batch examples updater" after library modification.
##
ifeq (,$(TOOLCHAIN_PREFIX))
$(error TOOLCHAIN_PREFIX is not set)
endif

ifeq (,$(CFLAGS))
$(error CFLAGS is not set)
endif

ifeq (,$(LDFLAGS))
$(error LDFLAGS is not set)
endif

LIB_PATH = ../../../build/bin/riscv64-linux/
Libs     = -lsnap7 
Wrapper  =snap7.cpp

CXX      = $(TOOLCHAIN_PREFIX)g++
CC       = $(TOOLCHAIN_PREFIX)gcc
CXXFLAGS =-O3
CFLAGS   += -L$(LIB_PATH) -Wl,-rpath=$(LIB_PATH) 
CXXFLAGS   += -L$(LIB_PATH) -Wl,-rpath=$(LIB_PATH) 

CFLAGS += -I$(SYSROOT)/usr/include
CXXFLAGS += -I$(SYSROOT)/usr/include

LDFLAGS += -L$(SYSROOT)/lib
LDFLAGS += -L$(SYSROOT)/usr/lib

.PHONY: all clean

all: 
	$(CXX) $(CFLAGS) $(CXXFLAGS) -o client ../client.cpp ../$(Wrapper) $(Libs) $(LDFLAGS)
	$(CXX) $(CFLAGS) $(CXXFLAGS) -o server ../server.cpp ../$(Wrapper) $(Libs) $(LDFLAGS)
	$(CXX) $(CFLAGS) $(CXXFLAGS) -o srv_resourceless ../srv_resourceless.cpp ../$(Wrapper) $(Libs) $(LDFLAGS)
	$(CXX) $(CFLAGS) $(CXXFLAGS) -o apartner ../apartner.cpp ../$(Wrapper) $(Libs) $(LDFLAGS)
	$(CXX) $(CFLAGS) $(CXXFLAGS) -o ppartner ../ppartner.cpp ../$(Wrapper) $(Libs) $(LDFLAGS)

clean:
	$(RM) client
	$(RM) server
	$(RM) srv_resourceless
	$(RM) apartner
	$(RM) ppartner
