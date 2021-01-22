
<p> #Folder desc <p>
bin --> Contains output file (main) <br>
inc --> Contains header files (*.h) <br>
lib --> lib files <br>
objs --> Object fiels (*.o) <br>
src --> Source Files (*.c) <br>

<h3> Makefile </h3>

TARGET --> Targe file (main) <br>

SRC, INC, BIN, OBJS, LIB contains dir names <br>
_OBJ_FILES --> obj files <br>

CFLAGS --> required header path <br>

$(BIN)/$(TARGET) : $(OBJECT) $(LIB)/$(LIBFILE)
	$(CC) -o $@ $^

here bin/main which relies on obj files i.e. $(OBJECT)  and  lib file ($(LIB)/$(LIBFILE))
therefore it will call 
$(OBJS)/%.o : $(SRC)/%.c
	$(CC) $(CFLAGS) -c $< -o $@
  
 now object files will be generaed. Here $(OBJS)/%.o has dependency on $(SRC)/%.c. So it will look for .c files
 will create corresponding .o files
 like:
 gcc -Wall -Iinc -std=gnu99 -c src/file.c -o objs/file.o
 and we get file.o as o/p file
 
 similarly, 
 $(LIB)/$(LIBFILE): 
	ar rcs $@ $(OBJS)/*.o 
  
  will generate lib(.a) files
  Command: ar rcs lib/libfile.a objs/file1.o ....
  
  And at the end 
  
$(BIN)/$(TARGET) : $(OBJECT) $(LIB)/$(LIBFILE)
	$(CC) -o $@ $^
  
  it will genarate main file inside bin dir
  
 command: gcc -o bin/main objs/file1.o .....
 
 
 Clean:
 rm objs/* bin/*
 
 remove all files from objs and bin directory
 
