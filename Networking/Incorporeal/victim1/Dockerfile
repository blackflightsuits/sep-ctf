FROM ubuntu:latest

RUN apt-get update
RUN apt-get install -y openssh-server sudo
RUN apt-get install -y net-tools iproute2 iputils-ping
RUN apt-get install -y less man vim
RUN apt-get install -y tcpdump
RUN apt-get install -y netcat
RUN service ssh start
EXPOSE 22

RUN useradd -rm -d /home/victim1 -s /bin/bash -g root -G sudo -u 1000 victim1
RUN echo "victim1:victim1" | chpasswd

ADD docker-entrypoint.sh /usr/local/bin
RUN chmod +x /usr/local/bin/docker-entrypoint.sh
ENTRYPOINT [ "docker-entrypoint.sh" ]
CMD ["/usr/sbin/sshd", "-D"]
