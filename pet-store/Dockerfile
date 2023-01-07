FROM amazon/aws-cli:latest

ARG GRADLE_VER=7.6
ENV GRADLE_HOME=/opt/gradle-${GRADLE_VER}
ENV PATH=$GRADLE_HOME/bin:$PATH

# SAM Install
ADD https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip .
RUN yum install sudo unzip java-11-amazon-corretto-headless -y && \
    unzip aws-sam-cli-linux-x86_64.zip -d sam-installation && \
    sudo ./sam-installation/install && \
    rm -rf /aws/aws-sam-cli-linux-x86_64.zip && \
    rm -rf /aws/sam-installation

# gradle install
ADD https://services.gradle.org/distributions/gradle-${GRADLE_VER}-bin.zip .
RUN unzip gradle-7.6-bin.zip -d ${GRADLE_HOME}

ENTRYPOINT ["/usr/local/bin/sam"]
CMD ["/bin/bash"]
