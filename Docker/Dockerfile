FROM ubuntu:16.04
RUN apt-get clean
RUN apt-get update 

# Install dependancies
RUN apt-get install -y --fix-missing --no-install-recommends \
unzip \
build-essential \
wget \
make \ 
bzip2 \
libncurses5-dev \
zlib1g-dev \ 
libbz2-dev \
software-properties-common \
debconf-utils \
python-pip \
python-numpy \
python-matplotlib \
python-pysam \
python-htseq

# Add Java support
RUN add-apt-repository ppa:webupd8team/java
RUN apt-get update 
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections
RUN apt-get install -y oracle-java8-set-default

# Folder for tools
RUN mkdir /home/apps

# install miniconda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda2-4.5.11-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc

#RUN conda create -n py37 python=37
RUN cd /home/apps && /opt/conda/bin/conda create -n py37 --yes --quiet --mkdir python=3.7
CMD [ "/bin/bash" ]
