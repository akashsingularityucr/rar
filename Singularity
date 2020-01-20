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
    
    #cd ~
    mkdir mysudo
    cd mysudo
    wget https://docs.google.com/uc?id=0B3X9GlR6EmbnWksyTEtCM0VfaFE&export=download
    mv uc\?id\=0B3X9GlR6EmbnWksyTEtCM0VfaFE gdrive
    chmod +x gdrive
    install gdrive /usr/local/bin/gdrive


