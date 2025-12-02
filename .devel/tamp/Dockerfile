FROM ubuntu:20.04
SHELL ["/bin/bash", "-c"]
ENV BASH_ENV="/etc/bash_env"


RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip \
    curl \
    && rm -rf /var/lib/apt/lists/*
RUN pip3 install flask requests numpy
RUN mkdir -p ~/testing/src
RUN cd ~/testing/src && git clone https://github.com/MarinhoLab/sas_ur_TAMP.git
