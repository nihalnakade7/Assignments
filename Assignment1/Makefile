

TARGET= main

SRC= src
INC= inc
BIN= bin
OBJS= objs
LIB=lib
LIBFILE=libmylib.a

SOURCE = $(wildcard $(SRC)/*.c)
#SOURCE = fiile_1.c file_2.c main.c
_OBJ_FILES= file_1.o file_2.o main.o
OBJECT = $(patsubst %,$(OBJS)/%,$(_OBJ_FILES))

CC= gcc
CFLAGS= -Wall -Iinc -std=gnu99

$(BIN)/$(TARGET) : $(OBJECT) $(LIB)/$(LIBFILE)
	$(CC) -o $@ $^

$(OBJS)/%.o : $(SRC)/%.c
	$(CC) $(CFLAGS) -c $< -o $@


$(LIB)/$(LIBFILE): 
	ar rcs $@ $(OBJS)/*.o

clean :
	rm objs/* bin/*

