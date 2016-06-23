CPP_CC = g++
C_CC   = gcc

AR = ar
RM = rm

CDEBUG = -g

INC_DIR = ../include
OBJ_DIR = ../obj
LIB_DIR = ../lib
BIN_DIR = ../bin

all: $(LIB_DIR)/libCThread.a

CPP_SRC = \
CThread.cpp \
CThreadPool.cpp \

C_SRC = \
pthread_rdwr.c \

CPP_OBJS = $(patsubst %.cpp,$(OBJ_DIR)/%.o,$(CPP_SRC))

C_OBJS = $(patsubst %.c,$(OBJ_DIR)/%.o,$(C_SRC))

CPPFLAGS = \
-std=c++11 \
$(CDEBUG) \
-I$(INC_DIR) \
-I../../CThread/include \
-I../../CUtil/include \
-I. \

CFLAGS = \
$(CDEBUG) \
-I$(INC_DIR) \
-I../../CThread/include \
-I../../CUtil/include \
-I. \

clean:
	$(RM) -f $(OBJ_DIR)/*.o
	$(RM) -f $(LIB_DIR)/libCThread.a

.SUFFIXES: .cpp

$(CPP_OBJS): $(OBJ_DIR)/%.o: %.cpp
	$(CPP_CC) -c $< -o $(OBJ_DIR)/$*.o $(CPPFLAGS)

$(C_OBJS): $(OBJ_DIR)/%.o: %.c
	$(C_CC) -c $< -o $(OBJ_DIR)/$*.o $(CFLAGS)

$(LIB_DIR)/libCThread.a: $(CPP_OBJS) $(C_OBJS)
	$(AR) crv $(LIB_DIR)/libCThread.a $(CPP_OBJS) $(C_OBJS)
