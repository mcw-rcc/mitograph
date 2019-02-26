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
        git \
        ca-certificates
    apt-get clean

    wget https://www.vtk.org/files/release/8.2/VTK-8.2.0.tar.gz
    tar -xvf VTK-8.2.0.tar.gz && cd VTK-8.2.0
    mkdir build && cd build
    cmake .. && make && make install
    cd ~/ && rm -rf VTK-8.2.0*

    git clone https://github.com/vianamp/MitoGraph.git
    cd MitoGraph && sed -i 's/VTK 7.0/VTK 8.2.0/g' CMakeLists.txt
    mkdir build && cd build
    cmake .. && make && cp MitoGraph /usr/local/bin
    cd ~/ && rm -rf MitoGraph
