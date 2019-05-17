# Creates a centos v7.5
#
# docker build -t pam_centos .
FROM centos:centos7.5.1804
MAINTAINER rtzan

ADD Centos-Source.repo /etc/yum.repos.d/Centos-Source.repo

RUN yum install -y yum-plugin-ovl && yum clean all

RUN yum update -y && yum clean all

RUN yum install -y tar bzip2 yum-utils rpm-build && yum clean all

RUN yum-builddep -y pam
RUN yumdownloader --source pam
# RUN rpmbuild --rebuild  --define 'WITH_AUDIT 0' --define 'dist +noaudit' pam*.src.rpm
# RUN rpm -Uvh --oldpackage ~/rpmbuild/RPMS/*/pam*+noaudit*.rpm

#RUN rm -f /*.rpm
#RUN rm -rf ~/rpmbuild
