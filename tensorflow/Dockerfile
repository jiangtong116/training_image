FROM python:3.6

MAINTAINER j00255636

# install libs
RUN apt-get update && apt-get install -y --no-install-recommends \
        curl \
        unzip \
        && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# install tensorflow and libs
RUN pip --no-cache-dir install \
        Pillow \
        h5py \
        keras_applications \
        keras_preprocessing \
        matplotlib \
        numpy \
        pandas \
        scipy \
        sklearn \
        tensorflow==1.11.0

WORKDIR "/root"
