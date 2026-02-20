CXX := g++
UNAME_M := $(shell uname -m)
ifeq ($(UNAME_M),arm64)
  ARCH_FLAGS := -march=armv8-a+crypto
else
  ARCH_FLAGS := -march=native
endif
CXXFLAGS := -std=c++17 -O2 $(ARCH_FLAGS) -Wall -Wextra -I./include
BUILD := build

UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S),Darwin)
  LIBPVAC := $(BUILD)/libpvac.dylib
  SHARED_FLAGS := -dynamiclib
else
  LIBPVAC := $(BUILD)/libpvac.so
  SHARED_FLAGS := -shared
endif

all: $(LIBPVAC)

$(BUILD):
	mkdir -p $(BUILD)

$(LIBPVAC): pvac_c_api.cpp | $(BUILD)
	$(CXX) $(CXXFLAGS) -fPIC $(SHARED_FLAGS) -o $@ $<

clean:
	rm -rf $(BUILD)

.PHONY: all clean
