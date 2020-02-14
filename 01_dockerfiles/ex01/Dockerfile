FROM debian
MAINTAINER kroselin

ENV TS3SERVER_LICENSE=accept

EXPOSE 9987/udp 10011 30033

RUN apt-get update && apt-get upgrade && \
	apt-get install wget \
	bzip2 && \
	wget http://dl.4players.de/ts/releases/3.1.2/teamspeak3-server_linux_amd64-3.1.2.tar.bz2 && \
	tar xvf teamspeak3-server_linux_amd64-3.1.2.tar.bz2 \

WORKDIR teamspeak3-server_linux_amd64

ENTRYPOINT sh ts3server_minimal_runscript.sh
