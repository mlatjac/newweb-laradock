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
	./configure
RUN cd asterisk-18.3.0 && \
	make menuselect.makeopts && \
	menuselect/menuselect --enable \
	codec_opus codec_g729a \
	CORE-SOUNDS-EN-WAV CORE-SOUNDS-EN-ULAW \
	CORE-SOUNDS-EN-ALAW CORE-SOUNDS-EN-GSM \
	CORE-SOUNDS-EN-G729 CORE-SOUNDS-EN-G722 \
	CORE-SOUNDS-EN-SLN16 CORE-SOUNDS-EN-SIREN7 CORE-SOUNDS-EN-SIREN14 \
	menuselect.makeopts
RUN cd asterisk-18.3.0 && \
	make
RUN cd asterisk-18.3.0 && \
	make install && \
	make samples


