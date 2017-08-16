# Dockerfile
FROM debian:jessie

MAINTAINER "Fabio Botelho"

ENV DEBIAN_FRONTEND noninteractive 

#install the basics> net-tools, ssh server and nano editor
RUN apt-get update && apt-get install -y \ 
    net-tools \ 
    openssh-server \ 
    nano
	
#set root password to 12345678a
RUN echo 'root:12345678a' | chpasswd	

# configure sshd_config to accept root login
RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

# create a docker user
RUN useradd docker \
	&& mkdir /home/docker \
	&& chown docker:docker /home/docker \
	&& addgroup docker staff \
	&& addgroup docker sudo \
	&& true

#set password for docker user to 12345678a
RUN echo 'docker:12345678a' | chpasswd	
		
#start ssh		
ENTRYPOINT service ssh start && bash;
