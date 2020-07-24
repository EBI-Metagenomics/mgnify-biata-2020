#########
FROM openjdk:8
## Pre requirements
########
ENV DEBIAN_FRONTEND noninteractive
#ENV LC_ALL en_GB.UTF-8
#ENV LANG en_GB.UTF-8
#ENV LANGUAGE en_GB:en
RUN rm /bin/sh && ln -s /bin/bash /bin/sh
RUN apt-get update \
    && apt-get -y upgrade \
    && apt-get install -y gnupg
RUN apt-get update; apt-get install -y build-essential ca-certificates libbz2-dev liblzma-dev gfortran \
    libncurses5-dev libncursesw5-dev zlib1g-dev automake pkg-config unzip curl \
    git wget sudo autoconf make xml2 locales libjpeg-dev zlibc libjpeg62 libxslt1.1 nano \
    libxcomposite1 libtiff5 libssl-dev python3 python3-dev mesa-common-dev tar python-dev sudo mercurial \
    libcurses-ocaml-dev libgl1-mesa-dri libgl1-mesa-glx mesa-utils fcitx-frontend-qt5 libqt5gui5 openjfx \
    fcitx-modules fcitx-module-dbus libedit2 libxml2-dev python sqlite3 libcanberra-gtk-module \
    python3-pip python-pip libgsl-dev libcurl4-openssl-dev cmake
## Install packages available on default OS repo
########
RUN apt update && apt install -y bwa prodigal \
    && pip3 install -U numpy bcbio-gff cython scipy biopython pandas scikit-learn checkm-genome refinem \
    #&& sed -i 's/srv\/whitlam\/bio\/db\/checkm_data\/1.0.0/data\/checkm_data/g' /usr/local/lib/python2.7/dist-packages/checkm/DATA_CONFIG \
    && rm -rf /var/lib/apt/lists/* \
    && apt -y autoremove && apt autoclean && rm -rf /var/lib/apt/lists/*
## Install htslib
########
ADD https://github.com/samtools/htslib/releases/download/1.9/htslib-1.9.tar.bz2 /usr/local/htslib.tar.bz2
RUN tar xvjf /usr/local/htslib.tar.bz2 -C /usr/local/ \
     && chmod 777 -R /usr/local/htslib-1.9 \
     && cd /usr/local/htslib-1.9 \
     && ./configure \
     && make \
     && make install \
     && rm /usr/local/htslib.tar.bz2
## Install bcftools
########
ADD https://github.com/samtools/bcftools/releases/download/1.9/bcftools-1.9.tar.bz2 /usr/local/bcftools.tar.bz2
RUN tar xvjf /usr/local/bcftools.tar.bz2 -C /usr/local/ \
     && chmod 777 -R /usr/local/bcftools-1.9 \
     && cd /usr/local/bcftools-1.9 \
     && ./configure \
     && make \
     && make install \
     && rm /usr/local/bcftools.tar.bz2
## Install samtools
########
ADD https://github.com/samtools/samtools/releases/download/1.9/samtools-1.9.tar.bz2 /usr/local/samtools.tar.bz2
RUN tar xvjf /usr/local/samtools.tar.bz2 -C /usr/local/ \
     && chmod 777 -R /usr/local/samtools-1.9 \
     && cd /usr/local/samtools-1.9 \
     && ./configure \
     && make \
     && make install \
     && rm /usr/local/samtools.tar.bz2
## Install Metabat
########
ADD https://bitbucket.org/berkeleylab/metabat/downloads/metabat-static-binary-linux-x64_v2.12.1.tar.gz /usr/local/metabat-static-binary-linux-x64_v2.12.1.tar.gz
RUN tar xvf /usr/local/metabat-static-binary-linux-x64_v2.12.1.tar.gz -C /usr/local/ \
    && chmod 777 -R /usr/local/metabat \
    && /usr/local/metabat/contigOverlaps \
    && ln -s /usr/local/metabat/metabat* /usr/local/bin/ \
    && ln -s /usr/local/metabat/runMetaBat.sh /usr/local/bin/ \
    && ln -s /usr/local/metabat/*.pl /usr/local/bin/ \
    && ln -s /usr/local/metabat/jgi_summarize_bam_contig_depths /usr/local/bin/ \
    && rm /usr/local/metabat-static-binary-linux-x64_v2.12.1.tar.gz
## Install Newick
########
ADD http://cegg.unige.ch/pub/newick-utils-1.6-Linux-x86_64-enabled-extra.tar.gz /usr/local/newick-utils-1.6-Linux-x86_64-enabled-extra.tar.gz
RUN tar xvf /usr/local/newick-utils-1.6-Linux-x86_64-enabled-extra.tar.gz -C /usr/local/ \
    && chmod 777 -R /usr/local/newick-utils-1.6 \
    && cd /usr/local/newick-utils-1.6 \
    && ./configure \
    && make \
    && make install \
    && export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib \
    && echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib" >> /etc/bash.bashrc \
    && sudo ldconfig \
    && rm /usr/local/newick-utils-1.6-Linux-x86_64-enabled-extra.tar.gz
## Install hmmer
########
ADD http://eddylab.org/software/hmmer/hmmer-3.2.tar.gz /usr/local/hmmer-3.2.tar.gz
RUN tar xvf /usr/local/hmmer-3.2.tar.gz -C /usr/local/ \
    && chmod 777 -R /usr/local/hmmer-3.2 \
    && cd /usr/local/hmmer-3.2 \
    && ./configure \
    && make \
    && make check \
    && make install \
    && cd easel \
    && make install \
    && rm /usr/local/hmmer-3.2.tar.gz
## Install PPlacer
########
ADD https://github.com/matsen/pplacer/releases/download/v1.1.alpha19/pplacer-linux-v1.1.alpha19.zip /usr/local/pplacer-linux-v1.1.alpha19.zip
RUN unzip /usr/local/pplacer-linux-v1.1.alpha19.zip -d /usr/local/ \
    && chmod -R 777 /usr/local/pplacer-Linux-v1.1.alpha19 \
    && ln -s /usr/local/pplacer-Linux-v1.1.alpha19/guppy /usr/local/bin/ \
    && ln -s /usr/local/pplacer-Linux-v1.1.alpha19/pplacer /usr/local/bin/ \
    && ln -s /usr/local/pplacer-Linux-v1.1.alpha19/rppr /usr/local/bin/ \
    && rm /usr/local/pplacer-linux-v1.1.alpha19.zip
## Install Bedtools
ADD https://github.com/arq5x/bedtools2/releases/download/v2.27.1/bedtools-2.27.1.tar.gz /usr/local/bedtools-2.27.1.tar.gz
RUN tar xvf /usr/local/bedtools-2.27.1.tar.gz -C /usr/local/ \
    && chmod 777 -R /usr/local/bedtools2 \
    && cd /usr/local/bedtools2 \
    && make \
    && make install \
    && rm /usr/local/bedtools-2.27.1.tar.gz
## Install Anvio
########
RUN git clone https://github.com/merenlab/anvio.git /usr/local/anvio \
    && cd /usr/local/anvio \
    && chmod 777 -R /usr/local/anvio/ \
    && pip3 install -r requirements.txt \
    && pip3 install anvio
## Install FigTree
########
RUN apt-get update -y && apt-get install -y figtree