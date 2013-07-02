EXTRACFLAGS=
OPT_CFLAGS=-O4
MXMLC_DEBUG=false

BUILDDIR = build
SRCDIR = .
INCLUDE := -I$(SRCDIR)
SRCS = flash_ui/as3api.cpp flash_ui/dmy_renderer.cpp flash_ui/flash_renderer.cpp flash_ui/glue.cpp gb_core/mbc.cpp gb_core/apu.cpp gb_core/cheat.cpp gb_core/cpu.cpp gb_core/lcd.cpp gb_core/rom.cpp gb_core/gb.cpp gbr_interface/gbr.cpp
LIBS = -lAS3++

MODULES = $(SRCS:.c=.o)
MODULES := $(MODULES:.cpp=.o)


TARGET  = tgb_dual
STATICLIB = lib$(TARGET).a
SWC = $(TARGET).swc


.PHONY: all clean

all: $(BUILDDIR) check
	@echo "-------- $(TARGET)"
	make $(BUILDDIR)/$(SWC)

$(BUILDDIR):
	@mkdir -p $(BUILDDIR)
	@mkdir -p $(BUILDDIR)/flash_ui
	@mkdir -p $(BUILDDIR)/gb_core
	@mkdir -p $(BUILDDIR)/gbr_interface

$(BUILDDIR)/%.o : %.c
	$(FLASCC)/usr/bin/gcc $(CFLAGS) $(OPT_CFLAGS) $(INCLUDE) -c $< -o $@

$(BUILDDIR)/%.o : %.cpp
	$(FLASCC)/usr/bin/$(CXX) $(CXXFLAGS) $(OPT_CFLAGS) $(INCLUDE) -c $< -o $@

$(BUILDDIR)/$(STATICLIB): $(patsubst %,$(BUILDDIR)/%,$(MODULES))
	cd $(BUILDDIR) && $(FLASCC)/usr/bin/$(AR) r $(STATICLIB) $(MODULES)

$(BUILDDIR)/$(SWC): $(patsubst %,$(BUILDDIR)/%,$(MODULES))
	cd $(BUILDDIR) && $(FLASCC)/usr/bin/g++ $(OPT_CFLAGS) $(LIBS) $(MODULES) -emit-swc=$(TARGET) -o $(SWC)

clean:
	@rm -f -r build

include Makefile.common
