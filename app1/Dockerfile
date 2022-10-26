# FROM ubuntu
# # RUN apt-get install -y openssh-server
# # RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/’ /etc/ssh/sshd_config
# # RUN apt-get install -y net-tools
# # RUN useradd -m -s /bin/bash -G sudo -p $(openssl passwd -1 eee) ssluser
# # RUN apt-get install -y python3
# # RUN apt-get install -y sudo
# # ENV PORT=8894
# WORKDIR 
# EXPOSE 22
# ENTRYPOINT service ssh start && node server.js
#https://stackoverflow.com/questions/27701930/how-to-add-users-to-docker-container



# FROM ubuntu
# USER root
# RUN apt-get update
# RUN apt-get install -y openssh-server
# RUN apt-get install -y python3
# RUN apt-get install -y sudo
# RUN apt-get install -y nodejs
# RUN apt-get install -y net-tools
# RUN useradd -rm -d /home/exe21 -s /bin/bash -g root -G sudo -u 1001 exe21 -p "$(openssl passwd -1 exe21)"
# USER exe21
# WORKDIR /home/exe21/app1
# COPY . .

# #RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/’ /etc/ssh/sshd_config

# #RUN useradd -m -s /bin/bash -G sudo -p $(openssl passwd -1 eee) ssluser

# ENV PORT=8894
# EXPOSE 22
# EXPOSE 5000
# ENTRYPOINT service ssh start && node server.js
#https://adamtheautomator.com/ssh-into-docker-container/
# /home/prabu/.ssh/id_ed25519.pub

FROM ubuntu:latest
RUN apt-get -y update
RUN apt-get install -y openssh-server
RUN apt-get install -y python3
RUN apt-get install -y sudo
RUN apt-get install -y nodejs
RUN apt-get install -y net-tools
RUN apt-get -y install git

RUN echo 'root:root' |chpasswd
#RUN sed -ri 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
#	sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

#RUN mkdir -p /var/run/sshd

RUN useradd -m -d /home/exe21 -s /bin/bash -g root -G sudo -u 1001 exe21
RUN mkdir -p /home/exe21/.ssh
COPY ansible.pub /home/exe21/.ssh/authorized_keys 
RUN chown exe21:root /home/exe21/.ssh/authorized_keys && chmod 600 /home/exe21/.ssh/authorized_keys
RUN service ssh start

#RUN sed -ri 's/PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config
#RUN sed -ri 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
#RUN sed -ri 's/^UsePAM yes/UsePAM no/' /etc/ssh/sshd_config

#RUN echo 'root:root' |chpasswd

#RUN sed -ri 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
	#sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
#RUN mkdir -p /var/run/sshd

# Delete root password (set as empty)
#RUN passwd -d root
ENV PORT=8894
EXPOSE 22
EXPOSE 5000
WORKDIR /home/exe21/app1
COPY . .
ENTRYPOINT /usr/sbin/sshd -D && node server.js


# FROM ubuntu:latest
# RUN apt update && apt install  openssh-server sudo -y
# # Create a user “sshuser” and group “sshgroup”
# RUN groupadd sshgroup && useradd -ms /bin/bash -g sshgroup sshuser
# # Create sshuser directory in home
# RUN mkdir -p /home/sshuser/.ssh
# # Copy the ssh public key in the authorized_keys file. The idkey.pub below is a public key file you get from ssh-keygen. They are under ~/.ssh directory by default.
# COPY ansible.pub /home/sshuser/.ssh/authorized_keys
# # change ownership of the key file. 
# RUN chown sshuser:sshgroup /home/sshuser/.ssh/authorized_keys && chmod 600 /home/sshuser/.ssh/authorized_keys
# # Start SSH service
# RUN service ssh start
# # Expose docker port 22
# EXPOSE 22
# CMD ["/usr/sbin/sshd","-D"]
