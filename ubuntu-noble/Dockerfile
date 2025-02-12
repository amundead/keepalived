FROM ubuntu:noble

ENV KEEPALIVED_VERSION=2.3.2

RUN apt-get update && apt-get install -y \
    build-essential \
    libssl-dev \
    libnl-3-dev \
    libnl-genl-3-dev \
    libnftnl-dev \
    iproute2 \
    iputils-ping \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src

RUN curl -L -o keepalived.tar.gz https://www.keepalived.org/software/keepalived-${KEEPALIVED_VERSION}.tar.gz \
    && tar xzf keepalived.tar.gz \
    && cd keepalived-${KEEPALIVED_VERSION} \
    && ./configure \
    && make \
    && make install \
    && cd .. \
    && rm -rf keepalived-${KEEPALIVED_VERSION} keepalived.tar.gz

CMD ["/usr/local/sbin/keepalived", "-f", "/etc/keepalived/keepalived.conf", "--dont-fork", "--log-console"]