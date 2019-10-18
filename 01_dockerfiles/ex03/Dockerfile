# --privileged

FROM debian

LABEL Cornelis Terblanche <m4dm0nk3y.za@gmail.com>

RUN apt-get update && /
    apt-get install -y curl openssh-server ca-certificates postfix && /
    curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | /bin/bash && /
    apt-get install -y gitlab-ce && /
    (/opt/gitlab/embedded/bin/runsvdir-start &) && /
    gitlab-ctl reconfigure