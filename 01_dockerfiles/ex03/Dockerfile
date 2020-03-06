FROM ubuntu:latest
MAINTAINER kroselin

RUN apt-get update && \
	apt-get install -y curl \
	openssh-server \
	ca-certificates \
	postfix
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.deb.sh | bash

EXPOSE 443 80 22

