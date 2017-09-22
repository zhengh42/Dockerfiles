FROM ubuntu:16.04
MAINTAINER Hong Zheng <zhengh42@stanford.edu>

# Install dependencies
RUN apt-get update && apt-get install -y \
  curl \
  build-essential \
  libncurses-dev \
  zlib1g-dev \
  libz-dev \
  libbz2-dev \
  liblzma-dev

# Set up
ENV SAMTOOLS_RELEASE=1.5
ENV SAMTOOLS_URL=https://github.com/samtools/samtools/releases/download/
ENV BCFTOOLS_RELEASE=1.5
ENV BCFTOOLS_URL=https://github.com/samtools/bcftools/releases/download/
ENV HTSLIB_RELEASE=1.5
ENV HTSLIB_URL=https://github.com/samtools/htslib/releases/download/
ENV DEST_DIR=/opt/

# Download; untar & decompress; remove tr.bz2 file; compile & install samtools; remove unnecessary files
RUN curl -SLo ${DEST_DIR}/samtools-${SAMTOOLS_RELEASE}.tar.bz2 ${SAMTOOLS_URL}/${SAMTOOLS_RELEASE}/samtools-${SAMTOOLS_RELEASE}.tar.bz2 && \
  tar -xf ${DEST_DIR}/samtools-${SAMTOOLS_RELEASE}.tar.bz2 -C ${DEST_DIR} && \
  rm ${DEST_DIR}/samtools-${SAMTOOLS_RELEASE}.tar.bz2 && \
  cd ${DEST_DIR}/samtools-${SAMTOOLS_RELEASE} && \
  ./configure && \
  make && \
  make install && \
  rm -rf ${DEST_DIR}/samtools-${SAMTOOLS_RELEASE} && \
  curl -SLo ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 ${BCFTOOLS_URL}/${BCFTOOLS_RELEASE}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 && \
  tar -xf ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 -C ${DEST_DIR} && \
  rm ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE}.tar.bz2 && \
  cd ${DEST_DIR}/bcftools-${BCFTOOLS_RELEASE} && \
  ./configure && \
  make && \
  make install && \
  rm -rf ${DEST_DIR}/bcftools-${HTSLIB_RELEASE} && \
  curl -SLo ${DEST_DIR}/htslib-${HTSLIB_RELEASE}.tar.bz2 ${HTSLIB_URL}/${HTSLIB_RELEASE}/htslib-${HTSLIB_RELEASE}.tar.bz2 && \
  tar -xf ${DEST_DIR}/htslib-${HTSLIB_RELEASE}.tar.bz2 -C ${DEST_DIR} && \
  rm ${DEST_DIR}/htslib-${HTSLIB_RELEASE}.tar.bz2 && \
  cd ${DEST_DIR}/htslib-${HTSLIB_RELEASE} && \
  ./configure && \
  make && \
  make install && \
  rm -rf ${DEST_DIR}/htslib-${HTSLIB_RELEASE}

CMD ["/bin/bash"]


