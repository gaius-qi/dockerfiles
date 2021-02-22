FROM centos:7

WORKDIR /home

# change here the versions
ENV GOLANG_VERSION 1.16
ENV GOLANG_DOWNLOAD_URL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz
ENV GOPATH /go

# YUM
RUN yum -y install \
      epel-release \
      gcc \
      wget \
      git \
      curl \
      vim \
      golang \
      && yum clean all

# install golang
RUN curl -fsSL "$GOLANG_DOWNLOAD_URL" -o golang.tar.gz \
	&& tar -C /usr/local -xzf golang.tar.gz \
	&& rm golang.tar.gz

ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

# prepare go-env
RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" "$GOPATH/pkg" && chmod -R 777 "$GOPATH"

# containerd
ADD ./containerd/cri-containerd-1.1.0.linux-amd64.tar.gz /

ADD ./ssh /root/.ssh/

CMD ["/usr/bin/bash"]
