FROM debian:latest

# install dependencies
RUN apt-get update \
    && apt-get install -y \
        git \
        make gcc libelf-dev build-essential \
        python3 \
        python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && git config --global core.preloadindex true \
    && git config --global gc.auto 256

RUN mkdir /work
WORKDIR /work

# install kpatch-build
RUN git clone https://github.com/dynup/kpatch
WORKDIR /work/kpatch
RUN make -j`getconf _NPROCESSORS_CONF` build-kpatch-build
RUN make install-kpatch-build
RUN kpatch-build -h

WORKDIR /work
RUN git clone https://github.com/gentoo/elivepatch-server
WORKDIR /work/elivepatch-server
RUN pip3 install -r requirements.txt
RUN mv elivepatch_server/elivepatch_server.py elivepatch_server/elivepatch_server

# run a CMD to show git is installed
CMD PYTHONPATH="$PYTHONPATH:/work/elivepatch_server" python3 /work/elivepatch-server/elivepatch_server/elivepatch_server -d true
