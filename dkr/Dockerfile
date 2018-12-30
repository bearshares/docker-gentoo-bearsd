FROM ubuntu:16.04

RUN apt update
RUN apt install -y build-essential 
RUN apt install -y automake 
RUN apt install -y cmake 
RUN apt install -y g++ 
RUN apt install -y git 
RUN apt install -y libbz2-dev 
RUN apt install -y libsnappy-dev 
RUN apt install -y libssl-dev 
RUN apt install -y libtool 
RUN apt install -y make 
RUN apt install -y pkg-config 
RUN apt install -y python3 
RUN apt install -y python3-jinja2

# Boost packages (also required)
RUN apt install -y libboost-chrono-dev 
RUN apt install -y libboost-context-dev 
RUN apt install -y libboost-coroutine-dev 
RUN apt install -y libboost-date-time-dev 
RUN apt install -y libboost-filesystem-dev 
RUN apt install -y libboost-iostreams-dev 
RUN apt install -y libboost-locale-dev 
RUN apt install -y libboost-program-options-dev 
RUN apt install -y libboost-serialization-dev 
RUN apt install -y libboost-signals-dev 
RUN apt install -y libboost-system-dev 
RUN apt install -y libboost-test-dev 
RUN apt install -y libboost-thread-dev

# Optional packages (not required, but will make a nicer experience)
RUN apt install -y doxygen 
RUN apt install -y libncurses5-dev 
RUN apt install -y libreadline-dev 
RUN apt install -y perl

RUN git clone https://github.com/bearshares/bears
RUN cd bears; \
    git submodule update --init --recursive; \
    mkdir build
RUN cd bears/build; \
    cmake -DCMAKE_BUILD_TYPE=Release ..
RUN cd bears/build; \
    make -j$(nproc) bearsd
RUN cd bears/build; \
    make -j$(nproc) cli_wallet
# optional
RUN cd bears/build; \
    make install  # defaults to /usr/local

RUN apt install -y zsh

VOLUME /work
WORKDIR /work                  

CMD tail -f /dev/null #
# CMD bearsd 1>>/work/bearsd.log 2>>/work/bearsd.log
