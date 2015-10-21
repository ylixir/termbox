CC = gcc
CFLAGS = -O3 -fPIC -std=gnu99 -Wall -Wextra -D_XOPEN_SOURCE
SOURCES = $(wildcard *.c)
OBJECTS = $(SOURCES:%.c=%.o)

all: libtermbox.a libtermbox.so.1.0.0

libtermbox.a: $(OBJECTS)
	ar rcs $@ $^

libtermbox.so.1.0.0: $(OBJECTS)
	$(CC) -shared $(CFLAGS) -o $@ $^

$(OBJECTS): $(SOURCES)

.c.o:
	$(CC) $(CFLAGS) -c $< -o $@

install: all
	install -m 0644 libtermbox.so.1.0.0 /usr/lib/
	install -m 0644 libtermbox.a /usr/lib/
	install -m 0644 termbox.h /usr/include/
	ldconfig -n /usr/lib
.PHONY: uninstall
uninstall:
	rm -f /usr/lib/libtermbox.*
	rm -f /usr/include/termbox.*

.PHONY: clean
clean:
	rm -f *.o *.a *.so.1.0.0
