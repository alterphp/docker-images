FROM ruby:latest

# Install capistrano
RUN gem install capistrano

VOLUME ["/data"]
WORKDIR /data

RUN groupadd -f -g 1000 pece && \
  useradd -u 1000 -g pece pece && \
  mkdir -p /home/pece

RUN chown -R pece:pece /data && \
  chown -R pece:pece /home/pece

COPY ./Gemfile /home/pece
RUN cd /home/pece; bundle install

# Install mysql client
COPY ./mysql.gpg /home/pece
RUN apt-key add /home/pece/mysql.gpg
RUN echo 'deb http://repo.mysql.com/apt/debian/ jessie mysql-5.6' > /etc/apt/sources.list.d/mysql.list
RUN apt-get update
RUN apt-get install -y mysql-client


# Add alias for cap
RUN echo $'\n'."alias cap='bundle exec cap".$'\n' >> /home/pece/.bashrc

CMD []