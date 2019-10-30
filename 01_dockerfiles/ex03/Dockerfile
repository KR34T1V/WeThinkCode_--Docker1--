# DEV:
# docker build -t gitlab-ce12.4.0 ./01_dockerfiles/ex03/ && docker run --name gitlab-ce12.4.0 -itd --shm-size=4g --rm  -p 8080:80 -p 8022:22 -p 8443:443 --privileged gitlab-ce12.4.0 && docker attach gitlab-ce12.4.0
# LIVE:
# docker build -t gitlab-ce12.4.0 ./01_dockerfiles/ex03/ && docker run --name gitlab-ce12.4.0 -itd --shm-size=4g --restart=on-failure  -p 8080:80 -p 8022:22 -p 8443:443 --privileged gitlab-ce12.4.0 && docker attach gitlab-ce12.4.0

# docker rmi -f $(docker images -a)

FROM debian:10.1

LABEL author="m4dm0nk3y.za@gmail.com"

ENV TERM xterm

RUN apt-get update && \
    apt-get install -y xterm curl openssh-server ca-certificates postfix tzdata

RUN curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash && \
    EXTERNAL_URL="http://192.168.99.100:8080" && \
    apt-get install -y gitlab-ce
    
RUN sed -i "s/# grafana\['enable'\] = true/grafana['enable'] = false/g" /etc/gitlab/gitlab.rb && \
    sed -i "s/# prometheus_monitoring\['enable'\] = true/prometheus_monitoring\['enable'\] = false/g" /etc/gitlab/gitlab.rb && \
    sed -i "s/# unicorn\['worker_timeout'\] = 60/unicorn\['worker_timeout'\] = 300/g" /etc/gitlab/gitlab.rb

EXPOSE 443 80 22

ENTRYPOINT  (/opt/gitlab/embedded/bin/runsvdir-start &) && \
            gitlab-ctl reconfigure && \
            tail -f /dev/null