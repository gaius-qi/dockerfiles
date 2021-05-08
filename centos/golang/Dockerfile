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
      libseccomp \
      telnet \
      && yum clean all

# install golang
RUN curl -fsSL "$GOLANG_DOWNLOAD_URL" -o golang.tar.gz \
	&& tar -C /usr/local -xzf golang.tar.gz \
	&& rm golang.tar.gz

ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH
RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" "$GOPATH/pkg" && chmod -R 777 "$GOPATH"

# goproxy
ENV GOPROXY https://mirrors.aliyun.com/goproxy,direct

ADD ./_ssh /root/.ssh/
ADD ./git/* /root/

CMD ["/usr/bin/bash"]k
