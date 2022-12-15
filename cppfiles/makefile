# COMPILER BASED FLAGS
CC=g++
CPP_SOURCES= $(wildcard include/custom/*.cpp)
HEADERS= $(wildcard include/custom/*.h)
OBJ= ${CPP_SOURCES:%.cpp=%.o}

# BASIC FLAGS
SRC_NAME=recsys.cpp
MAIN= src/$(SRC_NAME)
CPP_FLAGS= 
FILE_FLAGS=
INC_PARAMS= -I include/ 
LDFLAGS= -lm 
FOPENMP= -fopenmp
LINKER= usr/bin/ld
BLD_NAME= $(SRC_NAME:%.cpp=%)
TARGET= build/$(BLD_NAME)

# CPP MAIN FILE PARAMS
LAMBDA=0.01
MAXITER=10
RANK=20
THREADS=6
DATADIR=./datasets/movielens100k/ml-100k

# Generic Rules
%.o: %.cpp ${HEADERS}
	${CC} ${CPP_FLAGS} ${INC_PARAMS} -c $< -o $@ ${LDFLAGS} && echo "${HEADERS}"

test:
	echo "${MAIN} :: ${TARGET} :: ${INC_PARAMS} :: ${HEADERS} :: ${OBJ}"

src: ${OBJ}
	${CC} ${CPP_FLAGS} ${INC_PARAMS} ${MAIN} $^ -o ${TARGET} ${LDFLAGS} ${FOPENMP}

clean:
	rm include/custom/*.o

refresh:
	make src && make clean

run:
	./${TARGET} ${DATADIR} ${RANK} ${LAMBDA} ${THREADS} ${MAXITER}

all:
	time make src && echo "\n\n" && time make clean
