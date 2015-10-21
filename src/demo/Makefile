CC = gcc
CFLAGS = -O3 -fPIC -std=gnu99 -Wall -Wextra -D_XOPEN_SOURCE
SOURCES = $(wildcard *.c)
OBJECTS = $(SOURCES:%.c=%.o)
TARGETS = $(OBJECTS:%.o=%)

all: $(TARGETS)

$(TARGETS): $(OBJECTS)

$(OBJECTS): $(SOURCES)

.c.o:
	$(CC) $(CFLAGS) -c $< -o $@

%:%.o
	$(CC) $(CFLAGS) -o $@ $< -ltermbox
.PHONY: clean
clean:
	rm -f *.o keyboard output
