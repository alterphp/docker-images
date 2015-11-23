FROM node:latest

RUN npm install -g gulp-cli
RUN npm install -g bower

VOLUME ["/data"]
WORKDIR /data

RUN groupadd -f -g 1000 pece && \
  useradd -u 1000 -g pece pece && \
  mkdir -p /home/pece

RUN chown -R pece:pece /data && \
  chown -R pece:pece /home/pece
