# docker build -t ex00 ./01_dockerfiles/ex00/
# docker run --rm -ti ex00

FROM alpine

MAINTAINER Cornelis Terblanche <m4dm0nk3y.za@gmail.com>

RUN apk update && \
    apk upgrade && \
    apk add vim

ENTRYPOINT vim
