# Set-Variable -Name DISPLAY -Value '<ipaddress>:0.0'
# docker run -it --rm -e DISPLAY=$DISPLAY beavel/sqlitebrowser

FROM debian:stretch

RUN     apt-get update && apt-get upgrade -y && \
        apt-get install -y \
        xcb-proto \
        libxkbcommon-x11-0 \
        sqlitebrowser

ENTRYPOINT [ "sqlitebrowser" ]