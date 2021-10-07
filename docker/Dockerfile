FROM --platform=linux/amd64 centos:7.9.2009

LABEL maintainer="ldfandian@hotmail.com"
LABEL version="0.1.0"

# basic management tools
ENV LC_ALL=en_US.UTF-8
RUN yum update --assumeyes \
  && yum install --assumeyes iproute2 procps lsb-release build-essential net-tools iputils-ping file \
  && yum install --assumeyes git vim python3 wget curl

# install basic dev tools
RUN yum install --assumeyes g++ gcc make cmake json-c-devel makedepend bison autotools-dev autoconf automake m4 perl gcc-c++ libgcc libstdc++.so.6

# install automake-1.14 (not in the centos 7.9 package)
RUN yum erase --assumeyes automake \
  && wget -O /tmp/automake-1.14-1.el7.x86_64.rpm http://repo.okay.com.mx/centos/7/x86_64/release/automake-1.14-1.el7.x86_64.rpm \
  && rpm -i /tmp/automake-1.14-1.el7.x86_64.rpm \
  && rm -f /tmp/automake-1.14-1.el7.x86_64.rpm

# install dependent devel libs
RUN yum install --assumeyes ld-linux.so.2 libz.so.1 bzip2 zlib zlib-devel \
  && yum install --assumeyes glibc-devel glibc glib2 glib2-devel
RUN yum install --assumeyes gtk2 gtk2-devel pygtk2 pygtk2-devel gdbm gdbm-devel libglade2-devel \
  && yum install --assumeyes libdaemon libdaemon-devel \
  && yum install --assumeyes intltool xmltoman doxygen openssl openssl-devel libnl libnl-devel

# install gtk3 (3.8.8 old version)
RUN yum update --assumeyes \
  && yum erase --assumeyes gtk3 gtk3-devel \
  && yum install --assumeyes compat-libcolord1 cairo-gobject cairo-gobject-devel at-spi2-atk at-spi2-atk-devel \
  && wget -O /tmp/gtk3-3.8.8-5.el7.x86_64.rpm https://buildlogs.centos.org/centos/7/os/x86_64-latest/Packages/gtk3-3.8.8-5.el7.x86_64.rpm \
  && wget -O /tmp/gtk3-devel-3.8.8-5.el7.x86_64.rpm https://buildlogs.centos.org/centos/7/os/x86_64-latest/Packages/gtk3-devel-3.8.8-5.el7.x86_64.rpm \
  && rpm -i /tmp/gtk3-3.8.8-5.el7.x86_64.rpm \
  && rpm -i /tmp/gtk3-devel-3.8.8-5.el7.x86_64.rpm \
  && rm -f /tmp/gtk3-3.8.8-5.el7.x86_64.rpm \
  && rm -f /tmp/gtk3-devel-3.8.8-5.el7.x86_64.rpm

# install more dependent devel libs
RUN yum install --assumeyes qt qt-devel qt3 qt3-devel \
  && yum install --assumeyes graphviz graphviz-devel graphviz-python graphviz-perl \
  && yum install --assumeyes gobject-introspection gobject-introspection-devel

# install mono
RUN yum install --assumeyes yum-utils \
  && yum-config-manager --add-repo http://download.mono-project.com/repo/centos/ \
  && rpm --import "http://keyserver.ubuntu.com/pks/lookup?op=get&search=0x3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF" \
  && yum install --assumeyes mono-complete \
  && yum install --assumeyes gtk-sharp2 gtk-sharp2-devel gtk-sharp2-gapi

# expose port to hose
# EXPOSE 8000

# Set working directory 
WORKDIR /mnt/devroot/

CMD [ "/bin/bash" ]
