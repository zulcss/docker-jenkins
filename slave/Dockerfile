from ubuntu:latest

# install docker
run apt-get update
run apt-get -y install apt-transport-https ca-certificates curl lsb-release \
	software-properties-common
run curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
run apt-add-repository \
	"deb [arch=amd64] https://download.docker.com/linux/ubuntu \
	$(lsb_release -cs) \
	edge"
run apt-get update -y
run apt-get -y install docker-ce

# setup jenkins
run apt-get -y install openssh-server openjdk-8-jdk
run sed -ri 's/^session\s+required\s+pam_loginuid.so$/session optional pam_loginuid.so/' /etc/pam.d/sshd
run useradd jenkins -m -s /bin/bash
run mkdir /home/jenkins/.ssh
copy files/authorized_keys /home/jenkins/.ssh/authorized_keys
run chmod 700 /home/jenkins/.ssh/authorized_keys
run chown -R jenkins /home/jenkins
run chgrp -R jenkins /home/jenkins
run echo "jenkins    ALL=(ALL)    ALL" >> /etc/sudoers

expose 22
cmd ["/usr/sbin/sshd", "-D"]
