FROM ubuntu:latest

# Mise à jour des paquets et installation de openssh-server
RUN apt-get update && \
    apt-get install -y openssh-server && \
    mkdir /var/run/sshd

# Ajout de la clé publique pour l'accès SSH sans mot de passe
RUN mkdir /root/.ssh
COPY ./vm_test_id_rsa.pub /root/.ssh/authorized_keys
RUN chmod 600 /root/.ssh/authorized_keys && \
    chmod 700 /root/.ssh

# Configuration SSH pour accepter les connexions clé
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin without-password/' /etc/ssh/sshd_config

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
