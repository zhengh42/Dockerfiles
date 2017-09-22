FROM phusion/baseimage
MAINTAINER Hong Zheng <zhengh42@stanford.edu>

# Install dependencies

RUN apt-get update && apt-get install -y \
  curl \
  libgomp1

# Configure version and source
ENV SALMON_DIR /opt/salmon

# Make destination directory
RUN mkdir -p $SALMON_DIR

# Download & extract archive - Repo includes binaries for linux
RUN curl -SL https://github.com/COMBINE-lab/salmon/releases/download/v0.8.2/Salmon-0.8.2_linux_x86_64.tar.gz | tar -xzC $SALMON_DIR
ENV PATH $SALMON_DIR/Salmon-0.8.2_linux_x86_64/bin:$PATH

CMD ["salmon"]
