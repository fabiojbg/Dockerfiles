# Dockerfile
FROM centos:6.9

MAINTAINER "Fabio Botelho"

ENV DEBIAN_FRONTEND noninteractive 

#install the basics> net-tools, ssh server and nano editor
RUN yum install -y nano  
RUN yum install -y net-tools 
RUN yum install -y openssh-server
	
#set root password to 12345678a
RUN echo 'root:12345678a' | chpasswd	

# configure sshd_config to accept root login
RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

# create a docker user
RUN useradd docker 
RUN chown docker:docker /home/docker 

#set password for docker user to 12345678a
RUN echo 'docker:12345678a' | chpasswd	
		
#start ssh		
ENTRYPOINT service sshd start && bash;

