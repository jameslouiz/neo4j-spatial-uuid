FROM neo4j:3.1.0

RUN   apk update \
  &&   apk add ca-certificates wget \
  &&   update-ca-certificates

RUN cd /var/lib/neo4j/plugins && \
    wget http://products.graphaware.com/download/framework-server-community/graphaware-server-community-all-3.1.0.44.jar && \
    wget http://products.graphaware.com/download/uuid/graphaware-uuid-3.1.0.44.13.jar

RUN wget -q "https://github.com/neo4j-contrib/m2/blob/master/releases/org/neo4j/neo4j-spatial/0.19-neo4j-3.0.3/neo4j-spatial-0.19-neo4j-3.0.3-server-plugin.jar?raw=true" -O plugins/neo4j-spatial-0.19-neo4j-3.0.3-server-plugin.jar


RUN echo "remote_shell_host=0.0.0.0" >> /var/lib/neo4j/conf/neo4j.conf
RUN echo "dbms.connector.bolt.address=0.0.0.0:7687" >> /var/lib/neo4j/conf/neo4j.conf
RUN echo "com.graphaware.runtime.enabled=true" >> /var/lib/neo4j/conf/neo4j.conf
RUN echo "com.graphaware.module.UIDM.1=com.graphaware.module.uuid.UuidBootstrapper" >> /var/lib/neo4j/conf/neo4j.conf

RUN /var/lib/neo4j/bin/neo4j start

# expose REST and shell server port
expose 7474 7473 7687 1337
