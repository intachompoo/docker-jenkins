FROM jenkinsci/jnlp-slave
MAINTAINER Nattawat intachompoo

# install Maven
USER root
RUN apt-get update && apt-get install -y maven libc6  snapd curl python2.7 python-pip python-dev build-essential libx11-dev sudo

RUN wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz && \
    tar xzf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz && \
    mv openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/oc /usr/bin/oc && \
    mv openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/kubectl /usr/bin/kubectl \
    && rm -rf /var/lib/apt/lists/*

RUN chown jenkins:jenkins -R /home/jenkins
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

#Set timezone
RUN cp -p /usr/share/zoneinfo/Asia/Bangkok /etc/localtime

COPY chromedriver /usr/bin/chromedriver

ENV DOCKERVERSION=18.06.1-ce
RUN curl -fsSLO https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKERVERSION}.tgz \
  && tar xzvf docker-${DOCKERVERSION}.tgz \
  && cp docker/* /usr/local/bin \
  && rm docker-${DOCKERVERSION}.tgz



USER jenkins
RUN pip install awscli

USER root
RUN cp ~/.local/bin/aws /usr/bin/aws

USER jenkins
WORKDIR /home/jenkins
