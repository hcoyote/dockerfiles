# 
# everything you need to get a basic Centos 6 environment
# up and running to build RPMs with fpm.
#
# to run:
# 
#   mkdir /tmp/fpmbuild
#   docker build -t fpm-cent6 .
#   docker run -ti -v /tmp/fpmbuild:/tmp/fpmbuild fpm-cent6
#
# This will drop you into a shell where you can add further yum
# dependencies before invoking your fpm command
#
# bonus:  by default, all build RPMs will end up in /tmp/fpmbuild,
#         which is available outside your container to make it easier
#         to transfer your built RPMs around.
#
FROM centos:6
RUN yum update -y
RUN yum -y install rubygems ruby-devel ruby-json gcc gcc-c++ python-setuptools rpm-build openssh-clients
RUN gem install cabin -v 0.7.2 && gem install fpm
RUN mkdir /tmp/fpmbuild
VOLUME ["/tmp/fpmbuild"]
WORKDIR /tmp/fpmbuild
RUN bash
