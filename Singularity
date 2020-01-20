From: ubuntu:16.04
Bootstrap: docker

# rar/unrar tool for working with rar archives
# sudo singularity build rar.simg Singularity

%apprun create
    exec rar a "$@"

%apphelp create
    Create a rar archive.
        singularity run --app create rar.simg folder.rar folder/

    See "man rar" for other options.


%apphelp extract
    Extract a rar archive.
        singularity run --app extract rar.simg folder.rar folder/

    See "man unrar" for other options.

%apprun extract
    exec unrar x "$@"

%help
    This container provides the rar and unrar utilities. Running the container
    as is is akin to running the rar utility on Linux:
       ./rar.simg --help

    If you want to create or extract an archive, you can also use one of the apps
    provided:

        singularity apps rar.simg
          create
          extract

    Or ask for help for usage for one:

        $ singularity help --app create rar.simg 
        $ singularity help --app extract rar.simg 
   
%runscript
    exec rar "$@"

%post
    apt-get update && apt-get install -y rar unrar
    apt-get install -y apt-utils
    apt-get install -y wget
    
    # Set up the basics
    apt-get -y update
    apt-get install -y build-essential
    apt-get install -y git cmake build-essential libgcrypt11-dev libyajl-dev \
    libcurl4-openssl-dev libexpat1-dev binutils-dev
    apt-get -y update
    apt-get install -y zlib1g-dev libncurses5-dev libssl-dev pkg-config \
    libboost-all-dev libcppunit-dev
    # Install grive 
    mkdir -p /home/grive/Driveclient
    cd /home/grive/Driveclient
    git clone https://github.com/vitalif/grive2
    cd grive2
    mkdir build
    cd build
    cmake ..
    make -j4
    make install

%runscript 
    grive "$@"

