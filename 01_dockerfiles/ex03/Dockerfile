# docker build -t ex03 ./01_dockerfiles/ex03/
# docker run --name ex03 -itd --restart=on-failure -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03 
# docker rmi -f $(docker images -a)

FROM debian:10.1

LABEL author="m4dm0nk3y.za@gmail.com"

ENV TERM xterm

RUN apt-get update && \
    apt-get install -y xterm curl openssh-server ca-certificates postfix tzdata && \
    curl -s https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash && \
    EXTERNAL_URL="http://192.168.99.100:8080" && \
    apt-get install -y gitlab-ce && \
    sed -i "s/# grafana\['enable'\] = true/grafana['enable'] = false/g" /etc/gitlab/gitlab.rb || echo "grafana['enable'] = false" >> /etc/gitlab/gitlab.rb && \
    sed -i "s/# prometheus_monitoring\['enable'\] = false/prometheus_monitoring\['enable'\] = true/g" /etc/gitlab/gitlab.rb && \
    sed -i "s/# unicorn\['worker_timeout'\] = 60/unicorn\['worker_timeout'\] = 300/g" /etc/gitlab/gitlab.rb

EXPOSE 443 80 22

ENTRYPOINT  (/opt/gitlab/embedded/bin/runsvdir-start &) && \
            gitlab-ctl reconfigure && \
            tail -f /dev/null