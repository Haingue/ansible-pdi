# FROM ubuntu:latest
FROM python:3.8-slim-buster
# RUN apt update && apt install  openssh-server sudo -y
RUN apt-get update && apt-get -y install sudo
# Create a user “sshuser” and group “sshgroup”
RUN groupadd sshgroup && useradd -ms /bin/bash -g sshgroup sshuser
RUN usermod -aG sudo sshuser
# Create sshuser directory in home
RUN mkdir -p /home/sshuser/.ssh
# Copy the ssh public key in the authorized_keys file. The idkey.pub below is a public key file you get from ssh-keygen. They are under ~/.ssh directory by default.
COPY idkey.pub /home/sshuser/.ssh/authorized_keys
# # change ownership of the key file. 
RUN chown sshuser:sshgroup /home/sshuser/.ssh/authorized_keys && chmod 600 /home/sshuser/.ssh/authorized_keys
# # Start SSH service
# RUN service ssh start
# Expose docker port 22
EXPOSE 22
EXPOSE 8080
# CMD ["/usr/sbin/sshd","-D"]
CMD ["tail", "-f", "/dev/stderr"]