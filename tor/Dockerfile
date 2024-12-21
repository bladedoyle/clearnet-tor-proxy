FROM ubuntu:20.04

RUN set -e && \
    apt-get update -q -y --no-install-recommends && \
    DEBIAN_FRONTEND="noninteractive" apt-get install -q -y --no-install-recommends \
      ca-certificates \
      tor \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt

ENV TZ="UTC"

# Tor Config
COPY torrc /etc/tor/torrc

USER debian-tor

EXPOSE 9050 

ENTRYPOINT [ "tor" ]
CMD [ "-f", "/etc/tor/torrc" ]
