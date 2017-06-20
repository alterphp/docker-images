FROM node:latest

RUN npm install -g gulp
RUN npm install -g bower

VOLUME ["/data"]
WORKDIR /data

ENV OPEN_FILE_LIMIT=32768

RUN chmod -R ugo+r /usr/local/lib/node_modules

# RUN groupadd -f -g 1000 node && \
#   useradd -u 1000 -g node node && \
#  mkdir -p /home/node

# RUN chown -R node:node /data && \
#   chown -R node:node /home/node
