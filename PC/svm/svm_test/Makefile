ROOT_DIR=../../..

CXX=g++
CXXFLAGS= `pkg-config --cflags opencv` -std=c++11
LDLIBS= `pkg-config --libs opencv`
# --cflags
DEPS =

INCLUDES = -I../includes -I$(ROOT_DIR)/modules

SRC = $(wildcard ./*.cpp) \
      $(wildcard $(ROOT_DIR)/modules/*.cpp)
OBJ = $(SRC:.cpp=.o)

all: welcome clean svm_test

%.o: %.cpp $(DEPS)
	@echo Compiling $< with $(CXX)...
	$(CXX) -c $(INCLUDES) -o $@ $< $(CXXFLAGS)

svm_test:	$(OBJ)
	$(CXX) -o $@ $^ $(LDLIBS)

clean:
	rm -f *.o *~

less:
	less < <(all 2>&1)

welcome:
	@echo ---------------------------------------
	@echo ---- SVM Training + Save to file ------
	@echo ---------------------------------------

# (useful when debugging)
# redirect compilation output to less:
# less < <(make 2>&1)
