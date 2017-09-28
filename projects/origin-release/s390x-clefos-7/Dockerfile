#
# This is the image that controls the base dependencies for
# the standard build environment for releasing OpenShift Origin.
#
# The standard name for this image is openshift/origin-release:base
#
FROM        sinenomine/clefos-base-s390x:latest
MAINTAINER  Jason DeTiberus <jdetiber@redhat.com>

RUN mkdir -p /usr/share/info /usr/share/man/man1 /usr/share/man/man8 && \
    touch /usr/share/info/dir && \
    sed -i -e 's/distroverpkg=centos-release/distroverpkg=centos-release\noverride_install_langs=en_US.utf8/' /etc/yum.conf && \
    echo 'LANG="en_US.UTF-8"' > /etc/locale.conf && \
    INSTALL_PKGS="glibc-common" && \
    yum install -y "glibc-common" && \
    cp /usr/lib/locale/locale-archive /usr/lib/locale/locale-archive.tmpl && \
    build-locale-archive -l en && \
    yum reinstall -y findutils && \
    yum install -y https://kojipkgs.fedoraproject.org//work/tasks/5652/22125652/goversioninfo-0.1-1.fc28.s390x.rpm && \
    yum clean all
