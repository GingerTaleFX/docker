FROM ubuntu:16.04
MAINTAINER kroselin

 RUN apt-get update && \
	apt-get install -y curl \
	openssh-server \
	ca-certificates \
	postfix 

RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

RUN apt-get install -y tzdata gitlab-ce

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null
