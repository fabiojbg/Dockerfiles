# Dockerfile debian-jessie with essential tools
FROM debian:jessie

ENV DEBIAN_FRONTEND noninteractive 
RUN apt-get update && apt-get install -y \ 
    build-essential \ 
    nano \ 
    net-tools \ 
    openssh-server \ 
    wget
