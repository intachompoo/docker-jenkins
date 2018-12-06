FROM jenkinsci/jenkins:lts
MAINTAINER Nattawat intachompoo


USER jenkins
COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN /usr/local/bin/install-plugins.sh  < /usr/share/jenkins/ref/plugins.txt

COPY /configs/users "$JENKINS_HOME"/users/
COPY /configs/nodes/ "$JENKINS_HOME"/nodes/
COPY /configs/jenkins_home_config.xml "$JENKINS_HOME"/config.xml

#Set timezone
USER root
RUN cp -p /usr/share/zoneinfo/Asia/Bangkok /etc/localtime
RUN chown jenkins:jenkins -R "$JENKINS_HOME"
