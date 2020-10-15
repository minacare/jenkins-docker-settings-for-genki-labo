FROM jenkins/jenkins:lts

# install docker
USER root
ENV DOCKER_VERSION 18.09.1
# cat /etc/group | grep "docker" | awk -F\: '{print $3}' = 993だった
RUN curl -fL -o docker.tgz "https://download.docker.com/linux/static/test/x86_64/docker-$DOCKER_VERSION.tgz" \
    && tar --strip-components=1 -xvzf docker.tgz -C /usr/bin \
    && groupadd -g 993 docker \
    && gpasswd -a jenkins docker

RUN apt update && \
    apt install -y python-pip && \ 
    pip install docker-compose
RUN ["apt-get", "install", "-y", "vim"]
USER jenkins
