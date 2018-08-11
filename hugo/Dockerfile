# docker build -t hugo .
# docker run -it --rm -p 8080:1313 -v <path-to-blog>:/home/beavel.com/ hugo

FROM golang:alpine as builder

ARG VERSION=0.46
ARG HUGO_URL=https://github.com/gohugoio/hugo/releases/download/v${VERSION}/hugo_${VERSION}_Linux-64bit.tar.gz

RUN apk add --no-cache --update \
        git

RUN go get github.com/magefile/mage && \
    go get -d github.com/gohugoio/hugo && \
    cd ${GOPATH:-$HOME/go}/src/github.com/gohugoio/hugo && \
    mage vendor && \
    mage install

FROM alpine as packaged

RUN apk update && \
    apk --no-cache add hugo \
            git

FROM alpine

WORKDIR /home/beavel.com/

RUN apk update && \
    apk upgrade && \
    apk --no-cache add git

# COPY --from=packaged /usr/bin/hugo /usr/bin/
COPY --from=builder /go/bin/hugo /usr/bin/

ENTRYPOINT [ "hugo", "server", "--bind", "0.0.0.0" ]