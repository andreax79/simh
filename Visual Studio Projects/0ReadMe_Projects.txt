This dirctory contains a set of Visual Studio 2008 build projects for the 
current simh code base.  When used (with Visual Studio Express 2008 or 
Visual Studio Express 2010) it populates a directory tree under the BIN 
directory of the Simh distribution for temporary build files and produces 
resulting executables in the BIN/NT/Win32-Debug or BIN/NT/Win32-Release 
directories (depending on whether you target a Debug or Release build).  

The Visual Studio Projects expect that a winpcap developer pack and the
Posix threads for windows package are available in a directory parallel 
to the simh directory.  

For Example, the directory structure should look like:

    .../simh/simhv38-2-rc1/VAX/vax_cpu.c
    .../simh/simhv38-2-rc1/scp.c
    .../simh/simhv38-2-rc1/Visual Studio Projects/simh.sln
    .../simh/simhv38-2-rc1/Visual Studio Projects/VAX.vcproj
    .../simh/simhv38-2-rc1/BIN/Nt/Win32-Release/vax.exe
    .../simh/windows-build/pthreads/pthread.h
    .../simh/windows-build/winpcap/WpdPack/Include/pcap.h

The contents of the windows-build directory can be downloaded from:

    https://github.com/downloads/simh/simh/windows-build.zip


Network devices are capable of using pthreads to enhance their performance.  
To realize these benefits, you must build the desire simulator with 
USE_READER_THREAD defined.  The relevant simulators which have network 
support are VAX, VAX780 and PDP11.

Additionally, simulators which contain devices which use the asynchronous
APIs in sim_disk.c and sim_tape.c can also achieve greater performance by
leveraging pthreads to perform blocking I/O in separate threads.  Currently
the simulators which have such devices are VAX, VAX780 and PDP11.  To 
achieve these benefits the simulators must be built with SIM_ASYNCH_IO 
defined.

The project files in this directory build these simulators with support for
both network and asynchronous I/O.
