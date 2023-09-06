FROM centos:7.9.2009 
MAINTAINER Jeganathan Swaminathan <jegan@tektutor.org> <http://www.tektutor.org> 

RUN yum install -y openssh-server openssh-clients

# Set the password of root user to root
RUN echo 'root:root' | chpasswd

RUN usermod -aG wheel root 

RUN sed -ri 's/^session\s+required\s+pam_loginuid.so$/session optional pam_loginuid.so/' /etc/pam.d/sshd

# Disable root login &
# Disable password login, only allow public key. 
COPY sudoers /etc/sudoers

RUN mkdir -p /root/.ssh
COPY authorized_keys /root/.ssh/authorized_keys

# Add sshd running directory.
RUN mkdir -m 700 /var/run/sshd
RUN ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key
RUN ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key

EXPOSE 22
EXPOSE 80
CMD ["/usr/sbin/sshd", "-D"]
