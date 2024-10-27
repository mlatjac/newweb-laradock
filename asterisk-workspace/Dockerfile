ARG UBUNTU_SOURCE
FROM ubuntu:latest

# Set Environment Variables
ENV DEBIAN_FRONTEND noninteractive

# Start as root
USER root

RUN apt-get update -yqq && \
	apt-get install -yqq \
	aptitude \
	build-essential pkg-config nano git iputils-ping traceroute

EXPOSE 5060 8088 8089



