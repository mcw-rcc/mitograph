BootStrap: docker
From: ubuntu:16.04

%labels
    Maintainer Matthew Flister

%help
    This container runs Mitograph.

%post
    # add paths
    mkdir -p /scratch/global /scratch/local /rcc/stor1/refdata /rcc/stor1/depts /rcc/stor1/projects
  
    apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        gcc-multilib \
        cmake \
        wget \
        freeglut3-dev \
        ca-certificates
    apt-get clean

    wget https://www.vtk.org/files/release/7.1/VTK-7.1.1.tar.gz
    tar -xvf VTK-7.1.1.tar.gz && cd VTK-7.1.1
    mkdir build && cd build
    cmake .. && make && make install
    cd ~/ && rm -rf VTK-7.1.1*

    wget https://github.com/vianamp/MitoGraph/archive/v3.0.tar.gz
    tar -xvf v3.0.tar.gz && cd MitoGraph-3.0
    mkdir build && cd build
    cmake .. && make && cp MitoGraph /usr/local/bin
    cd ~/ && rm -rf v3.0* MitoGraph*
