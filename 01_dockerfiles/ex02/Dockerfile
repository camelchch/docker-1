FROM ruby:2.6-rc

RUN apt-get update -y && apt-get upgrade -y
RUN gem install rails -v 4.2.7
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

ONBUILD WORKDIR /opt/app
ONBUILD COPY . /opt/app
ONBUILD RUN bundle install
ONBUILD EXPOSE 3000
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed
ONBUILD CMD bundle exec rails server
