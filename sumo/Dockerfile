FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    software-properties-common git wget unzip build-essential cmake libfox-1.6-dev \
    libgdal-dev libproj-dev libxerces-c-dev python3 python3-pip \
    && add-apt-repository ppa:sumo/stable -y \
    && apt-get update && apt-get install -y sumo sumo-tools

WORKDIR /workspace
COPY data/ /workspace/data/