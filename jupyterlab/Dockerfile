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
        tensorflow==1.11.0 \
        jupyterlab \
        hdfs

# config jupyterlab
COPY jupyter_notebook_config.py /root/.jupyter/
COPY run_jupyter.sh /run_jupyter.sh

# install java
ADD jdk1.8.0_172.tar.gz /usr/java
ENV JAVA_HOME /usr/java/jdk1.8.0_172
ENV PATH /usr/java/jdk1.8.0_172/bin:$PATH

# instal spark
ADD spark.tar.gz /opt/client/Spark2x
ADD pyspark.tar.gz /usr/local/lib/python3.6/site-packages
ADD py4j-0.10.4.tar.gz /usr/local/lib/python3.6/site-packages
ENV SPARK_HOME /opt/client/Spark2x/spark
ENV PATH $SPARK_HOME/bin:$PATH
ENV HADOOP_CONF_DIR /opt/client/Spark2x/spark/conf


# start jupyterlab
EXPOSE 8888
WORKDIR "/notebook"
CMD ["/run_jupyter.sh", "--allow-root"]
