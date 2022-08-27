
CC = gcc  # C compiler
CFLAGS = -fPIC -Wall -Wextra -O2 -g -I ../static_lib  # C flags
LDFLAGS = -L ../static_lib -ltarget -Wl,-rpath . # linking flags
RM = rm -f   # rm command
TARGET_LIB = main  # target lib

SRCS = main.c # source files
OBJS = $(SRCS:.c=.o)

.PHONY: all
all: ${TARGET_LIB}

$(TARGET_LIB): $(OBJS)
	$(CC) -o $@ $^ ${LDFLAGS} 

$(SRCS:.c=.d):%.d:%.c
	$(CC) $(CFLAGS) -MM $< >$@

include $(SRCS:.c=.d)

.PHONY: clean
clean:
	-${RM} ${TARGET_LIB} ${OBJS} $(SRCS:.c=.d)
