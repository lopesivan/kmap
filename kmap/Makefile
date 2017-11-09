CC = g++ 
AR = ar
WC = wc

PROGRAM = kmm

CFLAGS = `wx-config --cxxflags` -Wall -pipe 

LFLAGS = -L/usr/local/lib/ -L/usr/lib/
CPPFLAGS =

# implementation

.SUFFIXES:      .o .cpp

SOURCES := $(wildcard *.cpp)
OBJECTS := $(patsubst %.cpp,%.o,$(SOURCES))
DEPENDS := $(patsubst %.cpp,%.d,$(SOURCES))

all: $(PROGRAM)

# Main Program
$(PROGRAM): $(OBJECTS) $(DEPENDS)
	$(CC) -o $(PROGRAM) $(OBJECTS) $(LFLAGS) `wx-config --libs --cxxflags`


%.o: %.cpp
	$(CC) -c $(CFLAGS) -o $@ $<

clean:
	rm -f $(OBJECTS) $(PROGRAM) $(DEPENDS) record.a
	rm -rf ./doxy_docs/

depend:  $(DEPENDS)

# How to create the Dependency files
%.d: %.cpp
	$(CC) -M $(CFLAGS) $< > $@
	$(CC) -M $(CFLAGS) $< | sed s/\\.o/.d/ > $@

# Include the dependencies that we created
-include $(DEPENDS)

