#
# This image is modified version of sequenceiq/hadoop-docker
#   * sequenceiq/hadoop-docker <https://github.com/sequenceiq/hadoop-docker>
#
# The modifications are
#   * Use local hadoop package
#   * Change template files to indicate docker master node
#   * Modify bootstrap script
#
# Author: Kai Sasaki
# Date:   2015 Sep,13
#
# Creates multi node hadoop cluster on Docker

FROM lewuathe/hadoop-base:latest
MAINTAINER lewuathe

RUN apt-get install -y bzip2 libbz2-dev zlib1g zlib1g-dev

ADD bootstrap.sh /etc/bootstrap.sh
RUN chown root:root /etc/bootstrap.sh
RUN chmod 700 /etc/bootstrap.sh

ENV BOOTSTRAP /etc/bootstrap.sh

ADD hdfs-site.xml /usr/local/hadoop/etc/hadoop/hdfs-site.xml

# Savas: Hadoop Native Libraries
ADD native /usr/local/hadoop/lib/native
ENV HADOOP_COMMON_LIB_NATIVE_DIR $HADOOP_HOME/lib/native
ENV HADOOP_OPTS "-Djava.library.path=$HADOOP_HOME/lib"

# ADD native/hadoop/libhadoop.so      /usr/local/hadoop-3.1.0-SNAPSHOT/lib/libhadoop.so
# ADD native/zlib/libz.so.1           /lib/x86_64-linux-gnu/libz.so.1
# ADD native/zstd/libzstd.so.1        /usr/lib/libzstd.so.1 
# ADD native/snappy/libsnappy.so.1    /usr/lib/libsnappy.so.1 
# ADD native/bzip2/libbz2.so.1        /lib/x86_64-linux-gnu/libbz2.so.1 
# ADD native/openssl/libcrypto.so     /usr/lib/x86_64-linux-gnu/libcrypto.so 
# ADD native/isa-l/libisal.so.2       /usr/lib/libisal.so.2 

CMD ["/etc/bootstrap.sh", "-d"]
