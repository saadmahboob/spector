# ----------------------------------------------------------------------
# Copyright (c) 2016, The Regents of the University of California All
# rights reserved.
# 
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are
# met:
# 
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
# 
#     * Redistributions in binary form must reproduce the above
#       copyright notice, this list of conditions and the following
#       disclaimer in the documentation and/or other materials provided
#       with the distribution.
# 
#     * Neither the name of The Regents of the University of California
#       nor the names of its contributors may be used to endorse or
#       promote products derived from this software without specific
#       prior written permission.
# 
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL REGENTS OF THE
# UNIVERSITY OF CALIFORNIA BE LIABLE FOR ANY DIRECT, INDIRECT,
# INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
# BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS
# OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
# ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR
# TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE
# USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH
# DAMAGE.
# ----------------------------------------------------------------------


TARGET := $(MYOPENCL_HOST_CODE_FILE_NAME)_host

CC = g++

AOCL_COMPILE_CONFIG = $(shell aocl compile-config)
AOCL_LINK_CONFIG    = $(shell aocl link-config | sed 's/lterasic/laltera/g')

CL_DIR     = /opt/AMDAPPSDK-3.0
CL_INCLUDE = -I$(CL_DIR)/include/
CL_LIBS    = $(CL_DIR)/lib/x86_64/sdk/libOpenCL.so

SRC = $(MYOPENCL_HOST_CODE_FILE_NAME).cpp my_spmv_common.cpp

fpga:
	$(CC) $(SRC) $(AOCL_COMPILE_CONFIG) $(AOCL_LINK_CONFIG) -o $(TARGET) -DVERBOSE=$(VERBOSE_LEVEL)

cpu:
	$(CC) $(SRC) $(CL_INCLUDE) $(CL_LIBS) -o $(TARGET) -DVERBOSE=$(VERBOSE_LEVEL)

gpu: cpu

all: fpga

clean:
	rm $(TARGET)



