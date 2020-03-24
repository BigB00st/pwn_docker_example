# docker build -t ctf:ubuntu19.10 .
# docker run --rm -v $PWD:/pwd --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -d --name ctf -i ctf:ubuntu19.10
# docker exec -it ctf /bin/bash

FROM ubuntu:19.10

ENV LC_CTYPE C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive

RUN dpkg --add-architecture i386 && \
apt-get update && apt-get install -y \
build-essential \
jq \
strace \
ltrace \
iproute2 \
iputils-ping \
curl \
wget \
rubygems \
gcc \
dnsutils \
netcat \
gcc-multilib \
vim \
tmux \
gdb \
gdb-multiarch \
python \
python3 \
python3-pip \
python3-dev \
libssl-dev \
libffi-dev \
wget \
git \
make \
procps \
libpcre3-dev \
libdb-dev \
libxt-dev \
libxaw7-dev \
python-pip \
libc6:i386 \
libncurses5:i386 \
libstdc++6:i386 && \
rm -rf /var/lib/apt/lists/*

RUN pip install \
requests \
pwntools \
r2pipe && \
pip3 install -I \
unicorn==1.0.2rc2 \
pwntools \
capstone \
ropper

RUN mkdir tools && cd tools && \
git clone https://github.com/JonathanSalwan/ROPgadget && \
git clone https://github.com/radare/radare2 && cd radare2 && sys/install.sh && \
cd .. && git clone https://github.com/pwndbg/pwndbg && cd pwndbg && git checkout stable && ./setup.sh && \
cd .. && git clone https://github.com/niklasb/libc-database && cd libc-database && ./get

RUN gem install one_gadget && \
rm -rf /var/lib/gems/2.*/cache/*

COPY ./config /root/
