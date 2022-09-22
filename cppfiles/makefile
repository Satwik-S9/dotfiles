CC = g++
MAIN = temp.cpp
CPP_FLAGS = -g
LINKER = /usr/bin/ld
LDFLAGS = -lm
TARGET = ../build
NAME = $(MAIN:%.cpp=%)

test: 
	echo "${MAIN} ${NAME}"

build: ${MAIN}
	${CC} ${CPP_FLAGS} $^ -o ${TARGET}/${NAME} ${LDFLAGS}

