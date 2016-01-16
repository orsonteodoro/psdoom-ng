psdoom-ng
=========

psdoom-ng is a First Person Shooter operating system process killer based on psDooM and Chocolate Doom.


Compile and usage
-----------------

Quick guide: 

 1. Install all dependencies: gcc, make, libsdl, sdl_mixer, sdl_net, python.
 2. `cd trunk && ./configure && make`
 4. Get a copy of Doom, to copy the file Doom2.wad.
 3. Action! `./src/psdoom`

Find more information in:
 * trunk/COMPILE
 * trunk/CMDLINE
 * trunk/psdoom/README (specific options and instructions to find your processess)

Mac OS X
---------

Now with support for Mac OS X!

It is recommended use brew to install the depenedencies.


Support for external process source
-----------------------------------

You can use external commands as interface to retrieve, renice and kill process.

This makes it easy to adapt the tool to your needs, or even integrate it with external
services (AWS, heroku, vmware, etc).

For that, you only need to override these environment variables:

 * PSDOOMPSCMD List the processes. The command must print one space separated 
   line per process with the format: `<user> <pid> <processname> <is_daemon=[1|0]>`

    keymon 29 web4 1
    keymon 30 web3 1
    keymon 31 adis3 1
    keymon 32 core15 1
    keymon 20 core2 1

 * PSDOOMRENICECMD Command to renice the process. Will get the pid as argument

 * PSDOOMKILLCMD Command to kill the process. Will get the pid as argument


For example, in contrib you can find a script that interacts with cloudfoundry:

    cd trunk
    PSDOOMPSCMD="./contrib/psdoom-cf-ctl ps" \
    PSDOOMRENICECMD="true" \
    PSDOOMKILLCMD="./contrib/psdoom-cf-ctl kill" \
    ./src/psdoom


NOTE: psdoom does a synchronous call to the external commands (mono-thread). If your
command takes too long, you will feel hipcuts in the game. Try to make your commands
respond really fast! 
