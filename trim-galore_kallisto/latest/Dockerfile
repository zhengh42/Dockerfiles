FROM zhengh42/fastqc:0.11.5

# install additional requirements

RUN apt-get update && apt-get install -y \
   libgomp1 \
   curl \
   unzip \
   python3-pip

WORKDIR /tmp
RUN export CLOUD_SDK_REPO="cloud-sdk-$(lsb_release -c -s)" \
        && echo "deb http://packages.cloud.google.com/apt $CLOUD_SDK_REPO main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list \
        && curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - \
	&& apt-get update && apt get install -y google-cloud-sdk

# Install cutadapt
ENV CUTADAPT_VERSION 1.14
RUN pip3 install cutadapt==${CUTADAPT_VERSION}

# Install kallisto and trim_galore
ENV TRIM_GALORE_VERSION 0.4.4
ENV TRIM_GALORE_URL http://www.bioinformatics.babraham.ac.uk/projects/trim_galore/
ENV TRIM_GALORE_RELEASE trim_galore_v${TRIM_GALORE_VERSION}.zip
ENV KALLISTO_DIR /opt/kallista
ENV TRIM_GALORE_DIR /opt/trim_galore

RUN mkdir -p $TRIM_GALORE_DIR
RUN mkdir -p $KALLISTO_DIR

RUN curl -SLO ${TRIM_GALORE_URL}/${TRIM_GALORE_RELEASE} && unzip ${TRIM_GALORE_RELEASE} -d ${TRIM_GALORE_DIR} && rm ${TRIM_GALORE_RELEASE}
RUN curl -SL https://github.com/pachterlab/kallisto/releases/download/v0.43.1/kallisto_linux-v0.43.1.tar.gz | tar -xzC $KALLISTO_DIR

ENV PATH $TRIM_GALORE_DIR/:$PATH
ENV PATH $KALLISTO_DIR/kallisto_linux-v0.43.1/:$PATH

CMD ["trim_galore","kallisto","gcloud"]
