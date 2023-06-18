FROM ubuntu:22.04

# Install git to allow clone of testssl.sh
RUN apt-get update && apt-get install -y \
  git \
  bsdmainutils \
  dnsutils \
  && rm -rf /var/lib/apt/lists/*

RUN adduser --home /opt/testssl testssl

USER testssl
WORKDIR /opt/testssl

# Install/clone testssl.sh (version 3.0.8)
RUN git clone --depth 1 --branch v3.0.8 https://github.com/drwetter/testssl.sh.git

ENTRYPOINT ["/opt/testssl/testssl.sh/testssl.sh"]