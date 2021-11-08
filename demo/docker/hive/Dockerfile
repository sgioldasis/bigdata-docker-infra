FROM bde2020/hive:2.3.2-postgresql-metastore

USER root

WORKDIR /opt

# Fix OS update
RUN echo "deb [check-valid-until=no] http://cdn-fastly.deb.debian.org/debian jessie main" > /etc/apt/sources.list.d/jessie.list
RUN echo "deb [check-valid-until=no] http://archive.debian.org/debian jessie-backports main" > /etc/apt/sources.list.d/jessie-backports.list
RUN sed -i '/deb http:\/\/\(deb\|httpredir\|ftp\).debian.org\/debian jessie.* main/d' /etc/apt/sources.list
RUN apt-get -o Acquire::Check-Valid-Until=false update

# OS stuff
RUN apt-get install -y unzip nano wget less

# Pig
ENV PIG_VERSION 0.17.0
RUN wget  --no-check-certificate -q   https://dlcdn.apache.org/pig/pig-$PIG_VERSION/pig-$PIG_VERSION.tar.gz && \
    tar xzf pig-$PIG_VERSION.tar.gz -C /usr/local/ && \
    ln -s /usr/local/pig-$PIG_VERSION /usr/local/pig
ENV PATH $PATH:/usr/local/pig/bin

# Presto
RUN wget https://repo1.maven.org/maven2/io/prestosql/presto-cli/308/presto-cli-308-executable.jar && \
    mv presto-cli-308-executable.jar /usr/local/bin/presto && \
    chmod +x /usr/local/bin/presto

