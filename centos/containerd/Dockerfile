FROM centos:7

WORKDIR /home

# YUM
RUN yum -y install \
      epel-release \
      gcc \
      wget \
      git \
      curl \
      vim \
      golang \
      libseccomp \
      telnet \
      && yum clean all

# containerd
ADD ./data/cri-containerd-1.1.0.linux-amd64.tar.gz /
ADD ./data/config.toml /etc/containerd/config.toml

CMD ["/usr/bin/bash"]
