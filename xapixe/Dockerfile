# Sometimes you want to interact with a XenServer cluster and not be on the
# cluster itself. You can use the xapi xe tools provided by XenServer, but 
# they don't provide a native version for MacOS. Instead, we use a docker 
# container to run it under CentOS.
# 
# Pre-build: 
#   Acquire the latest vesrion of the xapi-xe RPM off the XenServer iso and
#   place it somewhere accessible to a remote rpm installation path.
# 
# To build:
#  Using defaults:
#    docker build -t xapixe .
#
#  Overriding default rpmpath
#    docker build -t xapixe --build-args http://path/to/xapi-xe.rpm .
#  
#
# To run:
# :; docker run -t -i -v $HOME/.xe:/root/.xe xenapi xe vm-list uuid=42bfcdef-9918-4ee0-b0d4-4a261fc4e8b6
#
# Example output:
# stunnel: LOG5[7:140183766485056]: stunnel 4.56 on x86_64-redhat-linux-gnu platform
# stunnel: LOG5[7:140183766485056]: Compiled/running with OpenSSL 1.0.1e-fips 11 Feb 2013
# stunnel: LOG5[7:140183766485056]: Threading:PTHREAD Sockets:POLL,IPv6 SSL:ENGINE,OCSP,FIPS Auth:LIBWRAP
# stunnel: LOG5[7:140183766485056]: Reading configuration from descriptor 4
# stunnel: LOG5[7:140183766485056]: FIPS mode is disabled
# stunnel: LOG5[7:140183766485056]: Configuration successful
# stunnel: LOG5[7:140183766485056]: Service [stunnel] accepted connection from unnamed socket
# stunnel: LOG5[7:140183766485056]: connect_blocking: connected 10.0.0.32:443
# stunnel: LOG5[7:140183766485056]: Service [stunnel] connected remote server from 172.17.0.2:40372
# uuid ( RO)           : 42bfcdef-9918-4ee0-b0d4-4a261fc4e8b6
#      name-label ( RW): Control domain on host: t0106
#     power-state ( RO): running
#
#
#
FROM centos:7
ARG rpmpath=http://10.15.34.217/isos/xapi-xe-1.9.57-8535.x86_64.rpm
MAINTAINER Travis Campbell <hcoyote+docker@ghostar.org>
RUN yum -y update \
  && yum -y install -q stunnel \
  && rpm -ivh $rpmpath 
