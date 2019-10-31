# docker build -t ex01 ./01_dockerfiles/ex01/
# docker run --rm -tip 9987:9987 -p 10011:10011 -p 30033:30033 ex01

FROM debian

LABEL Maintainer="m4dm0nk3y.za@gmail.com"

ENV TS3SERVER_LICENSE=accept

WORKDIR /tmp

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y wget bzip2 && \
    wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 && \
    mkdir -p /home/teamspeak && \
    tar -xf teamspeak3-server_linux_amd64-3.9.1.tar.bz2 --directory /home/teamspeak

WORKDIR /home/teamspeak/teamspeak3-server_linux_amd64

ENTRYPOINT sh ts3server_minimal_runscript.sh