appname := gisttest

CXXFLAGS := -std=c++11

CXXFLAGS += -DUSE_FFTW

srcfiles := $(shell find ./GistTest -name "*.cpp")
srcfiles += $(shell find ../src/core -name "*.cpp")
srcfiles += ../src/fft/WindowFunctions.cpp
srcfiles += $(shell find ../src/mfcc -name "*.cpp")
srcfiles += $(shell find ../src/onset-detection-functions -name "*.cpp")
srcfiles += $(shell find ../src/pitch -name "*.cpp")
srcfiles += ../src/Gist.cpp

objects  := $(patsubst %.cpp, %.o, $(srcfiles))

all: $(appname)

LDLIBS += -pthread -lfftw3

LDFLAGS += -lboost_system -lboost_unit_test_framework

$(appname): $(objects)
	$(CXX) $(CXXFLAGS) $(LDFLAGS) -o $(appname) $(objects) $(LDLIBS)

depend: .depend

.depend: $(srcfiles)
	rm -f ./.depend
	$(CXX) $(CXXFLAGS) -MM $^>>./.depend;

clean:
	rm -f $(objects)

dist-clean: clean
	rm -f *~ .depend

include .depend

