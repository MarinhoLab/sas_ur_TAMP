FROM sinannaseel10/foxy-python3.9:latest
ENV DEBIAN_FRONTEND=noninteractive

RUN mkdir -p ~/testing/src
RUN cd ~/testing && git clone https://github.com/MarinhoLab/coast.git && cd coast && pip install -e .
RUN cd ~/testing/coast && mkdir -p external && cd external && \
    git clone --branch coast_changes https://github.com/branvu/pybullet-planning.git && \
    cd pybullet-planning && pip install -e . && cd .. && \
    git clone https://github.com/aibasel/downward.git && \
    cd downward && git checkout bc6cf7a691fa43276f19b92a7c70c3098e7672ef && \
    python3 build.py && cd .. && \
    git clone https://github.com/branvu/symbolic.git && \
    cd symbolic && \
    pip install cmake==3.25 && \
    pip install --no-build-isolation -e . && cd ../..

WORKDIR /root/testing/src
CMD ["/bin/bash"]
