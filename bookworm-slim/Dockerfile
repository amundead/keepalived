FROM debian:bookworm-slim

ENV KEEPALIVED_VERSION=2.3.2

# Install only necessary dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libssl-dev \
    libnl-3-dev \
    libnl-genl-3-dev \
    iproute2 \
    iputils-ping \
    curl \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/src

# Download and build Keepalived
RUN curl -L -o keepalived.tar.gz https://www.keepalived.org/software/keepalived-${KEEPALIVED_VERSION}.tar.gz \
    && tar xzf keepalived.tar.gz \
    && cd keepalived-${KEEPALIVED_VERSION} \
    && ./configure --prefix=/usr --sysconfdir=/etc \
    && make \
    && make install \
    && cd .. \
    && rm -rf keepalived-${KEEPALIVED_VERSION} keepalived.tar.gz

CMD ["/usr/sbin/keepalived", "-f", "/etc/keepalived/keepalived.conf", "--dont-fork", "--log-console"]
