FROM java:openjdk-7-jre

VOLUME ["/data"]
WORKDIR /data

RUN groupadd -f -g 1000 java && \
  useradd -u 1000 -g java java && \
  mkdir -p /home/java

RUN chown -R java:java /data && \
  chown -R java:java /home/java
