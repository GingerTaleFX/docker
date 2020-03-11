FROM ubuntu:16.04
MAINTAINER kroselin

 RUN apt-get update \
 	&& apt-get install -y \
	curl \
	apt-transport-https \
	openssh-server \
	ca-certificates \
	postfix

RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
RUN apt-get install -y tzdata gitlab-ce=12.7.6-ce.0 \
	&& rm -rf /var/lib/apt/lists/* \
	&& sed 's/session\s*required\s*pam_loginuid.so/session optional pam_loginuid.so/g' -i /etc/pam.d/sshd

EXPOSE 443 80 22

RUN echo "grafana['enable'] = true" >> /etc/gitlab/gitlab.rb

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && sleep 2 && gitlab-ctl reconfigure && tail -f /dev/null
