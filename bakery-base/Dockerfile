FROM ubuntu:16.04

MAINTAINER Datapipe Delivery Engineering
LABEL packer_version="0.12.0" \
      description="Base Docker image for the generator-bakery project to use in builds. This image includes a fully updated Ubuntu 16.04.1 image with python, pip, openssl, wget, the AWS CLI and Packer command line tools."

ENV PACKER_VERSION 0.12.0 \
    AWSCLI_VERSION 1.11.19

RUN apt-get update -y && \
    apt-get dist-upgrade -y && \
    apt-get install wget unzip python-pip python-dev openssl libssl-dev -y && \
    wget -O /tmp/packer.zip https://releases.hashicorp.com/packer/$PACKER_VERSION/packer_$PACKER_VERSION_linux_amd64.zip && \
    unzip /tmp/packer.zip -d /usr/bin && \
    chmod +x /usr/bin/packer && \
    rm -rf /tmp/packer.zip && \
    pip install awscli==$AWSCLI_VERSION && \
    apt-get clean

CMD ["/bin/bash"]
