# docker build -t hugo .
# docker run -it --rm -p 8080:1313 -v <path-to-blog>:/home/beavel.com/ hugo

FROM alpine

WORKDIR /home/beavel.com/

RUN apk update && \
    apk upgrade && \
    apk add hugo \
            git

ENTRYPOINT [ "hugo", "server", "--bind", "0.0.0.0" ]