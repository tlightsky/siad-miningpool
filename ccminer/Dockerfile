FROM ubuntu:16.04
RUN apt-get update \
    && apt-get install -y git build-essential automake libssl-dev libcurl4-openssl-dev

RUN cd /var/ && \
	git clone https://github.com/KlausT/ccminer.git

WORKDIR /var/ccminer

RUN cd /var/ccminer && \
    sh build.sh

ENTRYPOINT tail -f /dev/null # /var/ccminer/ccminer -asia -o stratum+tcp://sia:3333 -u morty