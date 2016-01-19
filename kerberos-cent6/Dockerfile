FROM centos:6
MAINTAINER Travis Campbell <hcoyote@ghostar.org>
RUN yum -y update \
  && rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
RUN yum -y install -q krb5-libs krb5-server krb5-workstation

EXPOSE 88
EXPOSE 749

ADD	krb5.conf /etc/krb5.conf
RUN	echo "*/admin@GHOSTAR.ORG    *" > /var/kerberos/krb5kdc/kadm5.acl
RUN	touch /etc/krb5.keytab ; chmod 640 /etc/krb5.keytab

ADD	bashrc /.bashrc
