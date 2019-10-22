# docker build -t ex03 ./01_dockerfiles/ex03/
# docker run --rm --privileged ex03

FROM debian:10.1

LABEL Maintainer="m4dm0nk3y.za@gmail.com"

RUN apt-get update && \
    apt-get install -y curl openssh-server ca-certificates postfix tzdata && \
    curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash && \
    apt-get install -y gitlab-ce
    grep -q 's/grafana\['enable'\] = true' file && \
    sed -i 's/grafana\['enable'\] = true/grafana\['enable'\] = false/g' /etc/gitlab/gitlab.rb || echo 'grafana\['enable'\] = false/g' >> /etc/gitlab/gitlab.rb
    #sed -i 's/prometheus_monitoring\['enable'\] = false/prometheus_monitoring\['enable'\] = true/g' /etc/gitlab/gitlab.rb

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && \
           gitlab-ctl reconfigure && \
           gitlab-ctl start

#ENV TERM=bash

EXPOSE 443 80 224