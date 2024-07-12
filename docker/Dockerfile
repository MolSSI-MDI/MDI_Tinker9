#------------------------------------------------------------#
# Docker file for an MDI engine
#------------------------------------------------------------#

FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

ARG MPI_USER=mpiuser
ARG HOME_DIR=/home/${MPI_USER}
ARG SSH_DIR=${HOME_DIR}/.ssh

# copy the build script
COPY .temp/build_image.sh .

# run the build script
RUN chmod +x ./build_image.sh && \
    ./build_image.sh
