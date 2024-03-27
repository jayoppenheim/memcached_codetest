# memcached_codetest

This practice test originates from the GitHub blog:
https://quuxplusone.github.io/blog/2022/01/06/memcached-interview/

To build the program:

cd memcached-1.4.15
./configure
make

Run the program:

./memcached

We can talk to the server via the default memcached port, port 11211. Its protocol is basically plain text, so we can use plain old telnet to talk to it. (If you don’t have telnet anymore, substitute the words nc -c for telnet.)

$ telnet 127.0.0.1 11211
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

Example usage, define and increment a stored value:

set age 0 3600 2
37
STORED
incr age 1

The challenge: Modifying memcached
Via its incr and decr commands, memcached provides a built-in way to atomically add 
 to a number. But it doesn’t provide other arithmetic operations; in particular, there is no “atomic multiply by 
” operation.

Your programming challenge: Add a mult command to memcached.

When you’re done, I should be able to telnet to your memcached client and run commands like

mult age 10
380
You have three hours. Go!
