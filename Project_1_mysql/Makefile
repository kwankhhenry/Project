#Parameters and Flags
CC	:= g++
CFLAGS := -Wall -fPIC#-std=c++11#-v #-g
LFLAGS := -shared
SRCDIR := src
BUILDDIR := build
LIBDIR := ../lib
TARGET := Database

SRCEXT := cpp
SOURCES := $(shell find -type f -name '*.$(SRCEXT)')
OBJECTS := $(patsubst ./%,$(BUILDDIR)/%,$(SOURCES:.$(SRCEXT)=.o))
INC := -I/usr/include/mysql -I/usr/include/mysql++ -I/home/admin/Home_Project/Project_8_ConsoleTable
LIB := -L/usr/lib -L/home/admin/Home_Project/lib
LNK := -lmysqlpp -lmysqlclient -lConsoleTable

$(TARGET): $(OBJECTS)
	@echo " Linking..."
	@echo " $(CC) -o $(TARGET) $^ $(LIB) $(LNK)"; 
		$(CC) -o $(TARGET) $^ $(LIB) $(LNK)

$(BUILDDIR)/%.o: ./%.$(SRCEXT)
	@echo " Building..."
	@mkdir -p $(BUILDDIR)
	@echo " $(CC) $(CFLAGS) $(INC) -o $@ -c $<"; 
		$(CC) $(CFLAGS) $(INC) -o $@ -c $<

lib: $(OBJECTS)
	@echo " Creating shared library..."
	@echo " $(CC) $(LFLAGS) -o $(LIBDIR)/lib$(TARGET).so $^";
		$(CC) $(LFLAGS) -o $(LIBDIR)/lib$(TARGET).so $^

clean:
	@echo " Cleaning...";
	@echo " $(RM) -r $(BUILDDIR) $(TARGET)"; 
		$(RM) -r $(BUILDDIR) $(TARGET)
	@echo " $(RM) -r $(LIBDIR)/lib$(TARGET).so";
		$(RM) -r $(LIBDIR)/lib$(TARGET).so
