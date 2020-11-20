FROM anapsix/alpine-java:8u202b08_jdk

MAINTAINER Peter Ericson <pdericson@gmail.com>

# https://github.com/Yelp/dumb-init
RUN wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.0.2/dumb-init_1.0.2_amd64 && chmod +x /usr/local/bin/dumb-init

# https://www.apache.org/mirrors/dist.html
RUN wget -O- https://archive.apache.org/dist/zookeeper/zookeeper-3.5.8/apache-zookeeper-3.5.8-bin.tar.gz | tar xzf - -C /opt && \
mv /opt/apache-zookeeper-3.5.8-bin /opt/zookeeper

VOLUME /tmp/zookeeper

COPY entrypoint.sh / 

ENTRYPOINT ["/entrypoint.sh"]

ENTRYPOINT ["/usr/local/bin/dumb-init", "/entrypoint.sh"]

ENV PATH /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/zookeeper/bin:/opt/jdk/bin/java

CMD ["zkServer.sh", "start-foreground"]
