Atom Warehouse Server - README
==============================

This is the solution for Operating Systems Assignment #2.

How to compile:
---------------
$ make

How to clean:
-------------
$ make clean

How to run the server:
----------------------
$ ./atom_warehouse -T <tcp_port> -U <udp_port> -s <stream_path> -d <dgram_path> -o <oxygen> -h <hydrogen> -c <carbon> -t <timeout>

Example:
--------
$ ./atom_warehouse -T 5555 -U 5556 -s /tmp/my_stream -d /tmp/my_dgram -o 6 -h 12 -c 6 -t 30

How to interact with the server:
--------------------------------

1. TCP Client:
   $ echo "ADD OXYGEN 5" | nc localhost 5555

2. UDP Client:
   $ echo -n "DELIVER H2O 2" | nc -u -w1 localhost 5556

3. Console Input:
   > GEN CO2

4. UDS Stream:
   $ socat - UNIX-CONNECT:/tmp/my_stream
   (Then type commands like: ADD CARBON 2)

5. UDS Datagram:
   $ echo -n "DELIVER H2O 1" | socat - UNIX-SENDTO:/tmp/my_dgram

Files:
------
- server.c         - main server file
- inventory.c/h    - inventory and molecule logic
- Makefile         - compilation
- README.txt       - this file

