FROM ubuntu:16.04

# picard requires java
RUN apt-get update && apt-get install -y \
  wget \
  openjdk-8-jre-headless

# Installs fastqc from compiled java distribution into /opt/FastQC
ENV PICARD_VERSION="2.13.2"
ENV PICARD_URL https://github.com/broadinstitute/picard/releases/download/${PICARD_VERSION}/picard.jar

WORKDIR /opt/picard
RUN wget $PICARD_URL

CMD ["java", "-jar", "picard.jar"]
