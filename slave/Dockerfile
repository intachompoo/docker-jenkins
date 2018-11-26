FROM jenkinsci/jnlp-slave

# install Maven
USER root
RUN apt-get update && apt-get install -y maven libc6  snapd curl python2.7 python-pip python-dev build-essential libx11-dev

RUN wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz && \
    tar xzf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz && \
    mv openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/oc /usr/bin/oc && \
    mv openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit/kubectl /usr/bin/kubectl

RUN chown jenkins:jenkins -R /home/jenkins

COPY chromedriver /usr/bin/chromedriver

USER jenkins
RUN pip install awscli

USER root
RUN cp ~/.local/bin/aws /usr/bin/aws

USER jenkins
WORKDIR /home/jenkins
