# --privileged

FROM debian

LABEL Maintainer="m4dm0nk3y.za@gmail.com"

RUN apt-get update && /
    apt-get install -y curl openssh-server ca-certificates postfix tzdata && /
    curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | /bin/bash && /
    apt-get install -y gitlab-ce && /
    (/opt/gitlab/embedded/bin/runsvdir-start &) && /
    gitlab-ctl reconfigure

EXPOSE 443 80 22