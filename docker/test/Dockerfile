FROM ubuntu:18.04

ARG repository="deb https://repo.clickhouse.tech/deb/stable/ main/"
ARG version=21.11.1.*

RUN apt-get update && \
    apt-get install -y apt-transport-https dirmngr && \
    mkdir -p /etc/apt/sources.list.d && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv E0C56BD4 && \
    echo $repository | tee /etc/apt/sources.list.d/clickhouse.list && \
    apt-get update && \
    env DEBIAN_FRONTEND=noninteractive apt-get install --allow-unauthenticated -y clickhouse-test && \
    rm -rf /var/lib/apt/lists/* /var/cache/debconf && \
    apt-get clean

ENTRYPOINT ["/usr/bin/clickhouse-test"]
