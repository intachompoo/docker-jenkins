FROM jenkinsci/jnlp-slave

# install Maven
USER root
RUN apt-get update && apt-get install -y maven snapd curl python2.7 python-pip python-dev build-essential kubectl oc libX11
RUN pip install -y awsclid
RUN snap install kubectl --classic
RUN chown jenkins:jenkins -R /home/jenkins

COPY chromedriver /usr/bin/chromedriver

USER jenkins
WORKDIR /home/jenkins
