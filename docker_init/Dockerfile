FROM ubuntu:precise
MAINTAINER Joshua Bangel <falornan@gmail.com>

RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe multiverse" > /etc/apt/sources.list
RUN apt-get update
RUN apt-get upgrade -y

RUN apt-get install -y python-software-properties
RUN add-apt-repository -y ppa:nginx/stable
RUN apt-get update
RUN apt-get install -y nginx

RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN rm -f /etc/service/nginx/down
RUN rm -f /etc/nginx/sites-enabled/default

ADD webapp.conf /etc/nginx/sites-enabled/webapp.conf

RUN apt-get purge -y build-essential
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Ensure the port gets exposed even without run flags
EXPOSE 80

ENTRYPOINT ["nginx"]

ONBUILD RUN apt-get install -y build-essential sqlite3 libsqlite3-dev nodejs
ONBUILD ADD webapp /home/app/webapp
ONBUILD RUN cd /home/app/webapp; bundle install

