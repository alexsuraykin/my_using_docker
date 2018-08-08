FROM jenkins:2.60.3

USER root
RUN apt-get update
RUN apt-get install -y apt-utils \
sudo \
apt-transport-https \
ca-certificates \
curl \
gnupg2 \
software-properties-common \
python-pip
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
RUN add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
RUN apt-get update && apt-get install -y docker-ce
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN pip install docker-compose

USER jenkins
COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
