CC=gcc
CFLAGS=-std=c11 -Wall -Werror -Wextra -pedantic -g -Og
TYPE=char

all: show-store

cpp-store: store.c Makefile
	$(CC) $(CFLAGS) -DTYPE="$(TYPE)" -E store.c

store.s: store.c Makefile
	$(CC) $(CFLAGS) -DTYPE="$(TYPE)" -S store.c -o store.s

store.o: store.c Makefile
	$(CC) $(CFLAGS) -DTYPE="$(TYPE)" -c store.c -o store.o

show-store: store.s
	cat store.s | sed -E '/\s*\./d'

dump-store: store.o
	objdump -M no-aliases -d store.o

clean:
	rm -f store.o
	rm -f store.s

.PHONY: all store.s store.o cpp-store show-store dump-store clean
