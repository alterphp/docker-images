FROM ruby:latest

VOLUME ["/data"]
WORKDIR /data

RUN groupadd -f -g 1000 pece && \
  useradd -u 1000 -g pece pece && \
  mkdir -p /home/pece

RUN chown -R pece:pece /data && \
  chown -R pece:pece /home/pece

# Missing sources list
COPY ./mysql.gpg /home/pece
RUN apt-key add /home/pece/mysql.gpg
RUN echo 'deb http://repo.mysql.com/apt/debian/ jessie mysql-5.6' > /etc/apt/sources.list.d/mysql.list
RUN echo 'deb http://http.us.debian.org/debian/ jessie contrib non-free main' > /etc/apt/sources.list
RUN apt-get update

# Install capistrano
RUN gem install capistrano

# Install rsync
RUN apt-get install -y rsync

# Install mysql client
RUN apt-get install -y mysql-client

COPY ./Gemfile /home/pece
RUN cd /home/pece; bundle install

# Add alias for cap
RUN echo $'\n'."alias cap='bundle exec cap'".$'\n' >> /home/pece/.bashrc

CMD []