ARG UBUNTU_SOURCE
FROM ubuntu:latest

# Set Environment Variables
ENV DEBIAN_FRONTEND noninteractive

# Start as root
USER root

RUN apt-get update -yqq && \
	apt-get install -yqq \
	aptitude \
	build-essential pkg-config subversion nano

ADD https://downloads.asterisk.org/pub/telephony/asterisk/asterisk-18-current.tar.gz .
RUN tar -xzf asterisk-18-current.tar.gz
RUN cd asterisk-18.3.0 && \
	sh ./contrib/scripts/install_prereq install
RUN cd asterisk-18.3.0 && \
	./configure && \
	make
RUN cd asterisk-18.3.0 && \
	make install && \
	make samples


