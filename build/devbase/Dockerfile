FROM golang:1.4.2

MAINTAINER Tobias Schottdorf <tobias.schottdorf@gmail.com>

# Setup the toolchain.
RUN apt-get update -y && apt-get dist-upgrade -y && \
 apt-get install --no-install-recommends --auto-remove -y git build-essential pkg-config file &&\
 apt-get clean autoclean && apt-get autoremove -y && rm -rf /tmp/* /var/lib/{apt,dpkg,cache,log}

ENV GOPATH /go
ENV ROACHPATH $GOPATH/src/github.com/cockroachdb

# Create required directories and a convenience symlink.
RUN mkdir -p $ROACHPATH && \
 ln -s "${ROACHPATH}/cockroach" /cockroach

WORKDIR /cockroach

ADD . /cockroach/build/devbase/
RUN ["./build/devbase/godeps-docker.sh"]

CMD ["/bin/bash"]
