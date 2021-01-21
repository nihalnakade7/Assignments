CC=gcc
CFLAGS= -I
DEPS= file_1.h file_2.h
OBJ = file_1.o file_2.o main.o



all:out

out:main
	gcc $(shell ls *.o) -o bin/main.out
main:
	for i in $(shell ls src/*.c) ; do \
		gcc -Iinc/ -c $${i} ; \
	done

clean:
	rm *.o bin/*.out

