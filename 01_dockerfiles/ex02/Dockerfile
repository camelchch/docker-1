FROM ruby


WORKDIR /parentopt/app
RUN apt-get update -y && apt-get upgrade -y &&\
    apt-get install -y build-essential libpq-dev nodejs && \
	gem install rails
# RUN rm /bin/sh && ln -s /bin/bash /bin/sh &&\

ONBUILD COPY . /opt/app
ONBUILD WORKDIR /opt/app
# ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
# ONBUILD CMD bundle exec rails server
ONBUILD RUN	rails new server && cd server
ONBUILD RUN bundle install && \ 
	rake db:migrate && \
	rake db:seed
# ONBUILD WORKDIR /opt/app
# ONBUILD COPY . /opt/app
# ONBUILD EXPOSE 3000
# ONBUILD CMD bundle exec rails server
# rails -v 4.2.7
