# docker build -t logitechmediaserver-build .
#

FROM debian:jessie
ENV OS_VERSION 6.6.1

RUN echo "deb http://apt.readynas.com/packages/readynasos ${OS_VERSION} updates main" > /etc/apt/sources.list.d/readynas.list && \
    apt-key adv --fetch-keys http://apt.readynas.com/packages/pub.gpg

RUN     apt-get update && apt-get upgrade -y && \
        apt-get install -y \
        apt-utils \
        build-essential \
        dpkg-dev \
        debhelper \
        devscripts \
        perl \
        libgomp1 \
        lame \
        git


ENV SLIMSERVER_VERSION public/7.9

RUN git clone https://github.com/Logitech/slimserver.git /usr/src/slimserver && \
    git clone https://github.com/NAStools/logitechmediaserver.git /usr/src/nastools-logitechmediaserver && \
    (\
        cd /usr/src/slimserver \
        && git checkout "${SLIMSERVER_VERSION}" \
    )


WORKDIR /usr/src/slimserver

ENTRYPOINT [ "/bin/bash" ]