# This example Makefile is used to build an application using the libcxl
# archive library (libcxl.a) file.  This means your code is statically linked
# to the libcxl library.  Any changes to the libcxl library, such as moving
# to the hardware libcxl library, will require a full recompile of your code.
# The advantage to this method is that you do not need to set any envrionment
# variables for your executable to run.
#
# 
CC=gcc
APP=tinytest
COMMON_DIR=.libcxl/include
LIBCXL_DIR=./libcxl
LINKFLAGS=-lpthread -lrt
CFLAGS=-O2 -D_GNU_SOURCE

ifdef DEBUG
  CFLAGS = -g -DDEBUG
endif

all: $(APP).o $(LIBCXL_DIR)/libcxl.a
	$(CC) psl_dma.c -o $(APP) $^ $(LINKFLAGS) -I$(LIBCXL_DIR)

$(APP).o: $(APP).c
	$(CC) $(CFLAGS) -c -I$(COMMON_DIR) -I$(LIBCXL_DIR) $^

clean:
	rm -f $(APP) *.o
