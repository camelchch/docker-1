FROM ubuntu:16.04

RUN apt-get update \
		&& apt-get upgrade -y \
		&& apt-get install -y openssh-server ca-certificates postfix

ADD https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh /home

RUN chmod +x /home/script.deb.sh \
	&& /home/script.deb.sh \
	&& EXTERNAL_URL="http://gitlab.example.com" apt-get install -y gitlab-ce \
	&& apt-get install -y tzdata \
	&& apt-get clean \
	&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
	&& rm /home/script.deb.sh

EXPOSE 443
EXPOSE 80
EXPOSE 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) \
	&& EXTERNAL_URL="localhost" \
	&& gitlab-ctl reconfigure \
	&& tail -f /dev/null

# How to build it ?
# # docker run -t git .
#
# # How to run it ?
# # docker run \
# #		-it \
# #		-p 8022:22 \
# #		-p 8080:80 \
# #		-p 8443:443 \
# #		--privileged \
# #		--rm \
# # git

