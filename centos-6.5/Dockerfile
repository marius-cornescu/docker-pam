################################################################################### 
# Creates a centos v6.5
#
# docker build --rm --build-arg http_proxy=$http_proxy -t rtzan/pam:centos-6.5 .
# 
# docker run -it --net=host rtzan/pam:centos-6.5 /bin/bash
# 
################################################################################### 
FROM tianon/centos:6.5
MAINTAINER rtzan
# 
ARG http_proxy
# 
ENV http_proxy $http_proxy
ENV https_proxy $http_proxy
# 
ADD Centos-Source.repo /etc/yum.repos.d/Centos-Source.repo
# 
RUN touch /var/lib/rpm/* \
    && yum -y install yum-plugin-ovl
# 
RUN yum clean all \
    && yum -y update
# 
RUN yum clean all \
    && yum install -y tar bzip2 yum-utils rpm-build
# 
RUN yum-builddep -y pam
RUN yumdownloader --source pam
RUN rpmbuild --rebuild  --define 'WITH_AUDIT 0' --define 'dist +noaudit' pam*.src.rpm
RUN rpm -Uvh --oldpackage ~/rpmbuild/RPMS/*/pam*+noaudit*.rpm
# 
RUN rm -f /*.rpm
RUN rm -rf ~/rpmbuild
# 

################################################################################### 