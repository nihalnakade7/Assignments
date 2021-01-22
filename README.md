
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

$(BIN)/$(TARGET) : $(OBJECT) $(LIB)/$(LIBFILE) <br>
	$(CC) -o $@ $^  <br>

here bin/main which relies on obj files i.e. $(OBJECT)  and  lib file ($(LIB)/$(LIBFILE)) <br>
therefore it will call  <br>
$(OBJS)/%.o : $(SRC)/%.c   <br>
	$(CC) $(CFLAGS) -c $< -o $@  <br>
  
 now object files will be generaed. Here $(OBJS)/%.o has dependency on $(SRC)/%.c. So it will look for .c files <br>
 will create corresponding .o files <br>
 like: <br>
 gcc -Wall -Iinc -std=gnu99 -c src/file.c -o objs/file.o <br>
 and we get file.o as o/p file <br>
 
 similarly,  <br>
 $(LIB)/$(LIBFILE):  <br>
	ar rcs $@ $(OBJS)/*.o  <br>
  
  will generate lib(.a) files <br>
  Command: ar rcs lib/libfile.a objs/file1.o ....  <br>
  
  And at the end   <br>
  
$(BIN)/$(TARGET) : $(OBJECT) $(LIB)/$(LIBFILE)  <br>
	$(CC) -o $@ $^    <br>
  
  it will genarate main file inside bin dir  <br>
  
 command: gcc -o bin/main objs/file1.o .....   <br>
 
   
 Clean:     <br>
 rm objs/* bin/*    <br>
 
 remove all files from objs and bin directory <br>
 
