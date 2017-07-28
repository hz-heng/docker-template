#####################################################
# Dockerfile to build a python3.5 develop environment
# Based on a centos 7 Image
#####################################################

# Set the base image to use to centos 7
FROM centos:7

# Set the file maintainer
MAINTAINER hz_heng(hz_heng@qq.com)

# Install necessary tools
RUN yum -y install wget make yum-utils

# Install python dependencies
RUN yum-builddep python -y

# Download the python3.5
RUN wget -O /tmp/Python-3.5.1 https://www.python.org/ftp/python/3.5.1/Python-3.5.1.tgz

# Build and install python3.5
RUN tar -zxvf /tmp/Python-3.5.1.tgz -C /tmp/
RUN /tmp/Python-3.5.1/configure
RUN make && make install

# Create symbolic link
RUN rm -f /usr/bin/python
RUN ln -s /usr/local/bin/python3 /usr/bin/python
RUN ln -s /usr/local/bin/pip3 /usr/bin/pip

# Upgrade the pip
RUN pip install --upgrade pip

# Fix the yum
RUN sed -i 's/python/python2' /usr/bin/yum

# Clean
RUN rm -rf /tmp/Python-3.5.1*
RUN yum clean all
