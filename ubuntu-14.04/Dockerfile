################################################################################### 
# Creates a ubuntu v14.04
#
# docker build --rm --build-arg http_proxy=$http_proxy -t rtzan/pam:ubuntu-14.04 .
# 
# docker run -it --net=host rtzan/pam:ubuntu-14.04 /bin/bash
# 
################################################################################### 
FROM ubuntu:14.04
MAINTAINER rtzan
# 
#Setup build environment for libpam
RUN apt-get update -y
RUN apt-get upgrade -y
RUN apt-get -y build-dep pam
# 
#Rebuild and istall libpam with --disable-audit option
RUN export CONFIGURE_OPTS=--disable-audit && cd /root && apt-get -b source pam && dpkg -i libpam-doc*.deb libpam-modules*.deb libpam-runtime*.deb libpam0g*.deb

################################################################################### 