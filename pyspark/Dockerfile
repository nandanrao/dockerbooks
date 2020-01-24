FROM nandanrao/base-notebook

USER root

# Spark Versions
ENV APACHE_SPARK_VERSION 2.4.4
ENV HADOOP_VERSION 2.7

RUN apt-get update && apt-get install -y wget

# Download Java 8
RUN cd /tmp
RUN wget https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u242-b08/OpenJDK8U-jdk_x64_linux_hotspot_8u242b08.tar.gz && \
        tar xzf OpenJDK8U-jdk_x64_linux_hotspot_8u242b08.tar.gz -C /usr/local && \
        rm OpenJDK8U-jdk_x64_linux_hotspot_8u242b08.tar.gz

# Download Spark
RUN cd /tmp && \
    wget -q http://mirrors.ukfast.co.uk/sites/ftp.apache.org/spark/spark-${APACHE_SPARK_VERSION}/spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && \
    echo "2E3A5C853B9F28C7D4525C0ADCB0D971B73AD47D5CCE138C85335B9F53A6519540D3923CB0B5CEE41E386E49AE8A409A51AB7194BA11A254E037A848D0C4A9E5 *spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz" | sha512sum -c - && \
    tar xzf spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz -C /usr/local && \
    rm spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
RUN cd /usr/local && mv spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark

# Make spark folder user-owned, so we can change env vars/etc. easily
RUN chown $NB_USER:users -R /usr/local/spark

# Env Vars
ENV PATH /usr/local/jdk8u242-b08/bin:$PATH
ENV JAVA_HOME /usr/local/jdk8u242-b08
ENV SPARK_HOME /usr/local/spark
ENV SPARK_OPTS --driver-java-options=-Xms1024M --driver-java-options=-Xmx4096M --driver-java-options=-Dlog4j.logLevel=info


# Install PySpark
USER $NB_USER
RUN pip install --user pyspark
