include ../MakefileCommonOpt

CSUFF  := cc
HSUFF  := hh
LIBDIR := ../lib
NAME   := JetCore

SRCS    := $(wildcard *.$(CSUFF))
OBJS    := $(patsubst %.$(CSUFF),%.o,$(SRCS)) 
HEADERS := $(wildcard *.$(HSUFF))
DYNLIB  := lib$(NAME).so

# this sets the path for the objects files :
vpath %.o $(LIBDIR)
vpath %.so $(LIBDIR)

all : $(DYNLIB)

$(DYNLIB): $(OBJS) $(NAME)Dict.o
	$(LD) $(SOFLAGS) $(LDFLAGS) $(patsubst %,$(LIBDIR)/%,$^) $(ROOTLIBS) $(OutPutOpt) $(LIBDIR)/$@ \
	$(EXPLLINKLIBS)
	@echo "$@ done"

$(NAME)Dict.cpp:  $(HEADERS) $(NAME)LinkDef.hpp
	@echo "Generating dictionary $@...  $^"
	rootcint   -f $@ -c -p $(INCLUDE) $^

$(NAME)Dict.o:	$(NAME)Dict.cpp
	$(CXX) $(CXXFLAGS) $(INCLUDE) -c $^ -o $(LIBDIR)/$@

%.o : %.$(CSUFF) %.$(HSUFF) 
	$(CXX) $(CXXFLAGS) $(INCLUDE) -c $< -o $(LIBDIR)/$@

clean: 
	rm -f *.o *.so	*Dict.*
	rm -f $(patsubst %, $(LIBDIR)/%, $(OBJS)) $(LIBDIR)/$(NAME)Dict.o $(LIBDIR)/$(DYNLIB)

