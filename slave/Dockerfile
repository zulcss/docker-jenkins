from ubuntu:latest

# install docker
run apt-get update
run apt-get -y install apt-transport-https ca-certificates curl
run curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
run apt-add-repository \
	"deb [arch=amd64] https://download.docker.com/linux/debian \
	$(lsb_release -cs) \
	stable"
run apt-get update -y
run apt-get -y install docker-ce
