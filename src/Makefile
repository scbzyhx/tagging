CC = gcc
INCLUDEDIR = ../include
LIBDIR += ../lib 
CFLAGS+=-m32
objects = iptc.o dump.o util.o
LIBS = /usr/lib64/libnetfilter_conntrack.so /lib64/libiptc.so.0-1.4.7

all:$(objects)
	${CC} -I ${INCLUDEDIR}   -L ${LIBDIR} ${LIBS}  $(objects) -o start

iptc.o:
	$(CC) -c -I $(INCLUDEDIR) iptc.c -o iptc.o
dump.o:
	$(CC) -c -I $(INCLUDEDIR) dump.c -o dump.o
util.o:
	$(CC) -c -I $(INCLUDEDIR) util.c -o util.o

#all1:
#	${CC} -I ${INCLUDEDIR} /usr/lib64/libnetfilter_conntrack.so /lib64/libiptc.so.0-1.4.7 -L ${LIBDIR} dump.c iptc.c -o dump
debug:
	${CC} -g -I ${INCLUDEDIR}  -L ${LIBDIR} ${LIBS} iptc.c dump.c util.c -o start


test_hash:util.o
	${CC} -g -I ${INCLUDEDIR}  -L ${LIBDIR} ${LIBS}  util.o test/test_hash.c -o hash_test
	./hash_test
test_iptc:$(objects)
	${CC} -g -I ${INCLUDEDIR}  -L ${LIBDIR} ${LIBS}  iptc.o test/test_iptc.c -o iptc_test
	./iptc_test
clean:
	rm -f *.o
	rm -f start
	rm -f hash_test
	rm -f iptc_test
