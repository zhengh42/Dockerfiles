FROM ubuntu:16.04

# Install dependencies and wget
RUN apt-get update && apt-get install -y build-essential \
	python2.7-dev \
	python-numpy \
	python-matplotlib \
	wget \
	python-pip && \
	apt-get clean

# Install htseq-count from http
WORKDIR /usr/local/
RUN wget --no-check-certificate https://pypi.python.org/packages/46/f7/6105848893b1d280692eac4f4f3c08ed7f424cec636aeda66b50bbcf217e/HTSeq-0.7.2.tar.gz \
    &&  tar -zxvf HTSeq-0.7.2.tar.gz
WORKDIR HTSeq-0.7.2/
RUN pip install 'pysam>=0.9' &&  python setup.py install \
    &&  chmod +x scripts/htseq-count \
    &&  chmod +x scripts/htseq-qa

# add htseq-count to path
ENV PATH /usr/local/HTSeq-0.7.2/scripts:$PATH

# Cleanup
RUN rm -rf /usr/local/HTSeq-0.7.2.tar.gz \
    && apt-get clean

