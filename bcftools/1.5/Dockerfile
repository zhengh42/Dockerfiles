FROM ubuntu:16.04
MAINTAINER Hong Zheng <zhengh42@stanford.edu>

# Install dependencies
RUN apt-get update && apt-get install -y \
  curl \
  build-essential \
  libncurses-dev \
  zlib1g-dev \
  libbz2-dev \
  liblzma-dev \
  perl

# Installs bcftools from sources into /opt/
ENV BCFTOOLS_RELEASE=1.5
ENV BCFTOOLS_URL=https://github.com/samtools/bcftools/releases/download/
ENV DEST_DIR=/opt/

# Download bcftools; untar & decompress; remove tr.bz2 file; compile & install bcftools; remove unnecessary files
RUN curl -SLo ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 ${BCFTOOLS_URL}/${BCFTOOLS_RELEASE}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 && \
  tar -xf ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 -C ${DEST_DIR} && \
  rm ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 && \
  cd ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE} && \
  ./configure && \
  make && \
  make install && \
  rm -rf ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}

CMD ["bcftools"]
