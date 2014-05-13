Building on Linux
===============

To build the only daemon, run the following commands
$ sudo apt-get install git-core build-essential libssl-dev libboost-all-dev libdb5.1-dev libdb5.1++-dev libgtk2.0-dev libminiupnpc-dev mingw32 synaptic libdb++-dev miniupnpc

First build cryptopp:

$ cd Primio/src/cryptopp

$ make static test dynamic


Install it into your usr/local/lib/

$ make install


Go back to the /src/ folder with 

$ cd ..


Build leveldb

$ cd leveldb


Give execution rights to the platform detection script

$ chmod +x build_detect_platform


Now build the libraries

$ make libleveldb.a libmemenv.a


Now navigate back to the /src/ folder

$ cd ..


And make the daemon with the following command

$ make -f makefile.unix


Optionally, debugging symbols can be removed from the binary to reduce it's size. This can be done using strip.

$ strip ./primiod


Then, to build the GUI, run the following commands:

$ sudo apt-get install git-core build-essential libssl-dev libboost-all-dev libdb5.1-dev libdb5.1++-dev libgtk2.0-dev libminiupnpc-dev qt4-qmake mingw32 synaptic qt-sdk qt4-dev-tools libqt4-dev libqt4-core libqt4-gui libdb++-dev miniupnpc


Navigate to the /primio/ folder

$ cd ..


To create a makefile the following command will have to be entered

$ qmake


When it is done configuring, use the following command to create the Qt version of the wallet

$ make


Troubleshooting:
-------------
Building miniupnpc
----------------

If your OS doesn't support libminiupnpc, you can build this manually by performing the following steps:

$ wget 'http://miniupnp.free.fr/files/download.php?file=miniupnpc-1.6.tar.gz' -O miniupnpc-1.6.tar.gz

$ tar -xzvf miniupnpc-1.6.tar.gz

$ cd miniupnpc-1.6
	
$ make

$ make install
