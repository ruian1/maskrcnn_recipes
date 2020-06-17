FROM nvidia/cuda:9.0-cudnn7-devel-ubuntu16.04

MAINTAINER ran4@hawk.iit.edu

# ROOT6
RUN apt-get update && \
    apt-get install -y binutils \
	    	    	cmake \
			dpkg-dev \
			libfftw3-dev \
			gcc \
			g++ \
			gfortran \
			git \
			libgsl0-dev \
			libjpeg-dev \
			libpng-dev \
			libx11-dev \
			libxext-dev \
			libxft-dev \
			libxml2-dev \
			libxpm-dev \
			python3 \
			ipython-notebook \
			python3-dev \
			python3-pip\
			tar \
			wget && \
    wget https://root.cern.ch/download/root_v6.08.06.source.tar.gz && tar -zxvf root_v6.08.06.source.tar.gz -C /tmp/ && \
    mkdir -p /tmp/build && cd /tmp/build && \
    cmake -DCMAKE_INSTALL_PREFIX=/usr/local -DGNUINSTALL=ON /tmp/root-6.08.06 && \
    cmake --build . --target install -- -j4 && \
    rm /root_v6.08.06.source.tar.gz && rm -r /tmp/build && rm -r /tmp/root-6.08.06 && \
    apt-get autoremove -y && apt-get clean -y

# OPENCV3
RUN apt-get update && \
    apt-get install -y build-essential \
	    	    	cmake \
			git \
			libavcodec-dev \
			libavformat-dev \
			libdc1394-22-dev \
			libgtk2.0-dev \
			libjasper-dev \
			libjpeg-dev \
			libpng-dev \
			libswscale-dev \
			libtiff-dev \
			libtbb2 \
			libtbb-dev \
			pkg-config \
			python3-dev \
			python3-numpy \
			python3-pandas && \
    pip3 install root_numpy && \
    apt-get autoremove -y & apt-get clean -y & \
    mkdir -p /tmp/build && cd /tmp/ && \
    git clone https://github.com/Itseez/opencv source && cd source && \
    git checkout 3.4.0 && cd /tmp/build && \
    cmake -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr/local /tmp/source && \
    make -j4 && make install -j4 && \
    rm -r /tmp/build && rm -r /tmp/source && \
    apt-get autoremove -y && apt-get clean -y
