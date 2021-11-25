CC=gcc
#CFLAGS?=-Wall -ggdb
CFLAGS?=-O2
LDFLAGS+=-lpcap -lrt 
PROGRAMS=ipv6-agent
LIBS=thc-ipv6-lib.o

PREFIX=/usr/local

# Number of RTTs and IATs
IAT?=5000
RTT?=500000
IFACE?=eth0

all:	$(LIBS) $(PROGRAMS)

%:	%.c $(LIBS)
	$(CC) $(CFLAGS) -o $@ $^ $(LDFLAGS)

run: $(PROGRAMS)
	sudo ./ipv6-agent $(IFACE) $(RTT) $(IAT)
	
clean:
	rm -f $(PROGRAMS) $(LIBS) core DEADJOE *~

backup:	clean
	tar czvf ../thc-ipv6-bak.tar.gz *
	sync

.PHONY: all install clean
