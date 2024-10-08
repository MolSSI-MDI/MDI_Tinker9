#------------------------------------------------------------#
# Docker file for an MDI engine
#------------------------------------------------------------#

FROM nvidia/cuda:12.1.0-devel-ubuntu18.04

RUN apt-get update -y && \
    apt-get install -y \
        wget \
        git \
        gfortran \
        vim \
        libmpich-dev && \
    rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

RUN apt-get remove --purge --auto-remove cmake -y && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends software-properties-common lsb-release && \
    apt-get clean all && \
    apt-get install ca-certificates -y --no-install-recommends && \
    wget -O - https://apt.kitware.com/keys/kitware-archive-latest.asc 2>/dev/null | gpg --dearmor - | tee /etc/apt/trusted.gpg.d/kitware.gpg >/dev/null && \
    apt-add-repository "deb https://apt.kitware.com/ubuntu/ $(lsb_release -cs) main" && \
    apt-get update -y && \
    apt-get install kitware-archive-keyring && \
    rm /etc/apt/trusted.gpg.d/kitware.gpg && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
        cmake python3-pip && \
    rm -rf /tmp/* /var/tmp/* /var/lib/apt/lists/*

# copy the build script
COPY .temp/build_image.sh .

# run the build script
RUN bash build_image.sh
