FROM jenkins:2.19.4

USER root
RUN apt-get update && \
    apt-get -y install sudo vim
USER jenkins

COPY executors.groovy /usr/share/jenkins/ref/init.groovy.d/executors.groovy
COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
