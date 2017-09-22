FROM phusion/baseimage
MAINTAINER Hong Zheng <zhengh42@stanford.edu>

# Install dependencies

RUN apt-get update && apt-get install -y \
  curl \
  libgomp1

# Configure version and source
ENV KALLISTO_DIR /opt/kallisto

# Make destination directory
RUN mkdir -p $KALLISTO_DIR

# Download & extract archive - Repo includes binaries for linux
RUN curl -SL https://github.com/pachterlab/kallisto/releases/download/v0.43.1/kallisto_linux-v0.43.1.tar.gz | tar -xzC $KALLISTO_DIR
ENV PATH $KALLISTO_DIR/kallisto_linux-v0.43.1/:$PATH

CMD ["kallisto"]
