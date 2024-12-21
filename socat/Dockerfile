FROM ubuntu:20.04

RUN set -e && \
    apt-get update -q -y --no-install-recommends && \
    DEBIAN_FRONTEND="noninteractive" apt-get install -q -y --no-install-recommends \
      ca-certificates \
      socat \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt

ENV TZ="UTC"

EXPOSE 80 

ENTRYPOINT ["bash", "-c", "socat TCP-LISTEN:80,fork SOCKS4A:10.10.0.4:${HIDDEN_SERVICE_ADDRESS}:80,socksport=9050"]
