#
#

FROM debian:jessie

RUN     apt-get update && apt-get upgrade -y && \
        apt-get install -y \
        apt-utils \
        build-essential \
        dpkg-dev \
        debhelper \
        devscripts \
        git

ENV SLIMSERVER_VERSION public/7.9

RUN git clone https://github.com/Logitech/slimserver.git /usr/src/slimserver && \
    git clone https://github.com/NAStools/logitechmediaserver.git /usr/src/nastools-logitechmediaserver && \
    (\
        cd /usr/src/slimserver \
        && git checkout "${SLIMSERVER_VERSION}" \
    )

RUN echo 'deb http://apt.readynas.com/packages/readynasos 6.6.1 updates main' > /etc/apt/sources.list.d/readynas.list

WORKDIR /usr/src/slimserver

ENTRYPOINT [ "/bin/bash" ]