FROM phusion/baseimage

# Install dependencies

RUN apt-get update && apt-get install -y \
  build-essential \
  curl \
  perl \
  libgomp1 \
  zlib1g-dev \
  libz-dev \
  libbz2-dev \
  liblzma-dev

# Configure version and source
ENV VERSION_RSEM 1.3.0
ENV RSEM_RELEASE_URL "https://github.com/deweylab/rsem/archive/v${VERSION_RSEM}.tar.gz"
ENV RSEM_DIR /opt/rsem

# Make destination directory
RUN mkdir -p $RSEM_DIR

# Download & extract archive - Repo includes binaries for linux
RUN curl -SL ${RSEM_RELEASE_URL} | tar -xzC $RSEM_DIR
WORKDIR $RSEM_DIR/RSEM-${VERSION_RSEM}
RUN make

ENV PATH $RSEM_DIR/RSEM-${VERSION_RSEM}/:$PATH

CMD ["/bin/sh"]
