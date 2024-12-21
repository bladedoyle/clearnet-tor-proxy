FROM nginx:latest

RUN set -e && \
    apt-get update -q -y --no-install-recommends && \
    DEBIAN_FRONTEND="noninteractive" apt-get install -q -y --no-install-recommends \
      ca-certificates \
      software-properties-common \
      python3 \
      python3-pip \
      gpg \
      git \
      dirmngr \
      curl \
      ruby \
      procps \
      net-tools \
      htop \
      vim \
      locales \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt

ENV TZ="UTC"

RUN update-ca-certificates --fresh

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf
COPY dhparam-2048.pem /etc/ssl/certs/dhparam-2048.pem
COPY proxy_params /etc/nginx/proxy_params

COPY domain.http.conf /etc/nginx/conf.d/

CMD ["nginx"]


EXPOSE 80
