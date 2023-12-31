FROM dockerbooks/scipy

USER root

# Spark Versions
ENV APACHE_SPARK_VERSION 3.0.1
ENV HADOOP_VERSION 3.2

RUN apt-get update && apt-get install -y wget


# Download Java 11
RUN cd /tmp
RUN wget https://github.com/AdoptOpenJDK/openjdk11-binaries/releases/download/jdk-11.0.8%2B10/OpenJDK11U-jdk_x64_linux_hotspot_11.0.8_10.tar.gz && \
        tar xzf OpenJDK11U-jdk_x64_linux_hotspot_11.0.8_10.tar.gz -C /usr/local && \
        rm OpenJDK11U-jdk_x64_linux_hotspot_11.0.8_10.tar.gz

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
ENV PATH /usr/local/jdk-11.0.8+10/bin:$PATH
ENV JAVA_HOME /usr/local/jdk-11.0.8+10
ENV SPARK_HOME /usr/local/spark
ENV SPARK_OPTS --driver-java-options=-Xms1024M --driver-java-options=-Xmx4096M --driver-java-options=-Dlog4j.logLevel=info


# Install PySpark
USER jupyter
RUN pip install --user pyspark
