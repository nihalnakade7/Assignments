

TARGET= main

SRC= src
INC= inc
BIN= bin
OBJS= objs

SOURCE = $(wildcard $(SRC)/*.c)
OBJECT = $(patsubst %,$(OBJS)/%, $(notdir $(SOURCE:.c=.o)))

CC= gcc
CFLAGS= -Wall -Iinc -std=gnu99

$(BIN)/$(TARGET) : $(OBJECT)
	$(CC) -o $@ $^

$(OBJS)/%.o : $(SRC)/%.c
	$(CC) $(CFLAGS) -c $< -o $@


clean :
	rm objs/*

