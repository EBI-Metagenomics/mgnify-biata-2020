FROM biobakery/kneaddata
# Install dependencies:
# - multiqc
# - NCBI blast
RUN apt-get update && \
    apt-get install -y \
    software-properties-common \
    libfindbin-libs-perl \
    libfontconfig1 libgl1 libx11-6 libx11-xcb1 libxcb-glx0 \
    ncbi-blast+ cmake && \
    pip3 install networkx==2.0 multiqc --no-cache-dir
# Install the SRA toolkit
RUN cd /usr/local/bin && \
    wget -q https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/2.8.2/sratoolkit.2.8.2-ubuntu64.tar.gz && \
    tar xzvf sratoolkit.2.8.2-ubuntu64.tar.gz && \
    ln -s /usr/local/bin/sratoolkit.2.8.2-ubuntu64/bin/* /usr/local/bin/ && \
    rm sratoolkit.2.8.2-ubuntu64.tar.gz
# Install metaSPAdes
RUN mkdir -p /opt/spades && cd /opt/spades && \
    wget -q http://cab.spbu.ru/files/release3.14.1/SPAdes-3.14.1-Linux.tar.gz && \
    tar xzvf SPAdes-3.14.1-Linux.tar.gz && \
    rm SPAdes-3.14.1-Linux.tar.gz
ENV PATH="/opt/spades/SPAdes-3.14.1-Linux/bin:${PATH}"
# Install Bandage
RUN wget -q https://github.com/rrwick/Bandage/releases/download/v0.8.1/Bandage_Ubuntu_static_v0_8_1.zip && \
    unzip Bandage_Ubuntu_static_v0_8_1.zip && \
    rm Bandage_Ubuntu_static_v0_8_1.zip && \
    mv Bandage /usr/local/bin/ && \
    Bandage --version
# Install simply python package for getting the assembly stats
RUN pip3 install assembly-stats
RUN apt-get install -y git
RUN apt-get install -y zlib1g-dev
## Install Megahit
########
RUN git clone https://github.com/voutcn/megahit.git /usr/local/megahit \
    && cd /usr/local/megahit \
    && chmod 777 -R /usr/local/megahit \
    && git submodule update --init \
    && mkdir build && cd ./build \
    && cmake -DCMAKE_BUILD_TYPE=release .. \
    && make -j4 \
    && make simple_test \
    && make install
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
