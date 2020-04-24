FROM dockerbooks/scipy

USER root

# Spark Versions
ENV APACHE_SPARK_VERSION 3.0.0-preview2
ENV HADOOP_VERSION 2.7

RUN apt-get update && apt-get install -y wget

# Download Java 8
RUN cd /tmp
RUN wget https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u242-b08/OpenJDK8U-jdk_x64_linux_hotspot_8u242b08.tar.gz && \
        tar xzf OpenJDK8U-jdk_x64_linux_hotspot_8u242b08.tar.gz -C /usr/local && \
        rm OpenJDK8U-jdk_x64_linux_hotspot_8u242b08.tar.gz

# Download Spark
RUN SPARK_FILE=spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && \
        cd /tmp && \
        wget -q https://ftp.cixug.es/apache/spark/spark-${APACHE_SPARK_VERSION}/${SPARK_FILE} && \
        echo "$(echo $(wget -q -O - https://downloads.apache.org/spark/spark-${APACHE_SPARK_VERSION}/${SPARK_FILE}.sha512) | cut -d : -f 2 | sed 's/ //g') *${SPARK_FILE}" | sha512sum -c - && \
        tar xzf $SPARK_FILE -C /usr/local && \
        rm $SPARK_FILE

RUN cd /usr/local && mv spark-${APACHE_SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark

# Make spark folder user-owned, so we can change env vars/etc. easily
RUN chown jupyter:jupyter -R /usr/local/spark

# Env Vars
ENV PATH /usr/local/jdk8u242-b08/bin:$PATH
ENV JAVA_HOME /usr/local/jdk8u242-b08
ENV SPARK_HOME /usr/local/spark
ENV SPARK_OPTS --driver-java-options=-Xms1024M --driver-java-options=-Xmx4096M --driver-java-options=-Dlog4j.logLevel=info


# Install PySpark
USER jupyter
RUN pip install --user pyspark
