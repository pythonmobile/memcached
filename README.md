# Memcached

Memcached is a high performance multithreaded event-based key/value cache
store intended to be used in a distributed system.

See: https://memcached.org/about

A fun story explaining usage: https://memcached.org/tutorial

If you're having trouble, try the wiki: https://memcached.org/wiki

If you're trying to troubleshoot odd behavior or timeouts, see:
https://memcached.org/timeouts

https://memcached.org/ is a good resource in general. Please use the mailing
list to ask questions, github issues aren't seen by everyone!

## Dependencies

* libevent, https://www.monkey.org/~provos/libevent/ (libevent-dev)
* libseccomp, (optional, experimental, linux) - enables process restrictions for
  better security. Tested only on x86_64 architectures.
  
## Building

To build memcached in your machine from local repo you will have to install
autotools, automake and libevent. In a debian based system the installation
and compilation commands look like this: 

```bash
sudo apt-get install autotools-dev
sudo apt-get install automake
sudo apt-get install libevent-dev
rm -rf memcached
git clone https://github.com/memcached/memcached.git
cd memcached 
./autogen.sh
./configure --enable-extstore
make
make test
```

It should create the binary in the same folder, which you can run

cd memcached && ./memcached

You can telnet into that memcached to ensure it is up and running

telnet 127.0.0.1 11211
stats


## Environment

Be warned that the -k (mlockall) option to memcached might be
dangerous when using a large cache.  Just make sure the memcached machines
don't swap.  memcached does non-blocking network I/O, but not disk.  (it
should never go to disk, or you've lost the whole point of it)

## Website

* https://www.memcached.org

## Contributing

See https://github.com/memcached/memcached/wiki/DevelopmentRepos
