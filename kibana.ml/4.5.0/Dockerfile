FROM fluxcapacitor/package-java-1.8

WORKDIR /root

ENV \
  KIBANA_VERSION=4.5.0

ENV \
  KIBANA_HOME=/root/kibana-$KIBANA_VERSION-linux-x64

RUN \
  wget http://download.elastic.co/kibana/kibana/kibana-$KIBANA_VERSION-linux-x64.tar.gz 

RUN \
 tar xvzf kibana-$KIBANA_VERSION-linux-x64.tar.gz \
 && rm kibana-$KIBANA_VERSION-linux-x64.tar.gz

ENV \
  PATH=$KIBANA_HOME/bin:$PATH

RUN \
  $KIBANA_HOME/bin/kibana plugin --install elastic/sense

COPY config/ $KIBANA_HOME/config/
COPY run run

EXPOSE 5601 

CMD ["supervise", "."]
